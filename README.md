# Predictive modeling using Regression Techniques and ARIMA

The project used NYSE stock index of Gold price (2000-2019) to create a predictive model to forecast future price. 

In the 1st pahse project used a simple auto correlation and partial auto correlation to forecast future price.
In the 2nd phase project used linear regression and ARIMA using grid search technique. Different features.

Data is measured in USD and are linked to Close price index. Therefore related to inflation. Much of the trend is merely due to inflation. Therefore, series has been defalated to de-trend the data. Eliminated seasonal patterns by substracting periodical values. Data here is daily scale and converted to monthly scale for computational ease. Therefore convetrted to 12-month seasonal and used 12-lag difference to get a flatter series. Also used logging to linearise with an exponential trend. 

# Linear regression

In linear regression vilatility has been taken care with added features:

f01 = (High - Low)/(Low)*100

f02 = (Close - Open)/(Open)*100

f03 = (Close) / (Open)-1

Moreover, moving averages of long and short window was taken:

s01 = Close.rolling(window=30)

s02 = Close.rolling(window=100)

# ARIMA

Performed logarithm transofrmation to stabilise (heteroscedasticity) the series.
Logarithm transformation equals the sum of the logarithms, i.e., LOG(XY) = LOG(X) + LOG(Y). This converts multiplicative to additive and random walk to geometric random walk i.e.exponential trends to linear trends. This also helps starightening out exponential growth patterns to fit into a linear model. Logging helps to incorporate an explicit forecast of future inflation into the model.

That's typically a series of daily returns where each return is expressed in continually compounded terms. For each day, we take the natural log of the ratio of stock prices (i.e., price today divided by price yesterday, and so on). This series of daily returns where each return is expressed in continually compounded terms. For each day, a natural log was taken of the ratio of stock prices (i.e., price today divided by price yesterday, and so on).

Rt = ln(St/St-1), Rt = return of the day, St = price on day t, St-1 = price day before t.

This produces a series of daily returns, from ui to Rt-n, depending niumber of days (n = days) measuring. This is simple moving average of the squared periodic returns and each squared return is given an equal weight. 

Also performed exponentially weighted moving average (EWM). Here, instead of equal weights in moving average, each squared return is weighted by a multiplier. The weakness of simple moving average is that all returns earn the same weight. Recent return has no more influence on the variance than last month's return. Therefore in EWM more recent returns have greater weight on the variance. This ensures a variance that is weighted toward more recent data.

The unpredictable amplitude of seasonal variations suggests multiplicative pattern.

Gold price = trend* seasonal*residual(multiplicative)

# Multivariate regression

Univariate time series=

                Yt = m + ɸYt-1 + ɛ
                
•	Yt= stationary time series and a linear combination of its past values t-1, t-2….

•	m=coefficient

•	ɸ = slope coefficient

•	ɛ = error terms(white noise)

Structural model-

                Yt = β0 + β1X
                
•	Y= dependent variable

•	X = independent variable

•	β0 = intercept

•	β1 = slope coefficient

Structural model do not have time component because of auto correlation issue. With time component, the values will be correlated with time, which impacts error term. Therefore, variables here added with cross section.

# Multivariate time series which combines above-

Structural model do not have time component because of auto correlation issue. With time component, the values will be correlated with time, which impacts error term. Therefore, variables here added with cross section.

Multivariate time series which combines above-

                Yt = μ + ɸ1Yt-1 + ɸ2Xt-1 + ɛt, 
                both Yt and Xt are stationary time series
