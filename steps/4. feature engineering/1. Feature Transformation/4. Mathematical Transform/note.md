# what is mathematical tranformation
> applying mathematical formula in column and converting it something else.
* log tranform
* reciprocal transform
* Box-Cox
* yeo-jonson

#### why the performance of the models gos up after apply the transformation

> It helps in data distribution. After applying this the pda (Probability density function) get converted into `normal distribution`

* normal distribution : It is helps to solve the problem. The calculation and problem get easy.

* performance of Rigression depands a lot upon the normal distribution.

# what is function transformar

> there are 3 types of transformar
* Function Transformar
    * log tranform
    * reciprocal transform
    * sqare / sqare-root
* Power Transformar
    * Box-Cox
    * Yeo-jonson
* Quantile Transformar

# steps
> first need to see that:
*  Is there is a need to transform the data
    * sns.displot
    * QQ plot
* will there any effect on the model we are going to use.


# log Transform
> if i want to apply log transform in age column of the titanic dataset, i will calculate the log of each value. Then the data get normally disributed (partially).
* avoid the negetive values

> where we have to use log transform
* if the data is right sceqed in the line graph


# Reciprocal transform
It is diffrent type of transform. Your small values will be converted large and large will be converted to small values.

# squreroot
> where we have to 
* if the data is left sceqed in the line graph

# BOX-COX
we can convert any distribution to normal distribution.
> `λ` or lambda is the hero here.
* The value of the lambda varies in range betwnn 5 to -5. 
* we examin the all the values of λ (eg 1,1.1,1.2) and choose the optimal value, resulting the best approxmation to a normal distribution.
> This transformation is only applicable to the `numbers > 0.`

> when you apply the box-cox, standard scaler is applied internally.

# yeo-jonson
same as box-cox. but `can be applied for the numbers <= 0`.
* yeo-jonson gives better result than yeo-jonson
