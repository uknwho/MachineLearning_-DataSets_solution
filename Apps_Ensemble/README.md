## App Rating predictions

The aim of this NoteBook is to predict the ratings (High or Low) based on the basic features like Number of Installs, Size, Number of Reviews etc. This ia a classification Problem and involves lot of preprocessing of the attributes.

> Column Description

*	App: Application name
*	Category: Category the app belongs to
*	Rating: Overall user rating of the app 
*	Reviews: Number of user reviews for the app
*	Size: Size of the app 
*	Installs: Number of user downloads/installs for the app 
*	Type: Paid or Free
*	Price: Price of the app
*	Content Rating: Age group the app is targeted at - Children / Mature 21+ / Adult
*	Genres: An app can belong to multiple genres (apart from its main category). For eg, a musical family game will belong to Music, Game, Family genres.
*	Last Updated: Date when the app was last updated on Play Store 
*	Current Ver: Current version of the app available on Play Store 
*	Android Ver: Min required Android version 

> Data Preprocessing

* The  "Ratings" attribute has the maximum number of null values, since the Target Column is feature extracted from this column, having null values doesnt make any sense. Hence, the rows with null values in this feature are dropped.
* The Zero values in the 'Price' column are replaced by "free".
* In Price column all the values have a "$" sign, since all have the same currency the symbol is omitted.
* The Size of the app has values in 'M' or 'k' i.e. Mb or kb, which are converted in to kbs.
* Installs here are categorical data, so encoding is done.
* The Year of the last update is extraded from the whole Date.


* Features like APP , Genre, Current ver, Android Ver are dropped as they do no help in model building.
* The Rating colum has been divided into "High" and "Low", this would be the Target column.
* This data set suffers from Data Imbalance, as there are less number of apps with low rating wheen comapred to the high rated apps.

> MODEL BUILDING

Ensemble based on Decision Trees have been used to classify the ratings. 

* The base Decision Tree model has an cross validation accuracy of 80.4% with 2% variation, with reviews being the most important feature, followed by SIZE and Category.
* Random Forest and Bagging Classifier had accuracy of 87.7 and 87.4 respectively with 0.71% and 0.96% variation. A 7% percent increase in accuracy has been obtained over the simple full grown Decision Tree.
* Gradient Boosting and ADA Boosting have accuraccy in the range of 89% but these models are not able to identify the Class 1 (Low rated Apps) which is evident in the Confusion matrix and classification report.
* There is a dip in correct predictions and precision and recall values for the class 1, the model is trained to identify the Class 0 the majority class.
* The Voting Classifiers too are effeccted drastically by the class imbalance but still better than Logistic Regression which could not classify the minority class at all.

> Conclusion

Even though Voting classifiers have greater accuracies with less variance, Random Forest is the Better Model as it is able to identify the minority class. The class imbalance is hindering the accuracies and model is able to identify the dominant class. Classes must be balanced to achieve greater Precision and Recall.

