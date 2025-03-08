# Bank-Churn-ML

## Overview  
This project focuses on predicting **bank customer churn** and segmenting customers based on their financial behavior. The goal is to build a classification model to identify customers likely to leave and use clustering techniques to group customers for targeted strategies.

The project is structured in three steps:  
1. **EDA, Data Cleaning & Feature Engineering**  
2. **Classification - Churn Prediction**  
3. **Segmentation - Customer Clustering**  

---

## Dataset  
The dataset contains account information for **10,000 customers** at a European bank. The key features include **credit score, balance, estimated salary, number of products, geography, and customer activity status**. The target variable is **Exited**, where 1 indicates a customer has churned and 0 means they have stayed.

---

## Step 1: EDA, Data Cleaning & Feature Engineering  

The first step involves **importing and preparing the data**. Two datasets (Customer Info and Account Info) are merged using the `CustomerID` column.  

### **Tasks:**  
- Remove **duplicates and inconsistent labels**.  
- Convert currency fields to **numeric format**.  
- Handle **missing values** in categorical and numeric columns.  
- Create new features:  
  - `balance_v_income = Balance / EstimatedSalary`  
  - `income_v_product = EstimatedSalary / NumOfProducts`  
- Explore churn behavior across different categories using bar plots and box plots.  

### **Observations:**  
- **German customers** have a significantly higher churn rate than French and Spanish customers.  
- **Inactive members** and those without credit cards are more likely to churn.  
- Customers with a **higher balance-to-income ratio** show an increased churn tendency.  

---

## Step 2: Classification - Predicting Customer Churn  

After preparing the data, we train **supervised machine learning models** to predict customer churn.  

### **Tasks:**  
- Convert categorical variables to **dummy variables**.  
- Split data into **training and testing sets (80-20)**.  
- Train models:  
  - **Logistic Regression**  
  - **Random Forest**  
- Evaluate model performance using **accuracy, precision, recall, F1-score, and ROC-AUC**.  
- Fine-tune **Random Forest** using **RandomizedSearchCV** and **GridSearchCV**.  

### **Results:**  
- **Logistic Regression** achieved an AUC of **0.77**, providing a simple and interpretable model.  
- **Random Forest** improved performance with an **AUC of 0.85**, although it showed slight overfitting.  

### **Feature Importance:**  
Feature importance from the **Random Forest model** revealed that:  
- **Age** is the strongest predictor of churn.  
- **Number of Products, Balance, and Credit Score** also play key roles.  

---

## Step 3: Segmentation - Clustering Customers  

To better understand customer groups, we apply **unsupervised learning** using **K-Means Clustering**.  

### **Tasks:**  
- Standardize numerical features for clustering.  
- Determine the optimal number of clusters using the **elbow method**.  
- Assign customers to clusters and analyze **demographic and financial behavior**.  

### **Findings:**  
- Cluster 1: **High-churn risk, low income** → Needs personalized retention strategies.  
- Cluster 2: **Financially stable, high balance** → Potential for premium financial products.  
- Cluster 3: **Young and active customers** → Focus on long-term engagement strategies.  

---

## How to Run  

1. Clone the repository:  
   ```bash
   git clone https://github.com/yourusername/Bank-Churn-ML.git
   cd Bank-Churn-ML
