# feature scaling 
* Standardization or Zscore Normalizaton
* Normalization 
    * min-max
    * robust scaler (works with outlier)



# Normalization

age
27
25
36
69
58
45
25
36

Here is our data, where we are going to create a new column name age_new

> formula
    >> (X(i) - X(bar))/ σ(Sigma)
        >>> (27 - mean) / Standard_deviation
    
>> NOTE : After doing this operation through the data, we are going to get a new series. The `mean of the new seriese will be 0` and s`tandard deviation will be 1.`

### NOte
> If we are applying the scaling on a column contains `outlier`. There will no effect on the outlier. So we need to perform outlier treatment before scaling.

# when we can use standardization
> There are no loss on appling standardization
> if you don't have any idea about the data use it.

> If we are working below algos. Use standardization blindly
* k-Means : Use the euckidean distance measure
* K-Nearest-Neighbours
* principal component analysis (PCA)
* Artiicial Neural Network
* Gradient Descent

> standardization not required
* Decision Tree
* Random Forest
* XS Boost
* Gradient Boost


# Normalization
> it is used in data preparation

> the goal is to change the values of numeric columns in the dataset to use a common scale withhout distorting the diffrence in the ranges of values or losing informaation. 

* min-max scaling (use 90% times)
* mean normalization
* max absolute scaling
* robust scaling

## min-max scaling - Intution

age
27
25
36
69
58
45
25

> fomula
* Xi' = Xi' - Xmin / Xmax - Xmin
* if you apply the formula to a column, the result istribution will scaled in beetween `0 to 1`

> when to use?
* if you know the max and min should in some range. eg: in image processing(CNN) colour channel value should be 0-255.

## mean normalization
> fomula
* Xi' = Xi' - Xmean / Xmax - Xmin
* if you apply the formula to a column, the result distribution will scaled in beetween `-1 to 1`

> rarely used, there is not class in sklearn

> used when you need a centered data

## mean absolute scaling
> fomula
* Xi' = Xi' / |Xmax|
* if you apply the formula to a column, the result distribution will scaled in beetween `-1 to 1`

> sklearn has a class for it -> MaxAbsScaler

> useful if you have parse data (parse matrix data) (if you have lot of zero )

## Robust scaling
> fomula
* Xi' =( Xi' - Xmedian )/ IQR     --> IQR(Inter Qurtile range)(75th percentile - 25th percentile value)

> sklearn calss `RobustScaler`

> Robust to outlier (if your data has lot of outlier.)

> I you know that your value contains outlier.




# Normalization vs Standardization
> first ask some questions
* is feature scaling need (Type of algo)
* what should is use normalization or standaedization
    * most of the time we use standization



>`Normalization`:
*

>`standardization`: