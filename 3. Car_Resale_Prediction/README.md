**Used Car DataSet**

The aim of the project is to build a model that can predict the Used car value at which it would be sold. The data set is available in Kaggle. This is a regression problem as the Price of the car is to be predicted.

> Link to DataSet : https://www.kaggle.com/avikasliwal/used-cars-price-prediction

Description of the Columns in the dataset.

- 'Unnamed: 0'          : Index of the DataSet.
- 'Name'                : The Car Model name starting with the Brand Name continued by the Model name. 
- 'Location'            : The Current Location of the Car. 
- 'Year'                : In which year the Car was Manufactured.
- 'Kilometers_Driven'   : A continous variable expressing the distance traveled by the car in kilometers.
- 'Fuel_Type'           : Type of Fuel the car uses.
- 'Transmission'        : 'Automatic' or 'Manual' Transmission.
- 'Owner_Type'          : No of different owners (First, Second, Third, etc).
- 'Mileage'             : Distance traveled by the car per unit consumption of the Fuel(kmpl).
- 'Engine'              : The Capacity of the Engine (CC).
- 'Power'               : Brake Horse Power of the Car (bhp).
- 'Seats'               : No of seats in the car.
- 'New_Price'           : The current price of the car.(lakhs and crores)
- 'Price'               : The resale price value.

> **[Car_resale_EDA.ipynb](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/3.%20Car_Resale_Prediction/Car_resale_EDA.ipynb) contains the preprocessing and Exploratory Data Analysis** 

The "Unnamed:0" column should be dropped as it is the serial no of the observations. "New_Price" column has many missing values, approximately only 14% of the observations have New_Price values with 540 unique values. Filling so many missing values is not ideal, dropping the column could reduce the noise. But the attribute can provide goof information which is tested in iterations.

'Mileage', 'Engine' and 'Power' have units associated making them object type. Data CLean up is done to transform them to Numerical Data Type. The missing values in these attributes are filled by the respective Medians.

There are various car Models (1876) so the brand name is extracted from the 'Name' to a new attribute 'Company'.

**Conclusisons of Univariate Analysis**

- Diesel and Petrol are predominant Fuel type.
- Vast Majority of the cars are First Hand.
- Manual Transmission vehicles are more in number but they are significant numner of Automatic Transmission Vehicels as well.
- 5 Seater cars are more prevalent followed by the 7 seaters.
- Most of the attributes exhibit outliers, these outliers have valuable information. The data points follow a patern, outliers are not isolated. Few Points lie farther from the rest of the data in Kilometers_Driven and Price columns. 


> **Models which are robust to Outliers must be employed as the data has significant genuine outliers.**


**Conclusions of Bivariate Analysis**

- Automatic(Class 0) has higher price than the Manual(Calss 1) with little few execptions.
- As the Power increases there is a rise in the price, low power vehicles have low price but there is a huge variance at higher price as the price are more scattered widely. High power cars are Automatic Transmission.
- As the power of diesel car increasesthe prices getss higher but that high power petrol cars have diversed prices. Electric (purple) have low power but are costlier than other cars with same power.
- Higher Mileage vehicles have low price and costly cars tend to have low mileage. CNG has the highest mileage and they have low price.
- Engine with low capacity have Manual Transmission as engine capacity gets higher Automatic transmission prevails. the general trend increases the price with increase in engine volume.
- Most of the automatic vehicles have driven for less kilometers. The more kilometers the car has been driven the less price it gets. At the lower end there is no significant pattern.
- Older the car less is the price and latest cars are dominantly automatic.
- 'Owner_type' being majorily dominated by first class does not show any significant pattern making it a weak attribute.
- Price has good correlation with Engine and Power, followed by Transmission and year columns. Diesel and Petrol also show some kind of relation with the Price. Other fuel types hardly have correlation with the target variacle price.
