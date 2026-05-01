BCG X Data Science Job Simulation: PowerCo Customer Churn Analysis

Project Overview

This project is part of the BCG X Data Science & Advanced Analytics Virtual Experience. The goal was to help PowerCo, a major energy utility provider, predict customer churn. The project focused on testing the "Price Sensitivity" hypothesis—determining if price fluctuations drive customers to switch providers—and building a predictive model to identify high-risk accounts.

Tech Stack & Tools

Language: Python
Libraries: Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
Model: Random Forest Classifier
Approach: Hypothesis Testing, EDA, Feature Engineering, and Predictive Modeling.

Project Workflow

1. Business Understanding & Hypothesis Testing
Formulated the "Price Sensitivity" hypothesis.
Identified essential data points (client information, historical pricing, and consumption patterns) needed to investigate churn drivers.

3. Exploratory Data Analysis (EDA)
Analyzed a 10% churn rate within the customer base.
Discovered that while price sensitivity is a factor, it is not the sole driver; customer tenure and consumption patterns are also highly significant.
<img width="1343" height="749" alt="Screenshot (69)" src="https://github.com/user-attachments/assets/dc14e439-d181-4975-ae52-44dde52f7734" />

4. Feature Engineering
Engineered new features to capture price volatility, specifically the difference between off-peak, peak, and mid-peak prices over time.
Calculated average price changes over 6 months and handled skewed consumption data using log transformations.
# Applying Log1p transformation to handle highly skewed consumption data
# This ensures extreme outliers don't bias the model
skewed_cols = ['cons_12m', 'cons_gas_12m', 'cons_last_month']
for col in skewed_cols:
    df[col] = np.log1p(df[col])

6. Modeling & Evaluation
Trained a Random Forest Classifier to predict churn probability.
Achieved a 50% Recall rate, which is critical for the business to identify as many potential churners as possible to minimize revenue loss.
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

# Training the Random Forest Classifier
model = RandomForestClassifier(n_estimators=1000, random_state=42)
model.fit(X_train, y_train)

# Evaluation focusing on Recall for Churners (Class 1)
predictions = model.predict(X_test)
print(classification_report(y_test, predictions))

<img width="1354" height="732" alt="Screenshot (71)" src="https://github.com/user-attachments/assets/fbe0bc2f-df58-41f9-95cd-fee0871cd6e2" />
<img width="1335" height="720" alt="Screenshot (70)" src="https://github.com/user-attachments/assets/91db93ef-fe17-4f14-9538-7aeac63a75ab" />


Challenges & Solutions

Class Imbalance: Churners made up only ~10% of the data. To address this, I focused on Recall and F1-Score rather than simple Accuracy, ensuring the model actually identifies customers likely to leave.

Data Integration: Merging historical price data with client consumption data required careful alignment. I used specific time-based joins to ensure the price features correctly reflected the period before a customer churned.

Feature Complexity: Many consumption features were highly skewed. I applied Log Transformations to normalize these distributions, which improved the stability of the Random Forest model.  

Key Insights & Recommendations

Key Driver: "Net Margin" and "Consumption" emerged as the most important features in predicting churn.
Price Sensitivity: Customers experiencing high price volatility in the last 3-6 months are at a higher risk of churning.

Strategic Action: Recommended a Targeted 20% Discount Strategy for high-risk customers identified by the model. This proactive retention approach is more cost-effective than acquiring new customers.

Strategic Recommendation: Identifying high-risk customers for a 20% discount
# Probability > 0.5 indicates a high risk of churning
probabilities = rf_model.predict_proba(X_test)[:, 1]
high_risk_customers = X_test[probabilities > 0.5]
print(f"Total High-Risk Customers Identified: {len(high_risk_customers)}")


Conclusion
  
This simulation provided hands-on experience in translating a complex business problem into a data science solution, covering the entire pipeline from hypothesis generation to executive communication.
