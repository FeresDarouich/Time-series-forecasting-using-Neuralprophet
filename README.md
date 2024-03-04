# Time-series-forecasting-using-Neuralprophet

![image](https://github.com/FeresDarouich/Time-series-forecasting-using-Neuralprophet/assets/120333973/a790f5b8-674d-4293-a017-b2838b0ea9ae)

NeuralProphet, a successor to Facebook Prophet, it s a scalable, and user-friendly forecasting frameworks. With the proliferation of time series data, explainable forecasting remains a challenging task for business and operational decision making. Hybrid solutions are needed to bridge the gap between interpretable classical methods and scalable deep learning models. We view Prophet as a precursor to such a solution. However, Prophet lacks local context, which is essential for forecasting the near-term future and is challenging to extend due to its Stan backend.
NeuralProphet is a hybrid forecasting framework based on PyTorch and trained with standard deep learning methods. Local context is introduced with auto-regression and covariate modules, which can be configured as classical linear regression or as Neural Networks. Otherwise, NeuralProphet retains the design philosophy of Prophet and provides the same basic model components.

two classes of models exist :

statistical algorithms (ARIMA, GARCH …) which are mathematically explainable knowing the theory
Neural network models, which are eminently more convoluted but have demonstrated their performance
Originally, the will of Facebook with Prophet is to provide an easily workable, tweakable, and explainable tool to predict time series. However, one problem persisted: poor performance. To clear up the issue, NeuralProphet was created.

In short, NeuralProphet = Neural Networks + Prophet

Thus, the intention was to combine the two previous classes by including neural networks in the Prophet (a statistical algorithm). The purpose: gain in efficiency while limiting the loss of interpretability.

![image](https://github.com/FeresDarouich/Time-series-forecasting-using-Neuralprophet/assets/120333973/b48eaed1-7b41-441b-b8f6-a532f4abdd34)


# Features
NeuralProphet provides many time series modeling and workflow features, in a simple package:

Support for global modeling of many time series.

Automatic selection of training related hyperparameters.

Plotting utilities for forecast components, model coefficients and final predictions.

Local context through Autoregression and lagged covariates.

Changing trends and smooth seasonality at different periods.

Modeling of event, holiday, and future regressor effects.

Many customization options, such as regularization.

# Selecting the Hyperparameters
Forecast horizon:
n_forecasts is the size of the forecast horizon. The default value of 1 means that the model forecasts one step into the future.



