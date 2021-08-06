# Advanced-House-Price-Prediction

The project will predict the cost price of houses with the help of linear regrerssion

## Essential Packages required to be installed:

1) Numpy
2) Pandas
3) matplotlib
4) seaborn
5) scipy

## Description:

1) Ensure that the files containing datasets ie. train.csv and test.csv must be imported. The model will be trained on the basis of the results of train.csv file and then model will predict the results for test.csv.
## Data Processing:
### Outliers 
2) We have drawn a subplot for "GrLivArea" feature.We can see at the bottom right two with extremely large GrLivArea that are of a low price. These values are huge oultliers. Therefore, we can safely delete them.
#### Note :
Outliers removal is note always safe. We decided to delete these two as they are very huge and really bad ( extremely large areas for very low prices).

There are probably others outliers in the training data. However, removing all them may affect badly our models if ever there were also outliers in the test data. That's why , instead of removing them all, we will just manage to make some of our models robust on them.

3)We have plotted a distplot for all the values/results of SalePrice in train.csv. Since the skewness and kurtosis for the distplot came out to be quite large thus not acceptable(skewness = 1.8828757597682129, kurtosis= 6.536281860064529), thus we had performed log transformation for the function that made our graph linear with even very less skewness and kurtosis.(skewness= 0.12134661989685333, kurtosis= 0.809519155707878.
4)Skewness determines the normal distribution of the graph in form of floating point numbers. when skewness==0, this shows that dataset is normally distributed.
5)Kurtosis determines the weightage of dataset on the basis of weights of tails. More is the kurtosis, heavier is the tail of dataset.
## Features engineering:
6)We have then calculated pairwise correlation of each column with every other column using corr() function. This was required to make a heatmap for the dataset that shows correlation of columns graphically.
7)Make sure to fill all missing values in the train as well as test dataframe . We had already combined both of them into a new dataframe called as all_data.Plot a subplot to check percent missing data by feature.We can see that "PoolQC", "MiscFeature", "Alley", "Fence", "FireplaceQu" have high missing values.We had also used LabelEncoder that assign label numeral to each and every data value in a dataseries.
8)Box cox tranformation was required to reduce skewness of some highly skewed data. It is a way to transform non normal depandant variables into a normal shape. This transform was successful with the help of function boxcox1p() present in scipy.special . We had added some dummy catagorical features using pandas.get_dummies().
## Modelling:
9)For modelling we have used LASSO Regression, Elastic Net Regression, Kernel Ridge Regression, Gradient Boosting Regression , XGBoost , LightGBM.

