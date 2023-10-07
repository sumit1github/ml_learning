# process

> catagorical data classification
* Nominal
    * one hot encoding

* Ordinal

* label encoding

# ordinal vs label encoding

> input columns (X), if there is a column inside X, contains some ordinal catagorical data.
* we will use ordinal encoding

> input columns (X), if there is a column inside X, contains some ordinal catagorical data. but the output column (y) conytins catagorical data we will use label encoding.
* eg: classification problems
* sklearn class : Label Encoder

# ordinal encoding
> catagorical data contains some order

education : [HS, UG, PG, UG, S]

education_encoded : [1, 2, 3, 2, 0]

> we can usnderstand the data in the edication column forming some kind of order. pg>ug>hs

> it will convert the data into in numeric
