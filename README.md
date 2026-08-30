# Credit Fraud Classifier 
This repository contains a Machine Learning project developed as part of the evaluation of the **IBM Machine Learning** course. The objective of the project is to develop and evaluate a model capable of classifying credit transactions and detecting possible cases of fraud. To this end, data exploration and pre-processing techniques, training of classification models and evaluation of their performance will be applied, using the knowledge and methodologies learned throughout the course.

## 01 Dataset Source & License
* **Dataset:** [Credit Card Fraud Dataset on Kaggle](https://www.kaggle.com/datasets/dhanushnarayananr/credit-card-fraud)
* **Author:** Dhanush Narayanan
* **License:** CC0 Public Domain

## 02 Why is Dataset?
This dataset was selected because it exhibits a significant class imbalance between legitimate and fraudulent transactions. This provides an ideal bench mark for testing specialized sampling techniques, cost-sensitive algorithms, and metrics beyond standard accuracy (such as Precision, Recall, F1-Score, and ROC-AUC).

## 03 Dataset Overview
* **Key statistics**
* **Total records:** 1,000,000 transactions
* **Class distribution:** 91.2% Legitimate (`0`) | 8.8% Fraudulent (`1`) 
* **Data integrity:** 0 missing or null values
*  **Data types:** Continuous and binary numerical variables (`float64`)
* **Features:**
* `distance_from_home`
* `distance_from_last_transaction`
* `ratio_to_median_purchase_price`
* `used_chip`
* `used_pin_number`
* `online_order`
  
* **Target Variable:** `fraud` (0= Legitimate, 1 = Fraudulent)
## 04 Class Distribution
 <img width="429" height="312" alt="imagen" src="https://github.com/user-attachments/assets/22fe75a1-e635-448e-9387-4b6837271dd5" />
 
## 05 Machine Learning Aproach & Metrics
* **Task Type:** Supervised binary classification on imbalance data.
* **Evaluation Metrics:** Due to the severe class imbalance, evaluation prioritizes **Recall**, **Precision**, **F1-Score**, and **PR-AUC (Precision-Recall Curve)** rather than raw accuracy.




