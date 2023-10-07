# pndas is using numpy for data processing and mathemetical operations

# there are 2 types of data structure are used in pandas
1. `series` : one dimential array, either one column or one row
2. `DataFrame` : tabular structure

# axis

-> `axis = 0` : row
-> `axis = 1` : column

# create a dataframe
import numpy as np
import pandas as pd

data_dict = {
    "name":['sumit', "amit","kaka","saka"],
    "roll":[1,5,6,8],
    "marks":[25,36,39,58]
}

df = pd.DataFrame(data_dict)
print(df)

`output`

-> It will add index by default


	name	roll	marks
0	sumit	1	25
1	amit	5	36
2	kaka	6	39
3	saka	8	58


`output`
it will create a csv file 

df.to_csv("kaka.csv")   --> with the default index

df.to_csv("kaka.csv", index = False) --> without the default index


# read get columns and get list output
`get columns`
print( df.columns)

`list output`
new = df.columns.tolist()

# print a row using index
row = df.iloc[0]
row_list = row.tolist()

# itreate over row / for loop in row
for i, row in df.iterrows():
    # Convert the current row to a list
    row_list = row.tolist()
    print(row_list)

# read data frol excel, xlsx
pip install xlrd
pip install openpyxl

df.to_excel("train.xlsx")

`with sheet name`
df =  pd.read_excel('train.xlsx', sheet_name="Sheet1")

# write data to excel

df.to_excel('train.xlsx', sheet_name="Sheet1")



# ---- data gathering and reading  -------

`read data with CSV(comma separated value) pandas`
    -> From Local

        import pandas as pd
        df = pd.read_csv('data.csv')

    -> From an URL

        import requests
        from io import StringIO

        url = "https://raw.githubusercontent.com/cs109/2014_data/master/countries.csv"
        headers = {"User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:66.0) Gecko/20100101 Firefox/66.0"}
        req = requests.get(url, headers=headers)
        data = StringIO(req.text)

        pd.read_csv(data)

`read data from TSV(Tab separated value)`
    -> df = pd.read_csv('data.csv', sep="\t")

`if there are no column name`
    -> pd.read_csv('movie_titles_metadata.tsv',sep='\t',names=['sno','name','release_year','rating','votes','genres'])

`How to make a column as index column`
    
    -> df = pd.read_csv('data.csv', index_col = 'order_id')

`header issue`
    -> At the time of csv generation someone made the header to row. 
    -> if you want to make a row to header
        -> pd.read_csv('test.csv',header=1)
            -> 1 is the index of the row

`use_cols parameter`
    -> if you want to import the specific columns the time of importing the data
    -> 
    pd.read_csv('aug_train.csv',usecols=['enrollee_id','gender','education_level'])

`Skiprows/nrows Parameter`
    -> Skiprows
        -> same , if you want to load rows at the time of loading
        -<> pd.read_csv('aug_train.csv',skiprows=[0,5])
        -> use skip rows with lambda function:

    -> nrows
        -> If you have a very big dataset, it is not possible to load the data in memory. We can load the data in small parts and can perform operation.
        -<> pd.read_csv('aug_train.csv',nrows=100)

`Encoding parameter`

    -> By default all files are encoded with UTF-8. If you get the unicode error at the time of loading the data. There will be 2 ways to deal with
        -> Findout the encoding
        -> use sublime-text editor and change the encoding
    -> 
    -> There are some case when the code is encoded with some other encoder
        -<> pd.read_csv('zomato.csv',encoding='latin-1')

`skip bad line`
    -> There may some case when you are loading the data, pandas gives you error like `ParserError`
    -> While loading, pandas is not able to load some lines.
    -<> pd.read_csv('BX-Books.csv', sep=';', encoding="latin-1", error_bad_lines=False)

`dtypes parameter`
    -> there is a case, at the time generating data from the data base. Someone made the integet to float
    -> there is a age column, age will be integer. But in the dataset it is float. 
    -> Dtype will help you to convert the datatupe at the time of loading

    -<>  pd.read_csv('aug_train.csv',dtype={'target':int})
        -> target is the column name
    
`Handling Dates`
    -> There is date column inside the data_sheet
    -> by df.info() it is showing the datatype as object(string)
    -> To convert the string data into the date format at the of loading
    -<> pd.read_csv('IPL Matches 2008-2020.csv',parse_dates=['date']).info()

`Convertors`:
    -> Helps to convert value or data manupulation while loading
    -> Lets there is column, where data is like case-case1, case-case2, case-case3. Now you want to remove the `case-` from all the values of the column.

    -<>

    def data_fix(case_name):
        clean_name = case_name.split('-')[1]
        return clean_name

    pd.read_csv('IPL Matches 2008-2020.csv',converters={'case_name_column':data_fix})


`na_values parameter for missing values`
    -> data set column can contains NAN values, sometimes there may be some `--` or `...` or `1111`, means some randome data is there insted of NAN but they are garbage.
    -> Now we have function where can Convert the garbage values to NAN at the time of loading

    -<> pd.read_csv('aug_train.csv',na_values=['---','...', '1111'])
        -> here it will convert all '---','...', '1111' values to NAN


`Loading a huge dataset in chunks`

    -> dfs = pd.read_csv('aug_train.csv',chunksize=5000)
    -<> 
    for chunks in dfs:
            print(chunk.shape)
            `all operations will be performed here`


# ======= data gathering and reading  ============


# how start indexing from 0
new = df.reset_index(drop=True)

`out`
    index	train_number	speed	destination
0	0	    1111	        23	    hwh
1	1	    2222	        235	    bqa
2	2	    3333	        126	    dgr
3	3	    4444	        188	    asr

--> it ccreates new column 'index'
to avoid it 
new = df.reset_index(drop=True, inplace = True)


# how to set cutom index
df.index=['a','b','c','d']

# How to see last and first 5 rows for a large dataframe

df.head(5) -> for first 5

df.tail(5) -> for last 5

# truncate row and column
   train_number  speed destination
0          1111     23         hwh
1          1111    235         bqa
2          3333     25         dgr
3          4444    188         asr
4          5554    158          gg

`--> row`
df1 = df.truncate(before=3, after = 3)

`out`
train_number	speed	destination
3	4444	188	asr


`--> column`
df1 = df.truncate(before='b', after = "c", axis=1)
`Note`
-> as per the current column data it is not possible to do,
-> column name should be sorted
-> like 1,2,3,4 or a,b,c,d



# df.describe()
it will calculate the min,max,count,std,25%,50%,75%,
for all columuns contains the numeric values

	name	roll	marks
0	sumit	1	25
1	amit	5	36
2	kaka	6	39
3	saka	8	58

`output`

		roll		marks
count	4.00000		4.000000
mean	5.00000		39.500000
std		2.94392		13.723459
min		1.00000		25.000000
25%		4.00000		33.250000
50%		5.50000		37.500000
75%		6.50000		43.750000
max		8.00000		58.000000


# arithmatic opearation sum, count,mean, std, min, max, median, var(Variance)
new = df['speed'].count()


# read csv
 
import pandas as pd

df = pd.read_csv('train.csv')
df
`output`
	train_number	speed	destination
0	1111	        23	    hwh
1	2222	        235	    bqa
2	3333	        126	    dgr
3	4444	        188	    asr

-- `NOte`
here the column are python list, the original representation is

    "train_number":[1111,2222,3333,4444],
    "speed":[23,235,126,188],
    "destination":["hwh","bqa","dgr","asr"]


# get a column
df['speed']
`out`
0     23
1    235
2    126
3    188
Name: speed, dtype: int64

17.4088988989747, 78.47894875749856

`note`
-> we can use indexing
df['speed'][1]


# drop a row and column

import pandas as pd

df = pd.read_csv('train.csv')
df
`out`

	train_number	speed	destination
0	1111	        23	    hwh
1	2222	        235	    bqa
2	3333	        126	    dgr
3	4444	        188	    asr


`column`
new=
-->  df.drop(['speed','destination'],axis=1)

new

`row`
new=df.drop(1,axis=0) 
new

# drop a row and column  inplace

new=df.drop('speed',axis=1)
--> here we are droping the column and storing it on new variable and printing

if I want to drop it on the origin ed: df variable

df.drop('speed',axis=1, inplace= True)

print(dfs)




# get rows using index number using loc
import pandas as pd

df = pd.read_csv('train.csv')
new = df.loc[[0,3],:]
new

`out`

    train_number	speed	destination
0	1111	        23	    hwh
3	4444	        188	    asr


# get all rows using columns
import pandas as pd

df = pd.read_csv('train.csv')
new = df.loc[:,['speed','destination']]
new

`out`

    train_number	speed	destination
0	1111	        23	    hwh
3	4444	        188	    asr

# get data using index and column name
import pandas as pd

df = pd.read_csv('train.csv')
print(df)
new = df.loc[[2,3],['speed','destination']]
new


speed	destination
2	126	dgr
3	188	asr


# iloc
If there is requirement I need to get the data from indexing
like: in row index 2, get destination

import pandas as pd

df = pd.read_csv('train.csv')
print(df)
new = df.iloc[2,2]  # `[2,2] == > [row_index_numbwe , index]`
new

`out`
--> hwh

[train_number, speed, desctination] -> 


# loc vs iloc

`loc`:
1. Need to use column _name to acceess data
2. if there is row_index like (a,b,c,d), here to access the row you need use rowname eg: df.loc[['a','b'],:]

`iloc`:
1. need column index number to access data
2. if there is row_index like (a,b,c,d), here to access the row you need use index_number eg:  df.iloc[1]



# ---------------------------- queries ----------------------------
	train_number	speed	destination
0	1111	        23	    hwh
1	2222	        235	    bqa
2	3333	        126	    dgr
3	4444	        188	    asr

# speed < 100

import pandas as pd

df = pd.read_csv('train.csv')
print(df)
new = df.loc[(df['speed'] < 100)]   # `[(df['speed'] < 100)]`

# speed < 100 and destination = hwh

new = df.loc[(df['speed'] < 150) & (df['destination']=='hwh')]

# ---------------------------- Group by ----------------------------

    train_number  speed          destination     model
0          1111     23          hwh          model1
1          1111    235          bqa          model2
2          3333     25          dgr          model3
3          4444    188          asr          model4
4          5554    158           gg          model5


`case 1 : by column name`
new = df.groupby("train_number")
for key, value in new:
    print (key, value, end= '\n\n')

`out`
1111    
train_number  speed destination    model
0          1111     23         hwh   model1
1          1111    235         bqa   model2

3333    train_number  speed destination    model
2          3333     25         dgr   model3

4444    train_number  speed destination    model
3          4444    188         asr   model4

5554    train_number  speed destination    model
4          5554    158          gg   model5


`Note`
Now get data of particular group

new = df.groupby("train_number")
print(new.get_group(1111))



# ------------------------- data cleaing------

# check for the null values
df['speed'].isnull()
`out`
0    False
1    False
2     True
3    False

# **************** dealing with null values ************

`case 1 : dropna()`
row
new = df.dropna()
--> it will remove entire row if there are any null value

column
new = df.dropna(axis=1)
--> it will remove entire culumn if there are any null value

`case 2 : dropna(how= 'all')`

row
new = df.dropna(how= 'all')
--> it will remove entire row if and only all values of the row is null

column
new = df.dropna(how= 'all', axis=1)
--> it will remove entire culumn if and only all values of the column is null

`case 3 : drop row if there are atlist 2 null values`

       name         toy         born
0       NaN         NaN         NaT
1    Batman         Batmobile   1940-04-25
2  Catwoman         Bullwhip    NaT

df.dropna(thresh=1, inplace=True)

# ********** dealing with duplicates ************

`  keep = 'First'  ` : to keep first record
`  keep = 'last'  ` : to keep last record
`  keep = 'False  ` : Remove all duplicates

new = df.drop_duplicates(subset='train_number', keep=False)