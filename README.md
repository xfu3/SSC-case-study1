# 202 SSC-case-study in Data Analysis (**Predicting hourly electricity demand in Ontario**)

[Case study overview](https://ssc.ca/en/case-study/predicting-hourly-electricity-demand-ontario)

[Case study result](https://ssc.ca/en/publications/ssc-liaison/vol-34-3-june-2020/results-ssc-2020-case-studies-data-analysis-competition)

## Introduction:
Models able to accurately predict hourly electricity demand can help energy
production meet trending energy demands, in terms of long term trends over years, and finely
across seasons and even days of the week.

## Objective of the study: 
In this case study, we build a predictive model for sector-specific hourly electricity
demand also able to predict annual demand. We do so using 14 years of real-world data from
Ontario, including sector-aggregated hourly demand, sector-specific annual totals, and
population-weighted hourly weather data. Our methods focus specifically on seasonal trend
estimation using a variety of techniques including smoothers, harmonic regression, autoregression,
and regression trees to address real-world difficulties in the data.

## Methods of the study:
With a focus on smoothing estimators, we first consider a multi-seasonal time series
decomposition using LOESS and Friedman’s super-smoother for seasonal and long-term trends,
respectively. We further improve the fit of the model using a data-motivated AR(2) residual model.
Second, we consider a number of harmonic autoregressive models. This includes a classical
ARIMA time series model accounting for scalar covariates and dynamic least-squares and quantile
regression models. These three models incorporate harmonic regression terms with pre-specified
frequencies and orders (tuned by cross-validation), electricity demand lag terms, and weather
predictors. Third, we consider a machine-learning oriented XGBOOST model that uses boosting to
build an ensemble of regression trees optimized by hyperparameter tuning[**Grid search**]. Finally, we fit
a deep learning model[Bidirectional LSTM] that is widely applied in large scale time series dataset.

## Results of the study:
Each model was evaluated using leave-one-out absolute error in predicting sector-specific
energy demand, averaged over 14 years. As a baseline, a Naive model was also fit using only the
annual demand targets. The flexibility of the MSTL model’s smoothing estimator is a benefit over
other parametric models, though its variability may negatively impact test set predictions for some
years. Nonetheless, the residual of the AR model helped mitigate the effect of estimator variability.
The dynamic regression model, particularly the quantile model, performed reliably across all sectors
but did not greatly outperform other models in any. The XGBOOST model found only the first and
second lagged predictors to be useful, while the third lag and other weather variables were not
found to be important.



## Conclusions: 
XGBOOST outperformed the other models in MAE and time efficiency. This was expected because XGBOOST is a
very poweful machine learning tool. The reason why Bidirectional LSTM underperformed may be due to lack of
training and small sample size. However, it was not wrong buidling parametric models becasue they take
advantage of good interpretation, which is essential in industries.
