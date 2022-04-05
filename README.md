# GW-Bootcamp-Project
- Update 3/23/2022: 
    - In the "connection_SQL" file, you can find how to connect the database and transfer each table in dataframe.
    - In the "LinearRegression_populationPredict" file, I tried to predict population based on "market_pop_data" dataset using Linear Regression. Tried to find the highest predicted increased population state. I have to check and update it because the R2 is 99. So it could overfit the model probably due to small size of daaset.
- Update 3/28/2022:
    - In the "LinearRegression_populationPredict" file, the R2 testing (0.9999164)  is higher that R2 training(0.9999204) . Meaning our model is doing good             predicting the 2022 population in each state. 
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
-  
 
### Machine Learning
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
💠 MRE: 39690.7044723
💠  R2 test: 0.99991645029
💠  R2 train: 0.9999204638
💠 R2 weighted: 0.99991645029
Using the model, predicted population of 2022 in each states. 

Sorted them by percentage increse in each city (2022)
![](https://user-images.githubusercontent.com/64121596/161860934-e7740d2e-cd28-4f0b-b9bc-3e28a9943db8.png)
 top 10 city by Predicted percentage increase in 2022: 
![](https://user-images.githubusercontent.com/64121596/161861257-bd09a998-86ec-492c-93fb-a6e5b83af20a.png)
