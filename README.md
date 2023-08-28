# Analysing-a-Time-Series-dataset-using-a-variety-of-models-and-data-classification-using-Logistic-Regression
This project presents the results of two separate analyses: a time series analysis of monthly and yearly average temperatures in Armagh from 1844 to 2004, and a binary logistic regression analysis of a dataset containing details of blood samples of diabetic patients collected in an Iraqi University Hospital in 2020. The time series analysis provides insights into historical temperature variation patterns in Armagh and can inform future climate projections for the region. The logistic regression analysis facilitates diabetes diagnosis based on blood results and has implications for diabetes diagnosis and treatment in clinical settings. The two analyses detail the process of constructing the model, give an overview of the ultimate model parameters, assess pertinent assumptions, and evaluate the performance and fitness of the model.
# WorkFlow
PART A: Time Series Analyses
1. Assessment of Raw Time Series: The two datasets were visually explored using R programming language. The monthly average temperature dataset ”nitm18442004.csv” contains 1932 observations of the average temperature in Armagh from January 1844 to December 2004, while the yearly average temperature dataset ”nity18442004.csv” contains 161 observations of the yearly average temperature from 1844 to 2004. The monthly average temperature dataset exhibited a distinct seasonal pattern, with higher temperatures in the summer months and lower temperatures in the winter months. This pattern is typical of temperature data in temperate regions.
2. Investigation of Suitable models: In this section, different suitable time series models for both monthly and yearly temperature data were explored using the following categories: i. Exponential Smoothing ii. ARIMA/SARIMA iii. Simple time series models.
(i) Exponential Smoothing: This is a popular forecasting method for univariate time series data that can be applied to monthly and yearly temperature data. Exponentially declining weights are used in exponential smoothing models to predict future values using prior data as a weighted average. It can be fit with different models. Here, the ETS function has been used to automatically aid in choosing the best model to match the data because it has more options and it is generally more powerful. The model summary includes the ETS (Error, Trend, Seasonality) which consists of ETS(A,A,A) and ETS(A,N,N).
(ii) ARIMA/SARIMA: The Arima model was also explored. To apply this approach, we first evaluated the ”ndiffs()” function’s output for our degree of freedom, which gave us d=1. To make the differenced temperature time series stationary, we also produced a plot of it. The Augmented Dickey-Fuller Test (adf.test(ts)) was run to further support this assertion, and the outcomes demonstrated its stationarity. Finding the ARIMA models that match the data the best is done using the Auto- ARIMA function.
(iii) Time Series Models: For the Time series model, Mean and Naive forecast was used. i. Average or Mean Method: This approach adheres to the principle that all future values must equal the average of past data. The mean(train) for the monthly data is 8.494 and for the yearly data is 8.4825. ii. Naive or Random Walk Method: Typically, the forecast for this approach is configured to reflect the value of the most recent observation. For the yearly data, the train[length(train)] is 9.3, whereas it is 5.1 for the monthly data.
3. Forecasting and assessment of the adequacy of the final model: Evaluation of the forecast of monthly and yearly temperature against the actual of data of 2004 was also assessed. different metrics were used such as RMSE,MAE, MAPE, and MASE and the Arima Model gave the best result on the test set as it provided the least RMSE score of 0.7514175 because it measures the average difference between the predicted and actual values.
PART B: Logistic Regression
1. Descriptive Statistics and Visualizations: The objective of the investigation is to estimate a binary logistic regression model to identify diabetes based on blood test data. The dataset consists of 14 variables, including demographic data, blood tests, and the existence or absence of diabetes. To better comprehend the variables and their interactions, exploratory data analysis is the initial step. The logistic regression model is then fitted to the training data once the data has been split into a training and testing dataset. Finally, the model is used to forecast the likelihood of prediabetic subjects receiving a diabetes diagnosis after the model’s performance is assessed using a confusion matrix on the test dataset. The analysis is completed using R in Jupyter Notebook.
2. Modelling Process and Evaluation: Exploratory data analysis preceded the creation of a logistic regression model. The analysis involved understanding variable relationships, identifying outliers/missing data, and checking distribution assumptions using histograms and correlation. Non-normally distributed variables were transformed. Data was split for training/testing, evaluating the model with a confusion matrix. Logistic regression was built using R's 'glm' function, initially involving all transformed predictors. Non-significant predictors were removed through backward stepwise selection with AIC. The final model included 'Chol', 'HbA1c', 'TG', and 'BMI'. Intermediate models were assessed using likelihood ratio tests, AIC/BIC, and coefficient significance/direction.
3. Final Model Performance and Fit: The final logistic regression model displayed strong performance in predicting diabetes based on blood test results. It exhibited statistical significance (p < 0.001) and a deviance of 84.338 on 659 degrees of freedom. The AIC and BIC values were lower for the final model (94.338 and 116.829 respectively), indicating improved fit compared to the initial model. All coefficients were statistically significant (p < 0.05) and aligned with expected associations with diabetes risk. The odds ratios for 'Chol', 'HbA1c', 'TG', and 'BMI' were 2.13, 4.02, 1.97, and 2.18 respectively, indicating increased diabetes odds with higher levels of these variables. The model correctly identified 'prediabetic' cases as diabetic with a 0.89 probability. It offers promise for identifying individuals at risk of diabetes and potentially guiding early interventions. However, the model's applicability beyond its original dataset and single hospital context requires validation. While effective for identifying diabetes risk, it doesn't detail contributing factors, necessitating further research. 
