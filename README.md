# Up and Coming Real Estate Market Hotspots

## Selected Topic:
### For our final project, our group will be creating a machine learning model that will predict the next up-and-coming cities in the US using historical housing market data from 2012 to 2021. 

## Why this topic?
### The reason the team selected the topic is due to an inherent passion derived from living through current events. According to the [Pew Research Center](https://www.pewresearch.org/social-trends/2020/01/09/trends-in-income-and-wealth-inequality/#:~:text=From%202015%20to%202018%2C%20the,era%20of%20the%20late%201990s.), “From 2000 to 2018, the growth in household income slowed to an annual average rate of only 0.3%. If there had been no such slowdown and incomes had continued to increase in this century at the same rate as from 1970 to 2000, the current median U.S. household income would be about $87,000, considerably higher than its actual level of $74,600.” Meanwhile, a CNBC 2017 [report](https://www.cnbc.com/2017/06/23/how-much-housing-prices-have-risen-since-1940.html) shows housing prices outpacing inflation .  Thus, income has remained relatively stagnant but housing prices continue to increase at astronomical rates. For members of our team who are current home owners or even individuals looking to buy a home, we are living through this era where homes are quite factually unaffordable based on areas. For our team members living in the DMV area that fact is all too real. 

### This project is a means to shed light on such hardships currently faced and to potentially show an alternative path. Is there a city out there with an affordable home that will eventually be the next San Diego or Washington DC? Can we get it at an investment level cost? Can we live out the American Dream of one day owning an affordable home? These are some of the questions we hope to answer. Not just for this project but also for ourselves. Using the data we have available, we hope to be able to use machine learning to predict where the next big housing boom will be, potentially allowing users to invest in real estate in those areas before home prices skyrocket.

## Data Source
### Our team found [redfin housing market information](https://www.kaggle.com/thuynyle/redfin-housing-market-data?select=state_market_tracker.tsv000) via Kaggle.com .  Utilizing data cleansing the team is analyzing the data based on factors such as region by month, region by year, median sale price versus median list price, the amount of homes sold vs new listings, the median amount of days on the market before a home is bought, and the amount of times a home is sold above list price. These are some data points that can help answer some of the questions above based on numerous hypotheses. 

## Questions we hope to answer through our analysis
### Some of the following hypotheses and related data points are listed below:
###   1. Does the difference between the median sale price and the median list price appear to grow in cities that are up and coming? In other words, if we analyze the median sale price – median list price should we start to see exponential growth in cities that are about to become big?
###   2. Do the median number of days a home is on the market tend to indicate an increase in demand? In other words, if the homes are being sold faster once listed, does that mean more people are trying to get in on the market? If so, does that mean that the city is already a big city?
###   3. Do the number of homes sold mean that the properties are in more demand or that the people living there are trying harder to leave?

### Finally, based on the above hypotheses what other data points could we potentially incorporate? Should we incorporate census data to see if there’s an inflow and outflow of people from one state to another? Should we see if there’s just a surge of wealthy individuals that happen to move into an area causing a drastic increase in sale prices? At the moment this is still something we are working on.

## Data Cleanup
### Our team used a number of tool to clean up our datasets, create database connections, and visualize our findings. Our primary tool  for data cleanup was Jupyter notebook. After importing our CSV files, our team removed unneccessary fields, removed null values, and grouped our data by location and year. 
![Jupyter](https://github.com/laurenweiner/GW-Bootcamp-Project/blob/brian/State%20Market%20Data%20Cleanup.PNG)

### After our datasets had been properly cleaned, our team utilized AWS and PG Admin to establish a database structure that would be used for our final project. We created tables using an SQL query similar to the one below, assigning the proper data types prior to importing our cleaned CSV files.

* CREATE TABLE county_market_tracker (
    * period_begin date NULL,
	  * period_end date NULL,
	  * period_duration integer NULL,
	  * region_type varchar(50) NULL,
	  * region_type_id varchar(50) NULL,
	  * table_id varchar(50) NULL,
	  * is_seasonally_adjusted char(1) NULL,
	  * region varchar(50) NULL,
	  * city varchar(50) NULL,
	  * state varchar(50) NULL,
	  * state_code char(2) NULL,
	  * property_type varchar(50) NULL,
	  * property_type_id varchar(50) NULL,
	  * median_sale_price double precision NULL,
	  * median_sale_price_mom double precision NULL,
	  * median_sale_price_yoy double precision NULL,
	  * median_list_price double precision NULL,
	  * median_list_price_mom double precision NULL,
	  * median_list_price_yoy double precision NULL,
	  * median_ppsf double precision NULL,
	  * median_ppsf_mom double precision NULL,
	  * median_ppsf_yoy double precision NULL,
	  * median_list_ppsf double precision NULL,
	  * median_list_ppsf_mom double precision NULL,
	  * median_list_ppsf_yoy double precision NULL) 

### Once our tables were imported into PG Admin, we joined our market datasets with census population data. Our analysis aims to identify future lucrative housing markets by location and population growth is an important factor in that anlysis.
![Postgres](https://github.com/laurenweiner/GW-Bootcamp-Project/blob/brian/Postgres%20-%20Table%20Join.PNG)

## Analysis

## Data Visualization

# Machine Learning Model to predict the "On demand" cities and states 
### ETL :
Columns Overview (21):
-  'state_name':
    47 states
-  'year_data':
    2012 - 2021
-  'median_sale_price':
-  ![](https://user-images.githubusercontent.com/64121596/161854187-4f1a1d27-21fa-443c-8738-817ec0b17543.png)  ![](https://user-images.githubusercontent.com/64121596/161855852-8aa9388d-49cb-4502-8094-6231dbbe47f2.png)
-  'median_list_price':
- ![](https://user-images.githubusercontent.com/64121596/161854444-93188520-bc06-4326-8bc1-61ce94638492.png). ![](https://user-images.githubusercontent.com/64121596/161856003-04822dab-ee44-4182-bd51-586d576ada6c.png)
-  'homes_sold':
-  ![](https://user-images.githubusercontent.com/64121596/161854630-910e64d7-4aa8-45c5-a4ff-3aa648931135.png) ![](https://user-images.githubusercontent.com/64121596/161856096-e8b40669-88ce-4c65-85e3-8beb61c985ed.png)
-  'inventory': 
-  ![](https://user-images.githubusercontent.com/64121596/161854749-a9e1cf1d-1b03-4bd7-8747-e28263097e39.png) ![](https://user-images.githubusercontent.com/64121596/161855680-9defadb4-a3be-4584-b713-d61efc809dea.png)
-  'new_listings': 
-  ![](https://user-images.githubusercontent.com/64121596/161854833-00df5dca-2af4-4c8e-9326-370ad1906e1b.png) ![](https://user-images.githubusercontent.com/64121596/161856807-cf74d674-bea8-4a99-b170-0aec91f66c10.png)
-  'avg_sale_to_list':
-  ![](https://user-images.githubusercontent.com/64121596/161854956-45eb66da-85df-413e-a8d6-4964b1d7a57c.png) ![](https://user-images.githubusercontent.com/64121596/161856888-d4b8223f-3e16-496c-9390-eb379f091903.png)
-  'sold_above_list':
-  ![](https://user-images.githubusercontent.com/64121596/161855085-a6d51af0-06c0-48cb-8bc1-846d36b6f8cb.png) ![](https://user-images.githubusercontent.com/64121596/161857028-178f7380-d987-4a67-ae98-024ba8f76527.png)
-  population estimates from 2010 to 2021 (12 columns)
 
## Machine Learning on Population Prediction
:dart: Target: population estimate 2021

:heavy_check_mark: Variables: other columns excluding the Target

1. Dropped the outlier from population 2021 estimate. Dropped "California".
Population Estimate 2021 histogram:
![](https://user-images.githubusercontent.com/64121596/161857409-5767c389-6e50-465a-9902-7340727b5823.png)
2. Using Standard Scaler, Scaled all the data. (Target and variables)
3. Split the data to training vs test 75 vs 25
4. Resampled the data using SMOTE algorithm
5. Used Linear Regression to predict the :dart: Target. 
### Our Linear Regression Model Metrics:
- 💠 MRE: 39690.7044723
- 💠  R2 test: 0.99991645029
- 💠  R2 train: 0.9999204638
- 💠 R2 weighted: 0.99991645029
Using the model, predicted population of 2022 in each states. 

### Cross Validation
![](https://user-images.githubusercontent.com/64121596/162147864-d9429140-1e4e-460c-948c-52e81213fc90.png)
Fitting 5 folds for each of 19 candidates, totalling 95 fits
GridSearchCV(cv=KFold(n_splits=5, random_state=100, shuffle=True),
             estimator=RFE(estimator=LinearRegression()),
             param_grid=[{'n_features_to_select': [1, 2, 3, 4, 5, 6, 7, 8, 9,
                                                   10, 11, 12, 13, 14, 15, 16,
                                                   17, 18, 19]}],
             return_train_score=True, scoring='r2', verbose=1)
             

![](https://user-images.githubusercontent.com/64121596/162149684-7b299c28-3e62-4dfb-af0f-fed04d60da77.png)


Then we looked at the feature importance:
![](https://user-images.githubusercontent.com/64121596/162149855-2be00dbe-8140-410f-b91f-63a2512e5e11.png)

This means we could predict the population 2022 by the first 5 population yearly data.

- Top 10 predicted highest increse in each city (2022)
![](https://user-images.githubusercontent.com/64121596/161860934-e7740d2e-cd28-4f0b-b9bc-3e28a9943db8.png)
- top 10 city by Predicted percentage increase in 2022: 
![](https://user-images.githubusercontent.com/64121596/161861257-bd09a998-86ec-492c-93fb-a6e5b83af20a.png)

please refer to the jupyter notebook [link](https://github.com/laurenweiner/GW-Bootcamp-Project/blob/oyuka/LinearRegression_populationPredict.ipynb).
## Multiple Regression on sold_above_list
Then we looked at the other variables since we predicted the highest growing states in the next year. 
![](https://user-images.githubusercontent.com/64121596/162151622-f95632bd-86d6-4cf5-adf6-ae54cd2bb848.png)
   Other than the median price sold, if we look at the homes sold numbers. It was highly correlated to inventory and the number of new listings in the area. 

To predict the sold_above_list
1. Cleaned the dataset by droping NAs, dropin duplicates, set the index as state_name (object).
2. Dropped the outlier. Median Sale price highest city : "Nevada nonmetropolitan area"
3. 🎯 target: sold_above_list
📎 variables : year_data, median_sale_price, median_list_price, homes_sold, avg_sale_to_list
	- Did not use inventory and new listings columns because these 2 are highly correlated with homes_sold.
4. Normalized the data by using Standard Scaler
5. Split the dataset by training and test. 
6. Our Regression model metrics:
MRE: 0.05940403316904764
R2 test: 0.5704715858517697
R2_train: 0.483487561943463
R2 weighted: 0.5704715858517697
7. Fitting 5 folds for each of 6 candidates, totalling 30 fits
GridSearchCV(cv=KFold(n_splits=5, random_state=100, shuffle=True),
             estimator=RFE(estimator=LinearRegression()),
             param_grid=[{'n_features_to_select': [1, 2, 3, 4, 5, 6]}],
             return_train_score=True, scoring='r2', verbose=1)
	     ![](https://user-images.githubusercontent.com/64121596/162160498-2cb06021-b711-4ad7-a438-fba538760e4b.png)
![](https://user-images.githubusercontent.com/64121596/162160712-d2c054f8-d54a-4d22-809f-2dcf4bd97ce6.png)

Final model by using 3 features:
R2 is 56%.
please refer to the jupyter notebook [link](https://github.com/laurenweiner/GW-Bootcamp-Project/blob/oyuka/metro_market_tracker.ipynb)
### Our team used Tableau to visualize our findings. The link to the story can be found [here](https://public.tableau.com/app/profile/lauren.weiner/viz/GWDataAnalyticsBootcampProjectDraft/Story1).
