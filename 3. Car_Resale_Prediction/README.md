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

**Univariate Analysis**

![Univariate Analysis](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/3.%20Car_Resale_Prediction/images/Uni_kde.png)

- Diesel and Petrol are predominant Fuel type.
- Vast Majority of the cars are First Hand.
- Manual Transmission vehicles are more in number but they are significant numner of Automatic Transmission Vehicels as well.
- 5 Seater cars are more prevalent followed by the 7 seaters.
- Most of the attributes exhibit outliers, these outliers have valuable information. The data points follow a patern, outliers are not isolated. Few Points lie farther from the rest of the data in Kilometers_Driven and Price columns. 


> **Models which are robust to Outliers must be employed as the data has significant genuine outliers.**


**Bivariate Analysis**

![Transmission-Price](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/3.%20Car_Resale_Prediction/images/Trans_price.png)

- Automatic(Class 0) has higher price than the Manual(Calss 1) with little few execptions.
- As the Power increases there is a rise in the price, low power vehicles have low price but there is a huge variance at higher price as the price are more scattered widely. High power cars are Automatic Transmission.
- As the power of diesel car increasesthe prices getss higher but that high power petrol cars have diversed prices. Electric (purple) have low power but are costlier than other cars with same power.
- Higher Mileage vehicles have low price and costly cars tend to have low mileage. CNG has the highest mileage and they have low price.
- Engine with low capacity have Manual Transmission as engine capacity gets higher Automatic transmission prevails. the general trend increases the price with increase in engine volume.
- Most of the automatic vehicles have driven for less kilometers. The more kilometers the car has been driven the less price it gets. At the lower end there is no significant pattern.
- Older the car less is the price and latest cars are dominantly automatic.
- 'Owner_type' being majorily dominated by first class does not show any significant pattern making it a weak attribute.
- Price has good correlation with Engine and Power, followed by Transmission and year columns. Diesel and Petrol also show some kind of relation with the Price. Other fuel types hardly have correlation with the target variacle price.

![Fue-Price](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/3.%20Car_Resale_Prediction/images/Fuel_price.png)

> **The Decision trees would result in better solution than Linear Model, the reaason being Data has valuable outliers and Location and company being nominal categories are one hot encoded due to thier large number of classes.**

## **Clustering**

Agglomerative Clustering is appplied on the data set using various Linkage techniques, Ward linkage has proven out to be the optimal method. THe aim of clustering is to group cars based on the independent parameters, like the Larger Vehicles(SUVs and MPVs), Luxury cars, Economic cars and many more. This categorization of cars adds another dimension to the data, Price of the vehicle will have a serious correlation if proper clusters are formed. 

Attributes like Location and Company have not been included in the Clustering as the label encoding has incoporated an order among the classes. 'Owner_type' is majorily dominated by one class and thus will not be effective in cluster formation. Kilometers Driven has huge outliers, the clustering techniques are not robust to outliers, therefore it is dropped. Effectively trying to cluster the cars based on the Power, Mileage, Seats and Engine Capacity.

![Hierarchical](https://github.com/uknwho/MachineLearning_-DataSets_solution/blob/master/3.%20Car_Resale_Prediction/images/G3_Clustering.png)

In the above Clustering image, the data can be either categorised to 3 or 5 Clusters. At 120 threshold, three clusters are formed which are represented by Orange, Green and Red. If the threshold is decreased to 100, the Green and the Red clusters are further split into smaller clusters. both these clusters are formed at a good distance suggesting that they are different from each other.

**Understanding the Clusters Formed.**

The boxplot has been plotted with the groups against Features - Transmission, Mileage, Engine, Power, Seats, and Fuel. with the boxplot the aim is to identify what these cluster represent.
* Cluster 0 :
All the Vehicles belong to automatic Transmission, with high Engine and Power Capacity, this cluster contains vehicles upto 8 seats and majorily Diesel type with few petrol outliers. Though the mileage box plot is wide spread this cluster has the lower mileage with few outliers.

* Cluster 1 :
This cluster belong to non-Diesel Vehicles with low Engine capacity, Power output and Better mileage compared to the Cluster 0. These vehicles are prdoiminantly 5 seater with few 4 and 6 seater aswell. These are the economic non-diesel cars. LPG and CNG belong to this cluster identified in the mileage boxplot.

* Cluster 2 :
 The Third cluster is again Diesel type with no petrol and electric vehicels. These cars have the highest mileage which is clearly distinguished in the boxPlot, with Low engine and power capacity making them economic diesel 5 seater cars.
 
 * Cluster 3:
 These aree the big vehicles with more than 6 seater. This groups has the lowest mileage (boxplot mean), with high engine and power output to support the high requirement of the large vehicle. these are again majorily dominated by Diesel with few Petrol Vehicles.
 
 * Cluster 4:
This cluster belong to petrol and electric (lowest engine capacity in mileage boxplot) vehicles, relativley higher engine capacity and power output comapre tot he cluster 1(Petrol). This group has seats rangine from 2 to 5

  
