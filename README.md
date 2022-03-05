# Project-4_MachineLearningIntegration
### Understanding COVID-19's Impact on Sales Using a Machine Learning Algorithm - Analysis Brought to You by AWS and Tableau

## Authors

### [Norman Adkins](https://github.com/nladkins)
### [David Dam](https://github.com/2Delta)
### [Louis Cheng](https://github.com/PigionLou)
### [Jae Park](https://github.com/jaep505)

## Background

TALK ABOUT THE DATA AND HYPOTHESIS

## Code - Machine Learning and ETL Approach



## Architecture

### Back-End

Once the ETL the tables were generated, the team needed to have a place to store the data in the structured format identified in the code.  Because there was a clear relationship across the tables and joins would be required, we decided on using a database that uses structured query language (SQL).  We decided to use Postgres because all features of Postgres are completely open-source.  The connect the team used was Amazon Web Services' (AWS) Relational Database Service (RDS).  This offering would allow our front-end to connect to the tables that contain our data.

### Front-end

To deliver the analysis to the end-users, we needed both a front-end user-interface (UI) capable of connecting to a database.  `Flask` was considered first.  However, because we knew the visuals would be continously changing and we needed to immediately see the results, Tableau seemed to be a more viable option.  Two members of the team had licenses available for use.  For the front-end, we utilized Tableau Desktop to generate the visuals which included a live connection on the back-end.  Because Tableau Public does not allow the ability to post visuals with a live connection, we had to perform a data extract in order to publish them online.  

![Source to User](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/Architecture.png?raw=true)

## Analysis

The erratic nature of Covid sales and logistics shows on the forecasting. Using Facebook Prophet's forecasting with the provided sales data used to train shows fluctuations in early forecasting from 2014 to 2018. The tuned Prophet is much more smoothed out and works just like the Tableau forecasting which uses exponential smoothing and is very linear. It is still interesting to see overall sales forecasted in the future is a continued growth in sales. However when the forecasting is seen broken down by months in the year, the forecasting does not really match the sales spikes that occur over the Covid years.

![Tables](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/tables.png?raw=true)

![Tableau Prediction](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/prediction.png?raw=true)

![Trends](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/trend.png?raw=true)

![Dashboard](https://github.com/2Delta/Project-4_MachineLearningIntegration/blob/main/images/dashboard.png?raw=true)




## [FINAL DASHBOARD](https://public.tableau.com/app/profile/jae.park/viz/CovidforecastingwithProphet/Dashboard1#1)
