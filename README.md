# Weather prediction
### Introduction
Predicting temperature is a critical task with wide-ranging applications across various sectors, including agriculture, energy, healthcare, and disaster management. As climate patterns become increasingly unpredictable due to global warming and other environmental factors, accurate temperature forecasting has become more important than ever. This project aims to develop a robust and reliable temperature prediction model using advanced machine learning techniques.

### Data
Data come from https://www.kaggle.com/datasets/muthuj7/weather-dataset/data
Variables:
- temperature
- apparent temperature
- summary (e.g. Partly Cloudy, Mostly Cloudy)
- precip type
- humidity
- wind speed
- wind bearing
- visibility

NaNs in `precip type` were filled using fill forward method.

### Temporal Fusion Transformer
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/439af8c2-5a1b-4b3e-8488-0b6543073935)
To tackle the problem of temperature prediction I chose Temporal Fusion Transformer architecture (https://arxiv.org/pdf/1912.09363) and implemented it using PyTorch Forecasting.

### Results
##### MAE
The model achieved MAE of 2.2.
##### Observed vs predicted
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/1d504412-caf3-47fc-8d00-8e6a9055cbbc)
##### Observed vs predicted by variable
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/b9cfe677-aa99-429b-997c-154a051e7923)
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/dbdfa3a5-36f0-4123-8fca-8871877b7041)
Model shows worse performance for higher temperatures
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/ddcfec05-98c6-4c26-910f-700d78580747)
Higher humidity corresponds to higher temperatures, model performs worse for (normalized) humidity in the range of 0.6-0.85
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/48b3fa68-cbed-46e0-86d4-6441c7e48b8d)
Counterintuitively, the higher the wind speed, the higher the temperature, but it might be caused by low sample size, also the model performs weaker for higher values of wind speed.
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/60f3bbfd-0e43-448d-99a4-61d90ca17d53)
The higher the visibility, the higher temperature, model performs well on the whole scope of visibility.
##### Attention
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/249e77d7-3b4e-46c0-b026-1475ab8e9427)
48-72 hours prior to prediction seem to be the most important with a spike just before the prediction.
##### Variable importance
![image](https://github.com/pawelwozniak14/WeatherPrediction/assets/73362296/ef2b9be1-176e-4f53-8240-98c87c5f1bc5)











