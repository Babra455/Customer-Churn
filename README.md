         Customer Churn Analysis & Prediction using Machine Learning

Executive Summary  
This project explores and models customer churn using data from a fictional business. The objective is to analyze user behavior, identify patterns that contribute to churn, and develop a predictive model to help the business proactively retain at-risk customers. The process involved loading and merging multiple datasets, performing descriptive and visual analysis, feature engineering, correlation analysis, and finally building a logistic regression model using Scikit-learn.

Business Problem  
Churn directly affects business profitability. Retaining customers is significantly more cost-effective than acquiring new ones. However, without insight into churn behavior, businesses struggle to act in time. The goal of this project is to identify factors that contribute to churn and develop a model to predict it accurately so the business can intervene early.

  Methodology

 I began by loading data from five different sheets and merged them using `CustomerID` to form a complete dataset. I then conducted descriptive analysis to understand the central tendencies and spread of the data by checking the mean, min, max, standard deviation, and count. I checked for missing values and ensured any inconsistencies were addressed. For feature engineering, I created age bins to categorize customers into groups and visualized the age distribution using a pie chart. I proceeded to integrate the churn status with demographic data by merging on `CustomerID`. Afterward, I removed irrelevant columns such as `CustomerID`, `TransactionID`, `InteractionID`, `TransactionDate`, `ProductCategory`, `LastLoginDate`, and `InteractionDate` to reduce noise. I analyzed feature correlation and noted weak relationships between `LoginFrequency` and churn. For modeling, I dropped `ChurnStatus` from the feature set, applied one-hot encoding to categorical variables, and split the dataset into training and testing sets. I used SMOTE to balance the training data, then trained a logistic regression model and made predictions on the test set. I calculated evaluation metrics including accuracy, precision, recall, F1-score, and AUC-ROC. Lastly, I computed prediction probabilities, false positive rate, true positive rate, and plotted the ROC curve to assess model performance.


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
- Model Evaluation (Accuracy, Precision, Recall, F1, AUC-ROC)  
- Python Libraries: Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn, Imbalanced-learn

 Results, Recommendations & Next Steps

The logistic regression model trained on the customer dataset achieved an accuracy of 79% and an AUC-ROC score of 0.61. However, precision, recall, and F1-score were all recorded at 0.00, indicating the model struggled to correctly identify customers likely to churn. This performance gap suggests that the model is biased toward the majority class (non-churners), likely due to class imbalance and limited predictive power of the current features. Correlation analysis supported this, revealing only a very weak negative relationship between login frequency and churn, and virtually no correlation between amount spent and churn status. 
This implies that customers may churn regardless of how much they spend, but lower engagement (fewer logins) may slightly increase churn risk.
Based on these findings, it is recommended that the business focus on improving customer engagement, particularly targeting users with low login frequency. Campaigns encouraging regular platform use, reminders, or personalized offers may help retain these users. Moreover, enhancing the dataset with more behavior-related features—such as customer satisfaction scores, resolution times for service issues, or complaint history—could improve model performance. For modeling, trying advanced algorithms like Random Forest or XGBoost, along with hyperparameter tuning, may yield better predictive power, especially for detecting minority churn cases.

Next Steps

Looking forward, next steps include expanding the feature set to capture more customer behavior and interaction nuances, tuning models for improved performance, and deploying results through an interactive dashboard (e.g., using Streamlit or Power BI). Additionally, incorporating time-based trends can help forecast future churn, enabling the business to take proactive retention measures.

