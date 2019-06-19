# Predictive modeling using linear regression and ARIMA
The project used NYSE stock index of Gold price (2000-2019) to create a predictive model to forecast future price. 
In the 1st pahse project used a simple auto correlation and partial auto correlation to forecast future price.
In the 2nd phase project used linear regression and ARIMA using grid search technique. Different features.
Data is measured in USD and are linked to Close price index. Therefore related to inflation. Much of the trend is merely due to inflation. Therefore, series has been defalated to de-trend the data. Eliminated seasonal patterns by substracting periodical values. Data here is daily scale and converted to monthly scale for computational ease. Therefore convetrted to 12-month seasonal and used 12-lag difference to get a flatter series. Also used logging to linearise with an exponential trend. 
The unpredictable appmplitude of seasonal variations suggests multiplicative pattern.
Gold price = trend* seasonal*residual(multiplicative)
