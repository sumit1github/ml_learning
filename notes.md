# -- key points of ML
    -> ml algo is pure math, it not understands the text
    -> If you are dealing with the string data, you need to convert it to numbers any how


# --------- types of ml -------------

`1. Supervised : `
    -> when you input and output, along with that id you can tell the out put for a new input.

    eg: placement prediction of student as per CGPA and IQ. Here iq and cgpa are the input column and the placement is the output column.

    -> regression, classification

-> There are 2 types of data, `numerical` and `categorical`
    `regression` --> If you data is `numerical`. eg: age, IQ, cgpa
    `classification` --> If you data is `categorical`. eg: gender


`2. Un supervised`
    Here you don't have output, you dont have any output. Like you have cgpa and IQ, but the dat aod placement is not present.

-> clustering, Dimensnality-reduction, anamoly-detection, Association.

`clustering` : It is basically grouping. 

    -> eg : we have data of homework data of students in the class. Now if want to do behavioural analysis. based upon the problem solving and result I want to devide the students into 3 types of group, high, mid, low IQ group. 
    -> Very helpful for N-Dimetional data or very large dataset.
    -> we can create group of groups.

`Dimensnality-reduction`:
    -> `overfitting` : when we are working on some data where we have a large numper if inputes. Because of that our programs runs little slow and after some point, by incresing the inout column the results also not improves.
    -> it helps remove the extra columns.
    -> we can do feature reduction, where we combine 2 columns and create a new columns. 
    -> eg:  Text data analysis, image analysis

`anamoly-detection`:
    -> creadit-card detection fraud can be a good example of this, When you have a normal range, if a data goes up from the range system can raisea flag.

`Association`:
    -> Think you have a store, Now the problem is arrangeing the products. How can we organise the location of the products. 
    -> approch -> we findout the the sales data, where we can see, There is a pattern, where 90 times of milk purchase there is 70 time eggs also purchased. So we can see there is co-relation between egg and milk. So we will keep eggs beside the milk.

    
    

`3. Semi-Supervised`

    -> partially supervised and unsupervised. 
    -> For example google photos, we have some photes, with  people, the system knows about the 2 people. They persorm clustering and they will group them. Now, it ask about the 3rd person, so said it is you father. Now a human helped to identify, now again google photos will group your father's images.

`4. Re-inforcement`
    -> you don't have data at the first, data is generating gradually and training is going.
    -> Self-Driving Car: You don't had data first, you are driving the car, and gathering the info. Based upon the data you are training the agent. 



# ------------- Batch/Offline and Online ML and Out_of_core  --------
`Batch/Offline Learning` : Takeup the entire data then you are buliding the ml model and deploy the ml model(exporting) on the server.
    -> problem:
        --> it is static, it is not getting learned as per the new data entry.
        --> need to retrain the model.
        --> we need to run a sceduler, when it can recreate the model with the old data and new data.
        --> if data is getting generated raoidly or getting converted in big-data, your tools are getting failed
        --> chances of hardwere failure.
        --> Tools:
            -> SCI-KIT, TensorFlow, Pytorch, Spark, Mlib
    
`Online Learing`:
    -> Incremental learning, Where your model is getting trained with new data. The data is getting seperated into small batches on server.
    -> eg: Chatbots
    -> Tools
        -> This types of algo is present in the scikit learn
        -> librery : River, Vowpal Wabbit
        -> MOA, SAMOA, SCIKIT-Multiflow, StreamDM
    -> Challange
        -> Need to set the learning rate. Where your model getiing updated by remembering the old data

`Out_of_core`:
    -> Now there is a case you have a large dataset. like, you have 3gb of ram and you data size is 50gb. You can't load the data.
    -> It this case you need to devide the data into small dataset then, implement the online learning. 
    -> Disadvantages : 
        -> Tricky od Use
        -> Unstable
        -> Enterprize label support is noy there.
        -> Risky (If any hacker plays with the incoming data, Need close monitoring to do that)
        -> Need to know the roll back

# ------- classification of ML, based upon how models are gettig learned ----
`instance vs Model Based Learning`

-> Learning is divided into 2: Memorizing, geralization

`Problem Statement` : we need to identify the placement based upon the IQ and CGPA. Then they will work.

`instance` : Here no learning is involbed. You are colleting the data points. When a new data comes. It maps the distance with all points and ives the result.


`Model Based Learning` : 
Here mathematical functions are the.

# ----- ML Challanges ----
    
-> `Data collection`
    -> Need to data from api and web-scraping
    -> Insufficient Data

-> `insufficient Data`
    -> if you have a lot of data then algo does not matters.
    -> For small amount of data algo matters (real life)

-> `Non Representative data`
    -> When you are dealing with a ml probelm, you need to gather data from all possible data.
    -> Poor quality data, a lot outlier data, missing data. Need to improve the quality of data.

-> `Irrelevent Data:`
    -> Need to elminate all the features, which are not adding any value.
    -> 

-> `overfitting :`
    -> when we are working on some data where we have a large numper if inputes. Because of that our programs runs little slow and after some point, by incresing the inout column the results also not improves.
    -> When your model is too much serious about the training data, it will not give good result with new traing data.

-> `underfitting`:
    -> With less data, model is not thinking just creating aopnion.
    -> you can get 100% accurecy, but not ok.

-> `Software Integration;`
    -> Now your model is created, now the challange it integration with diffrent diffrent platforms.

-> `Batch Learning`
-> `Costing`
    -> 


# ----- Machine Learning Development Lifecycle ----

-> `Frame The problem`
    -> What is the problem
    -> What is the output
    -> Who are the users, costing, supervised or un-supervised
    -> algo, batch or online

-> `Gathering The Data`
    -> Through api/ csv
    -> Running Database
        -> DataWereHousing (ETL)
    -> BigData
        -> Spark

-> `Data Preprocessing`
    -> Remove
        -> Duplicates, Missing , Outliers
    -> Scaling
        -> Scale-up or scale Down the data

-> `Eploratory Data Analysis`
    -> Data visualization using graphs, getting the relation among the graphs.
    
    ->  Univariate Analysis:
        -> Performing independent analysis on each column. Mean, std, 

    -> Bivariate
        -> Performing independent analysis on two diffrent columns. Mean, std

-> `Feature Engineering and Selection`
    -> Changing or improving on current on a feature
    -> Combine the new features
    -> Remove less impactful features

-> `Model Training, Evalution and selection`
    -> Need to train diffrent models and check the results.
    -> Performance accurecy
    -> Now to you have selected the model, time to tune the model. So you can get more features from the model.

-> `Deployment`
    -> 

-> `Testing`
    -> A/B Testing 

-> `Optimize`
    -> Model Backup
    -> Data Backup
    -> loadblancing
    -> model retrain frequency
    -> cost reduction



# ----------- Tensors ------------


-> Basic Data structer for all ML algos and deep learnigns.
-> Container for storing numbets
-> `n-D array is tensor`

-> `check dimention`
    -> data.ndim()

-> `0-D Tensors`
    -> also called scaler
    -> creation
        -> a = np.array(4)

-> `1-D Tesnsor`
    -> creation: a = np.array([1,2,3,4])
    -> dimention : 1
    -> It is also called `vector`
        -> `now the dimention of the vector is 4 (length of the array)`

-> `2-D Tensor (marrices)`
    -> creation: a = np.array([[1,2,3,4],[4,5,6,7]])0223

-> `3-D Tensor`
    -> They are not so frequest as 1d and 2d
    -> NLP is also example
    -> If your input is a text, then youneed to convert the texts into vectors(in terms of NLP).
    -> Steps:
        -> First you need find the unique words
        -> sumit kumar panda can be represent as 
            ->  [
                [[10001], [10101]]
                [[10000],[10001]]
                [[10010],[11001]]
                ]
            -> shape (3,2,4)
                -> total elements are (3*2*4)

-> `4D tensor`
    -> Image data is called 4d tensor, can be find in computer vison

-> `5D tensor`
    -> Videos
    -> Human eyes can classify 12 images/frames per sec.
    -> 30 fps, 60 fps


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




`************************* read data with json ************************`
-> pd.read_json('train.json')
-> pd.read_json('https://api.exchangerate-api.com/v4/latest/INR')

`************************* read data from mysql ************************`
import mysql.connector
conn = mysql.connector.connect(host='localhost',user='root',password='',database='world')
df = pd.read_sql_query("SELECT * FROM countrylanguage",conn)
df

# ============================================== data gathering =============================================