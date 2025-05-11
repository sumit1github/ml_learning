# intro

1. Foundation of Linear Regression
2. supervised Learing (cataory)
3. Types:
    - ***a. Simple LR***:
        - There will one input column and one out-put column. eg; In a data set there are 2 columns, cgpa and package. Now you have create a model where you need to find a student with a cgpa of 6, how much package he can score.

    - ***b. multiple LR:***
        - There will one input column and one out-put column. eg; In a data set there are many columns like `age`, `gender`, `10th marks`, `12th marks`, `cgpa and package`. Now you have create a model where you need to find a student with age, gender, 10th marks, 12th marks of 6, how much package he can score.


    - ***c. polunomial LR***

        - it is also called `closed form solution`
        - it is a mathemitial expression where you can get the result my applying finaite number of steps, variable, formula.

        - there should be no intregation or differentiation involbed.

4.  `linear_model.LinearRegression()` it uses direct formula which is also called orinary least     squares(OLS).
5.  applicable for 2 columns only

# start

from sklearn import datasets, linear_model
import numpy as np
import pandas as pd

# load model from sk learn module

diabetis = datasets.load_diabetes()  -- it will load the dataset
print(diabetis.DESCR) -- it will give information about the dataset



# ----------------------------------------a. Simple LR -----------------------------

1. There will only 2 colums
2. Both coloums should contains the int or float


***problem statement***

Here is data of a college where you have cgpa is given and package is given.

***input***: cgpa value

***output*** : how much package he can expect

```
cgpa    lpa
6       2
7       3
8       4 
3       2
6       2.5
9       8 
7       7 
1       2 
5       3 
```

`code -->`
```
from sklearn import datasets, linear_model
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split

df = pd.read_csv('cgpa.csv')
x = df[["cgpa"]]  ` x must have double brackaets`
y = df['lpa']

` creating training dataset and test data set`
x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2,random_state=2)

` creating model`
lr = linear_model.LinearRegression()
lr.fit(x_train,y_train)

` preiction`
ja= np.array([12,]).reshape(1,1)
lr.predict(ja)

```


# ================ explain ===============

`x_train, x_test, y_train, y_test = train_test_split(x,y,test_size=0.2,random_state=2)`

1. we have numpy array inside x and y
2. ***test_size=0.2***:
    - 0.2 means 20%
    - 20% of data will be used for testing and 80% of data will be used in training puspose
    - we are not giving the testing data to model, for mesuring result


3. ja= np.array([12,]).reshape(1,1)
    - need to reshape [1,1]
    - reshape only supports numpy array


4. ***Note***
- `y = mx + b` is the forlmua to calculate the simple lr

    - package = linear_cofficent*cgpa + linear_intercept
    - m = linear_cofficent = lr.coef_ or slop
    - b = linear_intercept = lr.intercept_

5. ***+ b why we are adding b`***

    - `case1`: if you compare this dataset with real-life, lets not adding 'b' at last. if your cgpa is zero (x=0) then the package will be zero.
    so thsi is ok.

    - `case2` : Instade of cgpa , if we have experience. if we dont add b, then if the fresher with zero experience will come his cgpa should be zero. But it is not true in real life. Fresher get some salary. We add b to avoid the zero value output to make it little close towards the real world.

- we can predict the for the cgpa which may not be present in the dataset


