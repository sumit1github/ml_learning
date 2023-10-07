# pandas dummy variable vs sklearn's on-hot encoding
> we can perform on hot encoding using panda's dummy variable and sklearn's onhot encoding

> `pandas dummy variable` : 
* it will encode , but it will not remember the position of the column.
* first time run:
    * `Color_y ,    Color_R  ,   Color_G`
* second time run
    * `Color_y   ,   Color_G  ,  Color_R`

> that's why we will not use the pandas's dummy variable in data preprocessing

# Dummy Variable Trap

model    Color_y     Color_R     Color_G
  x         1           0           0
  y         0           1           0
  z         0           0           1

* In ML your input columns always indipendent
* there should be no relation in between them
    * in the above case we can see [sum of Color_y,Color_R,Color_G] is coming 1 in each line.
    * 100 =1, 001=1
    * it is called `multicolinearity`
    * It creates a lot of issus in linear model
* to prevent that we remove 1st column


# High-Dimention dataset
> When there are lot of columns due to on-hot encoding

1. Approch 1:
> First count the frequency of occurance, how many times the model-number is present in dataset
* rename the model with low frequency columns as "other"
* then apply the on hot encoding
* fit into the model
