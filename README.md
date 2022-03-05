# Project-4_MachineLearningIntegration
### Understanding COVID-19's Impact on Sales Using a Machine Learning Algorithm - Analysis Brought to You by AWS and Tableau

## Authors

### [Norman Adkins](https://github.com/nladkins)
### [David Dam](https://github.com/2Delta)
### [Louis Cheng](https://github.com/PigionLou)
### [Jae Park](https://github.com/jaep505)

## Background

With ever extending lead times and shipping delays as a result of the explosive growth experienced during COVID pandemic, accurate time series analysis and forecasting are necessary for inventory management and production planning over an entire range of products in order to maintain appropriate inventory levels to meet sales demands over the next 710+ days to determine quantities to place orders with our factory by SKU. Supply chain shortages have exacerbated the situation as sales were capped by available inventory.

Hypothesis -

Years prior to COVID 2014-2019 should follow a normal trend and the model will test accurately

COVID Years 2020-2021 have abnormally high sales growth and the forecast will under predict sales

Future forecasting 2022-2023 will be challenging and the model will over predict if 2020-2021 are used in training

## Code - Machine Learning and ETL Approach

Actual sales data of my company’s products from 2014 through 2021 extracted as a CSV from our ERP software.

Columns were significantly reduced to remove sensitive information that was outside of the scope of this project to maintain confidentiality.

The relevant data for this project is primarily the material, month, and invoiced quantity to perform a time series analysis.

Pandas was utilized to read the CSV and transform the data by grouping by month and material and aggregating the invoiced quantity, then to match Prophet’s required input format. 

Prophet is able to fit non-linear trends with seasonal effects and shifts in trends and was used to model the sales data and forecast demand over the next 24 months to match lead times for the purpose of inventory/production planning. Cross-validation was performed to measure performance and tune hyperparameters.

After tuning the hyperparameters, we are able to minimize root mean squared error to under 500 units per year when training the model to fit 2014-2017 data and testing it to 2018-2019 sales. The best hyperameters are then utilized to fit the model to the entire sales history from 2014 through 2021 and predict values for 2022 and 2023.

Spark was then utilized to load the results to RDS.

## Architecture

### Back-End

Once the ETL the tables were generated, the team needed to have a place to store the data in the structured format identified in the code.  Because there was a clear relationship across the tables and joins would be required, we decided on using a database that uses structured query language (SQL).  We decided to use Postgres because all features of Postgres are completely open-source.  The connect the team used was Amazon Web Services' (AWS) Relational Database Service (RDS).  This offering would allow our front-end to connect to the tables that contain our data.

### Front-end

To deliver the analysis to the end-users, we needed both a front-end user-interface (UI) capable of connecting to a database.  `Flask` was considered first.  However, because we knew the visuals would be continously changing and we needed to immediately see the results, Tableau seemed to be a more viable option.  Two members of the team had licenses available for use.  For the front-end, we utilized Tableau Desktop to generate the visuals which included a live connection on the back-end.  Because Tableau Public does not allow the ability to post visuals with a live connection, we had to perform a data extract in order to publish them online.  

![Source to User](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/Architecture.png?raw=true)

## Analysis

The erratic nature of Covid sales and logistics have shown in forecasting when using other methods such as exponential triple smoothing that have resulted in suspiciously high predictions. Thus it was necessary to test other models. Using Facebook Prophet's default parameters to forecast with the provided sales data shows monthly fluctuations as it attempts to model for seasonality. After tuning the hyperparameters, the lowest root mean squared error of 367 is reached by smoothing change points and seasonality effects slightly in order to remove noisy data points. The model seems to fit the data reasonably well when examining by year rather than by month; as it is impossible to forecast for the erratic fluctuations in monthly sales due to large inventory sell offs and limitations of available inventory but could be closer if lead times were shorter. The prophet model seems to be a bit mmore conservative in its predictions vs ETS and seems to be decent candidate for forecasting future demand, but individual analysis of more SKUs will be necessary.

![Tables](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/tables.png?raw=true)

![Tableau Prediction](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/prediction.png?raw=true)

![Trends](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/trend.png?raw=true)

![Dashboard](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/dashboard.png?raw=true)




## [FINAL DASHBOARD](https://public.tableau.com/app/profile/jae.park/viz/CovidforecastingwithProphet/Dashboard1#1)
