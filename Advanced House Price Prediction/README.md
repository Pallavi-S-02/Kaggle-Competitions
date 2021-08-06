# Advanced-House-Price-Prediction

The project will predict the cost price of houses with the help of linear regrerssion

# Essential Packages required to be installed:

1) Numpy
2) Pandas
3) matplotlib
4) seaborn
5) scipy

# Description:

1) Ensure that the files containing datasets ie. train.csv and test.csv must be imported. The model will be trained on the basis of the results of train.csv file and then model will predict the results for test.csv.
## Data Processing:
### Outliers 
We have drawn a subplot for "GrLivArea" feature.We can see at the bottom right two with extremely large GrLivArea that are of a low price. These values are huge oultliers. Therefore, we can safely delete them.
Note :
Outliers removal is note always safe. We decided to delete these two as they are very huge and really bad ( extremely large areas for very low prices).

There are probably others outliers in the training data. However, removing all them may affect badly our models if ever there were also outliers in the test data. That's why , instead of removing them all, we will just manage to make some of our models robust on them.
