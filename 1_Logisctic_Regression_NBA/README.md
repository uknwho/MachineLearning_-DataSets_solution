This is a Data Set to practice calssification with logistic regression.

Logistic Regression is calssifier model based on linear Regression. The Response variable can be BInary class or multi classs with cateorical or numericals classes. It is simple to implement and provides probabilities for each class. The data set needs to be reqularised since high magnitude variabels might ifluence the predictions since its based on Linear regression. Logistoc Regression is highly effected by outliers. This model assumes attributes to be independent, so collinearity should be avoided.

The "nba_logreg.csv" attached to this folder has Statistics of NBA Players like Games played, points etc. The goal is to classify the players based on thier statistics, who has a carrer length of greater than 5 years. It is depicted in the "TARGET_5Yrs" column, where 0 is for players with lesss than 5 years career and 1 represents players with carrer more than 5 years. The column description is added to the folder.

> ##**Column Description**##

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

In this Notebook, a basic approach is taken by dropping the highly collinear features and handlling the outliers. This model can be treated as the base model, which results in an accuraccy of 69%. The null values are filled by the medians.


