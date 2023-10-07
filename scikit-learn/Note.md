# usecase
-> helps in dat modeling, scaling
-> data preprocessing
    --> scaling
    --> cross-validation(accurecy score)
    --> dimention reduction to prevent overfitting


# install 
pip install numpy
pip install pandas
pip install 

# ---------load dataset ------------
import sklearn
from sklearn import datasets

`to get all available dataset `
print(dir(sklearn))

` load a dataset `
iris = datasets.load_iris()

`target and target names`
print(iris.target)
print(iris.target_names)

`to get the description of the data`
print(iris.DESCR)


# standard data

from sklearn.preprocessing import StandardScaler
sc = StandardScaler()

`note `
-> for training data use are using `fit_transform`
-> for testing data use are using `transform`    


X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)