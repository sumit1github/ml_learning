# ------------------------------------------ data gathering -------------------------------------------------


`*************************read data with CSV(comma separated value) pandas************************`
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
    -> data set column can contains NAN values, sometimes there may be some `--` or `...` or `1111`, means some me data is there insted of NAN but they are garbage.
    -> Now we have function where can Convert the garbage values to NAN at the time of loading

    -<> pd.read_csv('aug_train.csv',na_values=['---','...', '1111'])
        -> here it will convert all '---','...', '1111' values to NAN


`Loading a huge dataset in chunks`

    -> dfs = pd.read_csv('aug_train.csv',chunksize=5000)
    
    
    
    -<> 
    for chunks in dfs:
            print(chunk.shape)
            `all operations will be performed here`




`************************* read data with json ************************`
-> pd.read_json('train.json')
-> pd.read_json('https://api.exchangerate-api.com/v4/latest/INR')

`************************* read data from mysql ************************`
import mysql.connector
conn = mysql.connector.connect(host='localhost',user='root',password='',database='world')
df = pd.read_sql_query("SELECT * FROM countrylanguage",conn)
df

# ============================================== data gathering =============================================
