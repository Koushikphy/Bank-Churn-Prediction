# Bank Churn Prediction

### **Binary Classification with a Bank Churn Dataset**

Kaggle Competetion: [Binary Classification with a Bank Churn Dataset](https://www.kaggle.com/competitions/playground-series-s4e1)

This project aims to build a binary classification model to predict whether a bank customer is likely to **churn (exit)** or **stay**, based on a variety of personal and financial features. 
The pipeline includes preprocessing, model benchmarking, imbalance handling with SMOTE, and feature importance analysis.
The modeling process uses structured data and evaluates performance using **ROC-AUC**. 

---

### ✅ **Key Highlights & Methodology**

* **📌 Objective:**
  Predict whether a customer will **exit (churn)** their bank account using tabular customer data.

* **📊 Dataset:**

  * Source: Kaggle Playground Series (Season 4, Episode 1).
  * Size: \~165K rows in training, \~110K in testing.
  * Features include demographics, credit score, product usage, and financial metrics.
  * Target variable: `Exited` (0 = stayed, 1 = churned).
  * Class imbalance: Only \~21% churned customers.

* **🛠️ Data Preprocessing:**

  * Dropped irrelevant features.
  * Identified and encoded categorical features using one-hot encoding.
  * Scaled numerical features for better normalization.

* **🔍 EDA Insights:**

  * Churners were the minority class (imbalanced data).
  * Churn tendency varied with age, account balance, tenure, and geography.
  * Imbalanced class distribution warranted careful handling during modeling.

* **🧠 Modeling Approach:**

  * Evaluated four models:
    ✅ `DecisionTreeClassifier`  
    ✅ `RandomForestClassifier`  
    ✅ `XGBClassifier`  
    ✅ `LGBMClassifier`  

  * Best performance (before handling imbalance) from **LGBMClassifier** with \~86.7% accuracy and **ROC-AUC = 0.889**.

* **📐 Imbalance Handling:**

  * Applied **SMOTE** to synthetically oversample the minority class.
  * Rebuilt the pipeline using `imblearn.pipeline` to include SMOTE.
  * Post-SMOTE model had **slightly improved recall for churners**, though accuracy dropped slightly (\~86.3% and ROC-AUC = 0.888).

* **🎯 Evaluation:**

  * Used **Confusion Matrix**, **Classification Report**, and **ROC Curve** for evaluation.
  * Observed improvement in **recall for class `Exited = 1`** after balancing.

* **🧪 Feature Importance (LGBM):**

  * Top predictive features included:

    * Age
    * Number of Products
    * Balance
    * Estimated Salary
    * Geography (encoded)
