# Covid-19 Vaccination Projecting Project

## 1- Business Goals Overview
By analyzing the relationship and the trend between the **Covid-19 pandemic** and **vaccination rates** and projecting vaccination rates in the United States and Canada **over the next 50 days**, Public health officials can use the projections to develop or adjust vaccination policies and strategies, ensuring that resources are allocated efficiently and effectively. **Projections and scenario planning(best-case, worst-case)** can help in preparing for **potential future waves of the pandemic** by ensuring that a significant portion of the population is vaccinated in time.

## 2- Technical Highlights
This project extensively leveraged the powerful capabilities of **Python** to conduct a comprehensive range of tasks including meticulous data cleaning, sophisticated preprocessing techniques, intricate modeling, and creating detailed, insightful visualizations achieved by using **Pandas, Numpy, Scikit-learn, Matplotlib, and Seaborn** to handle and interpret the dataset effectively. In predictive modeling, I chose auto **ARIMA Model(Auto-Regressive Integrated Moving Average)** to perform highly effecitve for **time series analysis and forecasting**.

## 3- Statistical Analysis
1. **Shapiro Wilk Test:** is a statistical test used to assess the normality of a data sample. 
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/shapiro.png">
<img width="600" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/covid%20project/autoarima%20us.png">

2. **KS test:** Because Shapiro Wilk test is more accurate for smaller sample size, so I used other normality test like Kolmogorov-Smirnov test to confirm the results.
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/Multi.png">
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/Multi1.png">


When considering the factors contributing to the probability of default, DELINQ, DEBTINC, NINQ,  DEROG, and VALUE emerge as the most significant predictors. DEBTINC, or the debt-to-income ratio, underscores the importance of a customer's financial burden in evaluating credit risk. DELINQ (number of delinquent credit lines), NINQ (number of recent credit inquiries), NINQ (number of recent credit inquiries), and DEROG (number of major derogatory reports) exhibit a positive correlation with default probability. These factors are indicative of recent financial stress or mismanagement, which can signal a higher risk of default. However, the 'VALUE' of an asset has a negative correlation with default probability. This is because a higher property value can provide a financial safety net, enabling borrowers to access equity in tough times instead of defaulting. It also suggests that the borrower may have greater financial stability and more to lose by defaulting, thereby providing a strong incentive to maintain their loan payments. However, this relationship can be influenced by market conditions and the borrower's overall financial health, underscoring the importance of a multifaceted risk assessment.

## 3- Model Selection
<img width="800" alt="image" src="https://github.com/jh4581/resume-projects-portfolio.github.io/blob/main/images/Performances.png">

1. Logistic Regression has the lowest performance across all metrics compared to the other two models. It has particularly low recall and F1 scores, indicating that it may not be the best at capturing all the default cases.

2. The Decision Tree Model shows very high recall and precision. It has the highest F1 score, which is a harmonic mean of precision and recall, suggesting a good balance between the two. Additionally, its AUC is the highest, showing a strong capability in distinguishing between classes.

3. The Random Forest Model has a high precision, indicating that when it predicts a default, it is very likely to be correct. It has a slightly lower recall than the Decision Tree, suggesting it doesn't capture as many of the true default cases. However, it does have a higher accuracy and the AUC score is very close to that of the Decision Tree.

### 4- Conclusion
The choice of the final model should be guided by the specific business objectives and the costs associated with false positives (incorrectly predicting default when there is none) versus false negatives (failing to predict a default that does occur).

- If the cost of missing a default is very high (a false negative is very costly), the Decision Tree Model may be the best option due to its highest recall and F1 score.

- If the goal is to ensure that the cases identified as defaults are indeed defaults (minimizing false positives), the Random Forest model would be preferable because of its high precision.

- If overall accuracy and the balance between true positive and true negative rates are the priority, then the Random Forest model may be the most suitable as it has the highest accuracy and a very competitive AUC score.

Given the metrics, the Decision Tree Model stands out for its ability to correctly identify default cases (high recall) while maintaining high precision, and it has the highest AUC score. However, the Random Forest model, with its slightly better accuracy and competitive AUC, could be more appealing if the problem requires a more balanced overall performance.

In this instance, the Decision Tree model's superior performance metrics make it the preferred choice, provided the model's robustness has been validated through appropriate cross-validation techniques and that it has been tested on an independent validation set to confirm these results.
