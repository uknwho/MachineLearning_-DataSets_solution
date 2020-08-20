## NBA STATISTICS

The Aim of this note book is to find whether a player has career length more than 5 years based on the statistics of his gameplay. The "nba_logreg.csv" attached to this folder has Statistics of NBA Players like Games played, points etc.  It is depicted in the "TARGET_5Yrs" column, where 0 is for players with lesss than 5 years career and 1 represents players with carrer more than 5 years. The column description is added to the folder.

> ## Column Description ##

* Name : Player Name.
* GP : Games Played.
* MIN : Total Minustes Played.
* PTS : Points Per Game.
* FGM : Field Goals Made.
* FGA : Field Goals Attempts.
* FG% : Field Goal Percentage.
* 3P Made : Three Points made.
* 3PA : Three Points Attempt.
* 3P% : Three Points Percentage.
* FTM : Free throws Made.
* FTA : Free Throws Attempts.
* FT% : Free Throws Percent.
* OREB : Offensive Rebounds.
* DREB : Defensive Rebounds.
* AST : Number of Assists made.
* STL : Steals Made.
* BLK : Blocks.
* TOV : Turnovers.
* Target_5Yrs : Career Length 0 (<5), 1 (>= 5).

The Columns have decimal values indicating that these points , attempts and percentages of various charecteristics like Goals, 3Points, free throws and etc are average values per game. 


[Base_model](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/1_Logisctic_Regression_NBA/nba_logreg_solution_1.ipynb)

In this Notebook, a basic approach is taken by dropping the highly collinear features and handlling the outliers. This model can be treated as the base model, which results in an accuraccy of 69%. The Model has Null values in one column and lots of genuine Outliers, no further preprocessing is required. 

> Null Values

The null values which are present in the FG% is due to the 0 value of the corresponding 'FGA'. Since 'FG%' is calculated by (FGM/FGA)100, the 0 values in FGA produce null values, which must be replaced by zeros instead of median value.

> Outliers

The attributes are average values, since it is a classification problem the exact number would not be required. The outlying data can be either capped to its maximum allowable value or Transformed using basic logarithmic and square root operations. Through iterations the best method to handle outliers is selected.

[Advanced Model](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/1_Logisctic_Regression_NBA/nba_features.ipynb)

In this Notebook both the methods of handling Outliers are evaluated, the Transformation method has yielded in better accuracy. Logistic Regression Model is used to evaluate, the bias error is increased and variance error is reduced.

> PCA

![Heat Map](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/1_Logisctic_Regression_NBA/corr_heatmap.png)

Looking at the Corelation heat map, Most of the columns have good amount of correlation aming them. PCA will reduce the dimensions by capturing the varaince associated among the attributes. 95% of variance is captured with 8 Principal Components. 

Logistic Regression Model has led to a score of 72% on the train set and 70% on the test set. This resulted in a 3% rise in accuracy and dimensions have been reduced to 8.

> Polynomial Feature Generation

The idea is to generate more Features from the existing attributes and select the best features to further train the Model. Feature Slection is done by the Sequential Feature Selection from the mlxtend package. The below graph shows no adverse peak or drop in perforamnce against the number of features. The Performance obtained here is very much similar to that of the PCA transformed Data.

![Feature_Selection](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/1_Logisctic_Regression_NBA/Feature_selection.png)

16 Features are selected as from the next a minute drop in performace is observed. The Recall and precision values suggest that the class imbalnce is a slight hindernce to the classification.

Other classification models predict with lesser accuracies, but the Hyperparameter Optimization will increase it. Since the focus of this project is on Logistic Regression, it is the Primary Model and the results are as follows.

Precision : 0.740
Recall : 0.83
F1 score : 0.79
Accuracy : 0.724

