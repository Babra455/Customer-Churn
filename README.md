         Customer Churn Analysis & Prediction using Machine Learning

Executive Summary  
This project explores and models customer churn using data from a fictional business. The objective is to analyze user behavior, identify patterns that contribute to churn, and develop a predictive model to help the business proactively retain at-risk customers. The process involved loading and merging multiple datasets, performing descriptive and visual analysis, feature engineering, correlation analysis, and finally building a logistic regression model using Scikit-learn.

Business Problem  
Churn directly affects business profitability. Retaining customers is significantly more cost-effective than acquiring new ones. However, without insight into churn behavior, businesses struggle to act in time. The goal of this project is to identify factors that contribute to churn and develop a model to predict it accurately so the business can intervene early.

  Methodology

 I began by loading data from five different sheets and merged them using `CustomerID` to form a complete dataset. I then conducted descriptive analysis to understand the central tendencies and spread of the data by checking the mean, min, max, standard deviation, and count. I checked for missing values and ensured any inconsistencies were addressed. For feature engineering, I created age bins to categorize customers into groups and visualized the age distribution using a pie chart. I proceeded to integrate the churn status with demographic data by merging on `CustomerID`. Afterward, I removed irrelevant columns such as `CustomerID`, `TransactionID`, `InteractionID`, `TransactionDate`, `ProductCategory`, `LastLoginDate`, and `InteractionDate` to reduce noise. I analyzed feature correlation and noted weak relationships between `LoginFrequency` and churn. For modeling, I dropped `ChurnStatus` from the feature set, applied one-hot encoding to categorical variables, and split the dataset into training and testing sets.

 Correlation Analysis

To better understand the relationships between numerical variables, I performed a correlation analysis using Pearson’s correlation coefficient. This helped identify how strongly different features were related to each other and to the target variable (ChurnStatus). The correlation matrix showed the following key relationships:
- AmountSpent & ChurnStatus: Correlation = -0.0002  
  This indicates virtually no relationship between how much a customer spent and whether they churned. Spending behavior alone doesn't seem to influence churn.
- LoginFrequency & ChurnStatus: Correlation = -0.0966  
  This shows a very weak negative correlation, suggesting that customers who logged in less frequently were slightly more likely to churn, but the relationship is still weak.
- AmountSpent & LoginFrequency: Correlation = 0.0346  
  This weak positive correlation implies a very slight tendency for users who spend more to also log in more often, but it’s not significant.
 None of the numeric features showed strong correlation with churn. This suggests that other features (possibly categorical or engineered ones) or interactions between variables might be more predictive, and reinforces the need for machine learning models to capture complex patterns beyond simple linear relationships.

 Skills Demonstrated

- Data Cleaning & Preprocessing  
- Feature Engineering (Age Bins, One-hot Encoding)  
- Exploratory Data Analysis (EDA)  
- Correlation Analysis  
- Model Building (Logistic Regression using Scikit-learn)  
- Model Evaluation ( AUC-ROC)  
- Python Libraries: Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn

 Results, Recommendations & Next Steps

After applying a Random Forest Classifier to the customer churn dataset, only the categorical columns were encoded, and datetime-related columns were dropped during preprocessing. The model was then trained and evaluated using the AUC-ROC metric, which achieved an impressive score of 0.9979.

This exceptionally high AUC-ROC value indicates that the model has an excellent ability to distinguish between churners and non-churners, showing strong predictive performance. The ROC curve, plotted using the false positive rate (FPR) and true positive rate (TPR) derived from the model’s prediction probabilities, further confirmed its robust discriminative power.

Overall, the results demonstrate that even with minimal preprocessing—limited to encoding categorical features and removing date columns—the Random Forest Classifier performed remarkably well in identifying churn patterns within the dataset.


Correlation analysis also revealed minimal predictive relationships:  
- Amount Spent showed virtually no correlation with churn.
- Login Frequency had a very weak negative correlation with churn (-0.096), suggesting that customers who log in less often might be at slightly higher risk of churning.

Recommendations:  
- Improve engagement: Encourage users with low login activity through targeted campaigns, nudges, or loyalty rewards.
- Feature expansion: Include richer behavioral or satisfaction-related data (e.g., complaints, service quality ratings, resolution speed).
- Model improvement: Try ensemble models like Random Forest or XGBoost, and apply hyperparameter tuning to boost performance.

