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

3) We have plotted a distplot for all the values/results of SalePrice in train.csv. Since the skewness and kurtosis for the distplot came out to be quite large thus not acceptable(skewness = 1.8828757597682129, kurtosis= 6.536281860064529), thus we had performed log transformation for the function that made our graph linear with even very less skewness and kurtosis.(skewness= 0.12134661989685333, kurtosis= 0.809519155707878.

4) Skewness determines the normal distribution of the graph in form of floating point numbers. when skewness==0, this shows that dataset is normally distributed.

5) Kurtosis determines the weightage of dataset on the basis of weights of tails. More is the kurtosis, heavier is the tail of dataset.

## Features engineering:
6) We have then calculated pairwise correlation of each column with every other column using corr() function. This was required to make a heatmap for the dataset that shows correlation of columns graphically.

7) Make sure to fill all missing values in the train as well as test dataframe . We had already combined both of them into a new dataframe called as all_data.Plot a subplot to check percent missing data by feature.We can see that "PoolQC", "MiscFeature", "Alley", "Fence", "FireplaceQu" have high missing values.We had also used LabelEncoder that assign label numeral to each and every data value in a dataseries.

8) Box cox tranformation was required to reduce skewness of some highly skewed data. It is a way to transform non normal depandant variables into a normal shape. This transform was successful with the help of function boxcox1p() present in scipy.special . We had added some dummy catagorical features using pandas.get_dummies().

## Modelling:
9) For modelling we have used LASSO Regression, Elastic Net Regression, Kernel Ridge Regression, Gradient Boosting Regression , XGBoost , LightGBM. For linear regression modelling, I've made use of Lasso Regression and Gradient Boost Regression methods. a] Lasso Regression: a type of linear regression that uses shrinkage. Data values are shrinked towards a central point like mean. b] Gradient Boosting Regression: used for identifying errors in prediction. It minimizes overall error by combining existing and prevois model.

10) Other important things used here include usage of RobustScaler, k-fold cross validation and transformer Mixin a] RobustScaler: This scaler removes median and scales data according to quantile range b] k- fold cross validation: provides train/test indices to split data in train/test sets c] Transformer Mixin: Mixin class for all tranformers

## Stacking models:
### Simplest Stacking approach : Averaging base models

11)We made a class AveragingModels that finds the average between the predictions of Elastic Net Regression, Gradient Boosting Regression, Kernel Ridge Regression and LASSO Regression.Of course we could easily add more models in the mix.

### Less simple Stacking : Adding a Meta-model
In this approach, we add a meta-model on averaged base models and use the out-of-folds predictions of these base models to train our meta-model.

The procedure, for the training part, may be described as follows:

i) Split the total training set into two disjoint sets (here train and .holdout )

ii) Train several base models on the first part (train)

iii) Test these base models on the second part (holdout)

iv) Use the predictions from 3) (called out-of-folds predictions) as the inputs, and the correct responses (target variable) as the outputs to train a higher level learner called meta-model.

The first three steps are done iteratively . If we take for example a 5-fold stacking , we first split the training data into 5 folds. Then we will do 5 iterations. In each iteration, we train every base model on 4 folds and predict on the remaining fold (holdout fold).

So, we will be sure, after 5 iterations , that the entire data is used to get out-of-folds predictions that we will then use as new feature to train our meta-model in the step 4.

For the prediction part , We average the predictions of all base models on the test data and used them as meta-features on which, the final prediction is done with the meta-model.

![QBuDOjs](https://user-images.githubusercontent.com/83487183/128514228-1ce70fe2-16f2-4674-921d-4360ec2d17b9.jpg)

### Stacking Averaged models Score:

To make the two approaches comparable (by using the same number of models) , we just average Enet KRR and Gboost, then we add lasso as meta-model.
We get again a better score by adding a meta learner.
### Ensembling StackedRegressor, XGBoost and LightGBM
We add XGBoost and LightGBM to the StackedRegressor defined previously.
We first define a rmsle evaluation function.

12) Finally we made accurate predictons from our side and stored them all in submission.csv file.

This project was made for learning perspective. The data set for the model can also be found at kaggle, below is the link to access dataset. 
 https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data


 
