# Credit Risk Prediction using Machine Learning

## Overview
Credit risk assessment is a critical task for financial institutions, as it helps determine whether a borrower is likely to default on their credit obligations. Traditional risk assessment methods often rely on manual evaluation and simple statistical models. In this project, machine learning techniques are applied to predict the probability of customer default based on their financial behavior and demographic information.

The objective of this project is to build an interpretable and effective credit risk prediction model that can assist financial institutions in identifying high-risk customers. The project follows a complete machine learning pipeline, including exploratory data analysis, feature engineering, model comparison, threshold optimization, and model interpretability using SHAP.

---

## Dataset
The dataset used in this project contains customer credit information, including demographic attributes, credit limits, billing amounts, payment amounts, and repayment history.
Dataset Link: [https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset]

Key types of features include:

- **Customer Demographics**
  - Age
  - Sex
  - Education
  - Marriage status

- **Financial Attributes**
  - Credit limit
  - Billing amounts
  - Payment amounts

- **Repayment Behavior**
  - Recent payment status

The target variable represents whether a customer **defaults on their credit payment**.

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA)
Exploratory analysis was conducted to understand the distribution of key variables and identify patterns related to credit default. Particular attention was given to repayment behavior features, which showed strong relationships with default outcomes.

### 2. Feature Engineering
Several aggregated behavioral features were created to capture repayment patterns more effectively, including:

- Average billing amount
- Maximum billing amount
- Average payment amount
- Maximum payment amount
- Average payment-to-bill ratio
- Minimum payment-to-bill ratio
- Maximum payment delay
- Average payment delay
- Recent payment status
- Number of late payments

These engineered features help the model capture long-term repayment behavior rather than relying solely on monthly observations.

### 3. Handling Class Imbalance
Since default events are relatively less frequent, the models were trained using balanced class weights to ensure that the minority class (default cases) was properly considered during training.

### 4. Model Development
Three machine learning models were evaluated:

- Logistic Regression
- Decision Tree
- Random Forest

Models were trained and evaluated using metrics such as:

- Precision
- Recall
- F1-score
- ROC-AUC

Among the tested models, **Random Forest demonstrated the best overall performance**, particularly in terms of ROC-AUC and its ability to capture non-linear relationships in the data.

### 5. Threshold Optimization
In credit risk prediction, failing to detect a defaulter (false negative) is more costly than incorrectly flagging a safe customer (false positive). Therefore, the model evaluation focuses on improving recall for the default class.

Instead of using the default classification threshold of **0.5**, threshold tuning was performed to improve the model’s ability to detect potential defaulters.

The final decision threshold was set to: **0.25**

### 6. Model Interpretability (SHAP)
To improve transparency and understand the model's decisions, SHAP (SHapley Additive exPlanations) was used to interpret the Random Forest model.

Two types of explanations were generated:

- **Global Interpretation (SHAP Summary Plot)**  
  Identifies the most important features influencing predictions across the entire dataset.

- **Local Interpretation (SHAP Waterfall Plot)**  
  Explains how individual features influence the prediction for a specific customer.

The results show that **repayment behavior variables**, such as recent payment status and payment delays, are the strongest drivers of default risk.

---

## Key Findings

- **Repayment behavior is the strongest predictor of credit default.**
- Features such as **recent payment status, maximum payment delay, and number of late payments** have the largest impact on model predictions.
- Demographic variables play a relatively minor role compared to financial behavior.
- Threshold tuning significantly improves the detection of high-risk customers.
- SHAP analysis confirms that the model learns financially meaningful patterns.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- SHAP

---

## Conclusion

This project demonstrates how machine learning can be used to support credit risk assessment by identifying customers who are more likely to default on their payments. By combining robust model evaluation, threshold optimization, and interpretable machine learning techniques, the final model not only provides strong predictive performance but also offers clear insights into the key factors driving credit risk.

Such approaches can assist financial institutions in making more informed lending decisions and managing credit risk more effectively.

---

## Author
Anthony Davidson Salim
