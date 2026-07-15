# Time-Series-Modelling-Case-Study
Calendar-Aware German Electricity Forecasting
Project Aim

This project studies whether known calendar information can improve German electricity-demand forecasts during public holidays. Instead of selecting one model for every week, the analysis compares normal weeks, Christmas/New Year, Easter and other holiday periods separately.

Data and Forecast Period

The analysis uses hourly German electricity demand from January 2015 to September 2020.

After data preparation:

50,400 hourly observations were retained
Demand was converted from MW to GW
Daily and weekly averages were created
Incomplete boundary weeks were removed
299 complete weeks remained
195 weeks were used for training
The final 104 weeks were used for testing

The weekly test period runs from October 2018 to September 2020.

Calendar Information

The forecasting features include:

Number of holidays in each week
Number of working days
Christmas and New Year indicators
Easter indicators
Weeks before and after major holidays
Month, quarter and week of year
Cyclical seasonal features

Weather variables are also included for conditional comparisons.

Models Compared

The notebook evaluates:

Mean
Naive
Seasonal Naive
Drift
SARIMA
Calendar-only SARIMAX
Weather-only SARIMAX
Full SARIMAX
Load-only Gradient Boosting
Calendar-only Gradient Boosting
Weather-only Gradient Boosting
Full Gradient Boosting
Hourly LSTM

The SARIMA stage examines the required parameter combinations. Gradient Boosting models use recursive forecasts, while the LSTM uses the previous 168 hours to predict the following 24 hours.

Evaluation Approach

Models are assessed using:

MAE
RMSE
MASE
sMAPE
Forecast bias
Prediction-interval coverage
Holiday-week RMSE
Non-holiday RMSE
Christmas/New Year RMSE
Easter RMSE

Chronological splitting, training-only scaling and shifted lag features are used to reduce data leakage.

Main Findings

Seasonal Naive achieved the best overall RMSE of 2.988 GW and remained the strongest model for ordinary weeks and Christmas/New Year.

Calendar-only Gradient Boosting produced the lowest holiday-week RMSE of 4.100 GW. It also performed best around Easter because Easter changes calendar position each year and is not captured reliably by a fixed 52-week repetition.

The results support a situation-based forecasting strategy:

Use Seasonal Naive as the regular weekly forecast
Use Calendar-only Gradient Boosting during Easter and other movable holidays
Treat models using observed future weather as conditional forecasts
Running the Project
Open the notebook in Google Colab or Jupyter Notebook.
Install the required Python libraries.
Run all cells in order.
Allow the SARIMA search and LSTM training to complete.
Review the forecast tables, holiday analysis and final model ranking.
Main Libraries
pandas
NumPy
Matplotlib
SciPy
statsmodels
scikit-learn
TensorFlow
requests
Generated Outputs

The workflow produces:

Data-quality summaries
Holiday-demand comparisons
Christmas and Easter event studies
Stationarity and autocorrelation results
Benchmark forecasts
SARIMA and SARIMAX diagnostics
Gradient Boosting comparisons
LSTM learning curves
Holiday-specific error tables
Final operational model recommendations
