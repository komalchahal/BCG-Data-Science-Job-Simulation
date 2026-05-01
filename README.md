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
2. Exploratory Data Analysis (EDA)
Analyzed a 10% churn rate within the customer base.
Discovered that while price sensitivity is a factor, it is not the sole driver; customer tenure and consumption patterns are also highly significant.
3. Feature Engineering
Engineered new features to capture price volatility, specifically the difference between off-peak, peak, and mid-peak prices over time.
Calculated average price changes over 6 months and handled skewed consumption data using log transformations.
4. Modeling & Evaluation
Trained a Random Forest Classifier to predict churn probability.
Achieved a 50% Recall rate, which is critical for the business to identify as many potential churners as possible to minimize revenue loss.

Challenges & Solutions
Class Imbalance: Churners made up only ~10% of the data. To address this, I focused on Recall and F1-Score rather than simple Accuracy, ensuring the model actually identifies customers likely to leave.
Data Integration: Merging historical price data with client consumption data required careful alignment. I used specific time-based joins to ensure the price features correctly reflected the period before a customer churned.
Feature Complexity: Many consumption features were highly skewed. I applied Log Transformations to normalize these distributions, which improved the stability of the Random Forest model.  

Key Insights & Recommendations

Key Driver: "Net Margin" and "Consumption" emerged as the most important features in predicting churn.
Price Sensitivity: Customers experiencing high price volatility in the last 3-6 months are at a higher risk of churning.

Strategic Action: Recommended a Targeted 20% Discount Strategy for high-risk customers identified by the model. This proactive retention approach is more cost-effective than acquiring new customers.

Conclusion
  
This simulation provided hands-on experience in translating a complex business problem into a data science solution, covering the entire pipeline from hypothesis generation to executive communication.
