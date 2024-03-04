# Time-series-forecasting-using-Neuralprophet

![image](https://github.com/FeresDarouich/Time-series-forecasting-using-Neuralprophet/assets/120333973/a790f5b8-674d-4293-a017-b2838b0ea9ae)

NeuralProphet, a successor to Facebook Prophet, it s a scalable, and user-friendly forecasting frameworks. With the proliferation of time series data, explainable forecasting remains a challenging task for business and operational decision making. Hybrid solutions are needed to bridge the gap between interpretable classical methods and scalable deep learning models. We view Prophet as a precursor to such a solution. However, Prophet lacks local context, which is essential for forecasting the near-term future and is challenging to extend due to its Stan backend.
NeuralProphet is a hybrid forecasting framework based on PyTorch and trained with standard deep learning methods. Local context is introduced with auto-regression and covariate modules, which can be configured as classical linear regression or as Neural Networks. Otherwise, NeuralProphet retains the design philosophy of Prophet and provides the same basic model components.

two classes of models exist :

statistical algorithms (ARIMA, GARCH …) which are mathematically explainable knowing the theory

Neural network models, which are eminently more convoluted but have demonstrated their performance


In short, NeuralProphet = Neural Networks + Prophet

The intention was to combine the two previous classes by including neural networks in the Prophet (a statistical algorithm). The purpose: gain in efficiency while limiting the loss of interpretability.

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

'n_forecasts': is the size of the forecast horizon. The default value of 1 means that the model forecasts one step into the future.

'n_lags': defines whether the AR_net is enabled or not, its value should be higher than the n_forecasts, since it is preferable for the FFNNs to encounter at least n_forecasts length of the past in order to predict n_forecasts into the fiture.

'learning_rate': if it s not specified, a learning rate range test is conducted to determine the optimal learning rate.

If not specified 'epochs' and 'loss_func' are automatically set based on the dataset size.

Two different 'optimizer': 'AdamW' and 'SDG' 

'ar_layers': defines the number of hidden layers and their sizes for the AR_net in the overall model. it is an array where each element is the size of the corresponding hidden layer.

'lagged_reg_layers': defines the number of hidden layers and their sizes for the lagged regressors FFNN in the overall model. it is an array where each element is the size of the corresponding hidden layer.

'normalize_y': is about scaling the time series before modelling. By default, NeuralProphet performs a (soft) min-max normalization of the time series. Normalization can help the model training process if the series values fluctuate heavily. However, if the series does not such scaling, users can turn this off or select another normalization.

'n_changepoints': which sets the number of points where the trend rate may change. Additionally, the trend rate changes can be regularized by setting 'trend_reg' to a value greater than zero.

'changepoints_range': controls the range of training data used to fit the trend. The default value of 0.8 means that no changepoints are set in the last 20 percent of training data.

'yearly_seasonality', 'weekly_seasonality' and 'daily_seasonality' are about which seasonal components to be modelled. For example, if you use temperature data, you can probably select daily and yearly.

NeuralProphet also contains a number of regularization parameters to control the model coefficients and introduce sparsity into the model. This also helps avoid overfitting of the model to the training data. For 'seasonality_reg', small values in the range 0.1-1 allow to fit large seasonal fluctuations whereas large values in the range 1-100 impose a heavier penalty on the Fourier coefficients and thus dampens the seasonality. For ar_sparsity values in the range 0-1 are expected with 0 inducing complete sparsity and 1 imposing no regularization at all. 'ar_sparsity' along with 'n_lags' can be used for data exploration and feature selection. You can use a larger number of lags thanks to the scalability of AR-Net and use the scarcity to identify important influence of past time steps on the prediction accuracy. 

For 'future_regressor_regularization', 'event_regularization' and 'country_holiday_regularization', values can be set in between 0-1 in the same notion as in 'ar_sparsity'. You can set different regularization parameters for the individual regressors and events depending on which ones need to be more dampened.


