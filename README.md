# 💳 Credit Card Fraud Detection

## 📌 Project Overview
This project aims to detect fraudulent credit card transactions using machine learning. Given the highly imbalanced nature of fraud datasets, where legitimate transactions overwhelmingly outnumber fraudulent ones, the primary goal is to build models that can accurately identify fraud without generating too many false positives.

## 📊 Dataset
The dataset used in this project is the widely recognized **Credit Card Fraud Detection** dataset (typically sourced from Kaggle). 
* **Size:** ~284,800 transactions, 31 features.
* **Features:** * `V1` to `V28`: Numerical features resulting from a PCA (Principal Component Analysis) transformation to protect user confidentiality.
  * `Time`: Seconds elapsed between each transaction and the first transaction in the dataset.
  * `Amount`: The transaction amount.
* **Target Variable:** `Class` (0 = Normal Transaction, 1 = Fraudulent Transaction).

*Note: Due to file size constraints, the `creditcard.csv` dataset is not included in this repository. It must be downloaded separately to run the notebook.*

## 🛠️ Project Workflow

1. **Exploratory Data Analysis (EDA):**
   * Loaded the dataset and inspected data types and structural integrity.
   * Identified and removed duplicate rows to ensure clean training data.
   * Confirmed that there were no missing/null values in the dataset.

2. **Baseline Modeling:**
   * Split the data into Training and Testing sets (80/20 split).
   * Trained a **Logistic Regression** model as an initial baseline.
   * Trained a **Random Forest Classifier** utilizing class weighting (`class_weight='balanced'`) to begin addressing the target imbalance.

3. **Evaluation Strategy:**
   * Because the dataset is heavily imbalanced, **Accuracy** is a misleading metric (predicting all transactions as "Normal" yields 99.9% accuracy). 
   * Instead, models are evaluated using the **Confusion Matrix** and **Classification Report**, with a strong emphasis on **Recall** for the Fraud class (Class 1) to minimize false negatives.

## 📈 Initial Results
* **Logistic Regression:** Achieved a baseline recall of 0.59 for fraudulent transactions. It struggled with convergence due to the unscaled `Time` and `Amount` features.
* **Random Forest Classifier:** Performed significantly better, achieving a recall of 0.71 for fraudulent transactions, proving to be a stronger baseline model for this non-linear, imbalanced problem.

## 🚀 Next Steps & Future Improvements
This repository represents the foundational stage of this project. Planned improvements include:
* **Feature Scaling:** Applying `RobustScaler` to the `Time` and `Amount` columns to improve distance-based algorithms like Logistic Regression.
* **Handling Class Imbalance:** Implementing techniques like **SMOTE** (Synthetic Minority Over-sampling Technique) to synthetically balance the training data.
* **Advanced Modeling:** Training gradient boosting models such as **XGBoost** or **LightGBM**, which are highly effective for tabular classification tasks.

## 💻 How to Run
1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/YourUsername/Credit-Card-Fraud-Detection.git](https://github.com/YourUsername/Credit-Card-Fraud-Detection.git)