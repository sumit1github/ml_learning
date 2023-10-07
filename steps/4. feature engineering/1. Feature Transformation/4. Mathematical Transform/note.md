# what is mathematical tranformation
> applying mathematical formula in column and converting it something else.
* log tranform
* reciprocal transform
* Box-Cox
* yeo-jonsom

#### why the performance of the models gos up after apply the transformation

> It helps in data stribution. After applying this the pda (Probability density function) get converted into `normal distribution`

* normal distribution : It is helps to solve the problem. The calculation and problem get easy.

* performance of Rigression depands a lot pon the normal distribution.

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