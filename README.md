# Bank-Churn-ML

## Overview  
This project focuses on **predicting customer churn** and **segmenting customers** using machine learning. The goal is to identify **which customers are likely to leave** and understand **customer behavior** to improve retention strategies.  

The project is structured into three key steps:  
1. **EDA, Data Cleaning & Feature Engineering**  
2. **Classification - Churn Prediction**  
3. **Segmentation - Customer Clustering**  

---

## Dataset  
The dataset consists of **10,000 bank customers**, with information on **credit scores, account balances, estimated salaries, number of products, geography, and customer activity status**. The target variable is **Exited**, where:  
- `Exited = 1` means the customer has churned.  
- `Exited = 0` means the customer has remained with the bank.  

---

## Step 1: EDA, Data Cleaning & Feature Engineering  

I started by **importing and merging** the customer and account information datasets using `CustomerID` as the common key.  

### **Data Preparation**  
- Removed **duplicate records and inconsistent labels**.  
- Converted **currency fields** to numeric values by stripping symbols.  
- Handled **missing values** by replacing categorical missing data with `"MISSING"` and filling numerical missing values with the **median**.  
- Standardized **geographical values** (e.g., `"FRA", "France", "French"` → `"France"`).  
- Identified **incorrect salary values** (e.g., `-999999` was replaced with the median).  

### **Feature Engineering**  
To improve the model’s predictive power, I created two new features:  
- **Balance-to-Income Ratio:** `Balance_v_income = Balance / EstimatedSalary`  
- **Income per Product:** `income_v_product = EstimatedSalary / NumOfProducts`  

### **Exploratory Data Analysis (EDA)**  
To understand customer churn behavior, I visualized relationships between variables:  
- **Churn rates across geography and gender** using bar plots.  
- **Numerical features vs. churn** using box plots and histograms.  

### **Key Insights**  
- **German customers** have nearly **twice the churn rate** compared to French and Spanish customers.  
- **Inactive members and those without credit cards** are more likely to churn.  
- Customers with a **higher balance-to-income ratio** tend to have a higher churn rate.  

---

## Step 2: Classification - Predicting Customer Churn  

With the data cleaned and new features added, I built **machine learning models** to predict whether a customer would churn.  

### **Data Preparation for Modeling**  
- Converted categorical variables into **dummy variables**.  
- Split the data into **training and test sets** (80% training, 20% testing).  

### **Model Training & Evaluation**  
I trained and evaluated two models:  
1. **Logistic Regression**  
2. **Random Forest Classifier**  

Performance was assessed using:  
- **Accuracy, Precision, Recall, F1-score, and ROC-AUC**  
- **Confusion matrices** to compare predicted vs. actual churn  
- **Precision-recall curves** to adjust model thresholds  

### **Results**  
- **Logistic Regression achieved an AUC of 0.77**, providing a simple and interpretable model.  
- **Random Forest performed better with an AUC of 0.85**, but showed slight overfitting.  

To reduce overfitting, I fine-tuned **Random Forest** using `RandomizedSearchCV` and `GridSearchCV` to optimize hyperparameters.  

### **Feature Importance**  
The most influential features in predicting churn were:  
- **Age** (strongest predictor)  
- **Number of Products, Balance, and Credit Score**  

---

## Step 3: Segmentation - Clustering Customers  

Beyond churn prediction, I wanted to understand **different types of customers** by applying **unsupervised learning**.  

### **Clustering with K-Means**  
- Standardized numerical features for better clustering.  
- Used the **elbow method** to determine the optimal number of clusters.  
- Analyzed the characteristics of each cluster.  

### **Findings**  
- **Cluster 1:** **High-churn risk, low income** → Customers in this group may need personalized offers.  
- **Cluster 2:** **Financially stable, high balance** → Upselling premium financial products could be effective.  
- **Cluster 3:** **Young and active customers** → Engaging these customers early could improve retention.  

---

## How to Run  

To replicate this analysis, follow these steps:  

1. Clone the repository:  
   ```bash
   git clone https://github.com/yourusername/Bank-Churn-ML.git
   cd Bank-Churn-ML
