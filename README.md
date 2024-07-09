# Covid-19 Vaccination Projecting Project

## 1- Business Goals Overview
By analyzing the relationship and the trend between the **Covid-19 pandemic** and **vaccination rates** and projecting vaccination rates in the United States **over the next 50 days**, Public health officials can use the projections to develop or adjust vaccination policies and strategies, ensuring that resources are allocated efficiently and effectively. **Projections and scenario planning(best-case, worst-case)** can help prepare for **potential future waves of the pandemic** by ensuring that a significant portion of the population is vaccinated in time.

## 2- Technical Highlights
This project extensively leveraged the powerful capabilities of **Python** to conduct a comprehensive range of tasks including meticulous data cleaning, sophisticated preprocessing techniques, intricate modeling, and creating detailed, insightful visualizations achieved by using **Pandas, Numpy, Scikit-learn, Matplotlib, and Seaborn** to handle and interpret the dataset effectively. For the model selection part, I chose auto **ARIMA Model(Auto-Regressive Integrated Moving Average)** to perform highly effectively for **time series analysis and forecasting**.

## 3- Statistical Analysis
1. **Shapiro Wilk Test:** It measures how well the data fits a normal distribution. A value close to 1 indicates that the data will likely be normally distributed.
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/shapiro.png">

-   **W-statistic (0.20982051):**  far from 1, indicating a poor fit to the normal distribution.

-   **p-value (0.0):** This is the probability of obtaining the observed test results under the null hypothesis (that the data is normally distributed). A small **p-value (≤ 0.05)** indicates strong evidence against the null hypothesis.

2. **KS test:** 
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/KS.png">

- Because the Shapiro-Wilk test is more accurate for smaller sample sizes, I used another normality test like the **Kolmogorov-Smirnov test** to confirm the results.
  
- P value ≤ confidential level, we have to reject the null, so I confirmed that Both cases are not normalized.

- The distribution for 'total vaccinations' and 'people fully vaccinated' might be right-skewed because as vaccines become more widespread, more people accept and get vaccinated.

3. **Augmented Dickey-Fuller (ADF) test and autocorrelation:**
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/us%20adf%20code.png">
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/us%20adf.png">

***Purpose:***
  - The Augmented Dickey-Fuller (ADF) test is a common statistical test used to determine if a time series is stationary.
  - A stationary time series has a consistent mean and variance over time, making it easier to predict future values accurately.
  - In stationary time series, the autocorrelations between observations depend only on the lag between them and not on when they occur. This simplifies the modeling process and helps in making robust predictions.
    
- ***Original Series:***
  - The time series exhibits a clear upward trend, indicating non-stationary.
  - The ACF plot shows high autocorrelation at multiple lags, confirming the original series's non-stationary nature.
    
- ***1st Order Differencing:***
  - The trend is significantly reduced, and the series appears to fluctuate around a constant mean, indicating that some degree of stationarity has been achieved.
  - The ACF plot shows a significant drop in autocorrelation at lag 1, but there are still notable autocorrelations at higher lags. This suggests that while the first differencing has addressed some non-stationarity, the series might still have some autocorrelation structure.

- ***2nd Order Differencing:***
  - The second differenced series appears more stationary with smaller fluctuations around the mean.
  - The ACF plot shows a further reduction in autocorrelation. Although there are still some significant spikes, they are less pronounced compared to the 1st order differencing. This indicates that the second differencing has further reduced any remaining non-stationarity.
    
- ***3rd Order Differencing:***
  - The third differenced series shows a slight improvement in stationarity, with fluctuations that appear more random around the mean.
  - The ACF plot shows minimal significant autocorrelations, suggesting that the series is now quite stationary. The spikes are much less pronounced, indicating that most of the autocorrelation has been removed.
   
## 4- Model Selection(ARIMA Model)
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/autoarima%20us.png">
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/us%20model%20result.png">



### 5- Model forecast
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/us%20forecast.png">
<img width="1000" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/base%20case.png">
<img width="1000" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/best%20case.png">

- Best-Case Scenario: shows that we forecast that the number of people vaccinated (left-side column)in the next 50 days is increased from the first day (282622 people get vaccinated) to the final day (2318170 people get vaccinated in these 50 days. JUST IN THESE 50 DAYS), in other words, the from now on to the next 50 days, there will 20822310 people get vaccinated 
This best-case scenario data frame (right-side column) shows that the predicted total number of people who get vaccinated from the very beginning until the next 50 days is 248802500 for the whole period from the beginning to the next 50 days. 
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/worst%20case.png">


