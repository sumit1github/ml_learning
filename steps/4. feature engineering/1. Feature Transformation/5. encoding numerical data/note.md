# why a numerical data needs encoding
we know the numerical data is good for the ml algo. Then why we need to encode the numerical data.

> user case

Let we are working with a palystore app data. There are diffrent types of application present in the playstore. There is a column which couts the number of downloads. There are apps having download count 23, on the other side there are some very populer apps having the download count over 10123452.

> This numerical values can't be in normal distrubution

> so the approch will be, need to reform the download data into like

Download_tarnsform
10+
100+
500+
1000+
1M+

# Ther are 2 famous methods
1. Discretixation(Binning) and   2. Binarization


#### Discretixation(Binning)
So transforming a continuous data into range.
10 to 100, 200 to 300
> pros:
* To handle Outliers
* improve value spread

> Binning
* unsupervid binning
    * Equal width(uniform)
    * equal frequency (quantile)
    * kmens binning
* supervised
* custom binning
