---
description: >-
  Forecasting allow you to predict a value in the future based on past data. It
  uses machine learning techniques to output the probable future.
---

# 🔮 Forecasting

## How to create a forecast

The forecast capability only works on timeseries chart that don't have a dimension grouping. When the capability is available it is materialized by a Create Forecast button in the chart area as shown below.

![Forecast button](<../../.gitbook/assets/image (223).png>)

When clicking on the button we will compute the next probable value based on the value that are displayed on the chart, therefore the more value are displayed on your chart the more accurate the forecast will be. We will forecast 10% of the number of steps that are used in your chart or a minimum or 1 value. For instance if your displaying a single value every day for a month we will predict 3 steps forward (30 days \* 10% = 3 days). If you display a week of values we will forecast 1 day (7 days \* 10% = 0.7 days rounded to 1).&#x20;

![Forecasted value](<../../.gitbook/assets/image (222).png>)

When you create your forecast you can see the probable value as well as the upper bound and lower bound for the forecasting.

## How does it work

We use under the hood [ARIMA](https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/) to predict the future values of your time series. This is a state of the art algorithm that is used in production by multiple companies.
