# 📊 Customer Churn Prediction - AlphaCom

## 🎯 Business Problem
AlphaCom, a leading telecommunications provider, is experiencing a concerning **28.2% customer churn rate**, meaning approximately 3,400 customers leave each billing cycle. This represents an annual revenue loss of approximately **$2.9 million**.

## 🔍 The Solution
A **Gradient Boosting** machine learning model was developed to predict customer churn with **83.6% ROC-AUC** on unseen data. The model identifies **67% of customers likely to churn** (458 of 681 churners) while maintaining **60% precision**.

## 📈 Key Churn Drivers Identified

| Rank | Feature | Insight |
|------|---------|---------|
| 1 | Electronic Check Payment | 49.1% churn rate - highest risk |
| 2 | Short Tenure | 46% of churn occurs in first 12 months |
| 3 | Month-to-Month Contracts | 46% churn rate |
| 4 | Fiber Optic Service | 44.9% churn rate |
| 5 | Missing Value-Added Services | Higher churn without OnlineSecurity/TechSupport |

## 📊 Business Impact

| Metric | Value |
|--------|-------|
| Annual revenue protected | Up to $619,611 |
| ROI on retention campaigns | 634% |
| Customers retained per cycle | ~723 |
| Churn rate reduction achievable | 5 percentage points (28.2% → 23.2%) |

## 📋 Top 5 Recommendations

1. **Convert Electronic Check users** to automatic payment methods with $5/month discount
2. **Implement 90-day onboarding program** for new customers with 5 engagement touchpoints
3. **Bundle OnlineSecurity and TechSupport** with new plans (3-month free trial)
4. **Offer contract upgrade incentives** (one month free for 12-month commitment)
5. **Investigate fiber optic service quality** through customer satisfaction surveys

## 🛠️ Methodology

### Data Overview
- **Records:** 12,051 customers
- **Features:** 35 (after one-hot encoding)
- **Target:** Churn (Yes/No)
- **Churn Rate:** 28.2%

### Pipeline
1. **Data Preprocessing**
   - Handled missing values (604 records in tenure)
   - Removed currency symbols from charges
   - Standardized inconsistent categories
   - Outlier capping using IQR method

2. **Feature Engineering**
   - TenureGroup (customer lifecycle stages)
   - ChargePerMonth (average customer spending)

3. **Class Imbalance Handling**
   - SMOTE applied to training data only

4. **Feature Scaling**
   - StandardScaler (fit on training, transform on test)

5. **Model Training & Evaluation**
   - 8 models evaluated: Logistic Regression, Decision Tree, Bagging, Random Forest, AdaBoost, Gradient Boosting, XGBoost
   - Hyperparameter tuning with RandomizedSearchCV (5-fold CV)
   - Primary metric: ROC-AUC

### Model Performance Comparison

| Model | ROC-AUC | Precision | Recall | F1 Score |
|-------|---------|-----------|--------|----------|
| **Gradient Boosting** | **0.8358** | 0.5971 | 0.6725 | 0.6326 |
| Random Forest (Tuned) | 0.8336 | 0.6085 | 0.6344 | 0.6211 |
| XGBoost (Tuned) | 0.8247 | 0.6158 | 0.6167 | 0.6163 |
| AdaBoost | 0.8255 | 0.5708 | 0.7019 | 0.6340 |
| Logistic Regression | 0.8225 | 0.5827 | 0.6725 | 0.6244 |

## 📁 Repository Structure
