# -Bank-Churn-ML
  

## 📌 Overview  
This project analyzes **bank customer churn** using **machine learning models** and explores customer segmentation using clustering techniques. The goal is to **predict which customers are likely to leave** and identify actionable **customer segments** for better retention strategies.

## 📊 Dataset  
- **Source:** European bank dataset with 10,000 customers.  
- **Features:** Credit score, balance, salary, number of products, geography, etc.  
- **Target Variable:** `Exited` (1 = churned, 0 = stayed)  

## 🚀 Project Workflow  
1️⃣ **Exploratory Data Analysis (EDA)**  
   - Cleaned missing values, removed duplicates, and handled categorical data.  
   - Visualized churn patterns across different features.  

2️⃣ **Feature Engineering & Data Prep**  
   - Created **new features** (`balance_v_income`, `income_v_products`).  
   - Converted categorical variables to **dummy variables**.  
   - Split data into **train-test sets** (80-20).  

3️⃣ **Supervised Learning - Classification (Churn Prediction)**  
   - Trained **Logistic Regression** & **Random Forest** models.  
   - Evaluated using **accuracy, precision, recall, F1-score, ROC-AUC**.  
   - Hyperparameter tuning with **GridSearchCV**.  

4️⃣ **Unsupervised Learning - Customer Segmentation**  
   - Applied **K-Means Clustering** to group similar customers.  
   - Visualized clusters with heatmaps & demographic analysis.  
