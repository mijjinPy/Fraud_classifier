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
 
## 05 Machine Learning Aproach, Metrics & Scaler:
* **Task Type:** Supervised binary classification on imbalance data.
* **Evaluation Metrics:** Due to the severe class imbalance, evaluation prioritizes **Recall**, **Precision**, **F1-Score**, and **PR-AUC (Precision-Recall Curve)** rather than raw accuracy.
*  **Selected Scaler:** **`QuantileTransformer(output_distribution='normal')`**

## 06 Exploratory Data Analysis and Model Evaluation

### General Dataset Exploration

The first step was to perform a general inspection of the dataset. I checked:

* Data types and structure of the variables.
* Missing values.
* Duplicate records.
* Descriptive statistics.

This initial analysis provided an overview of the dataset and helped identify potential data-quality issues before training the models.

### Class Distribution and Imbalance Analysis

The class distribution was analyzed to determine whether the target variable was balanced.

The analysis revealed a significant class imbalance, with the minority class representing a much smaller portion of the dataset. Because this is a fraud-detection problem, addressing this imbalance was important to avoid a model that simply favors the majority class.

### Continuous Variable Analysis

The continuous variables were analyzed to identify skewed distributions. Different transformations and scaling approaches were considered to make the distributions more suitable for machine learning algorithms.

After comparing the results, **Quantile Transformation** was selected to transform the continuous variables toward a more Gaussian-like distribution.

### Correlation Analysis

A correlation heatmap was used to analyze relationships between the variables.

Although some features showed weak direct correlation with the target variable, they were not removed because they still showed relationships with other features. Therefore, the variables were retained for model training rather than removing them solely based on their individual correlation with the target.

### Model Evaluation

Two different evaluation approaches were used:

1. **SMOTE-based evaluation**
2. **Stratified K-Fold Cross-Validation**

Four classification algorithms were evaluated:

* K-Nearest Neighbors (KNN)
* Random Forest
* LightGBM
* XGBoost

#### SMOTE Approach

For the SMOTE-based experiments, the data was prepared specifically for each algorithm.

KNN required feature scaling, so the previously selected transformation and standardization were applied before using SMOTE. Tree-based models such as Random Forest, LightGBM, and XGBoost did not require feature standardization.

The models achieved very high evaluation scores overall. Random Forest produced nearly perfect results, which raised concerns about possible overfitting or data leakage. The preprocessing and implementation were reviewed to verify that there were no apparent errors causing the unusually high performance.

Under the SMOTE-based evaluation, **LightGBM achieved the best overall performance**.

#### Stratified K-Fold Cross-Validation

To obtain a more robust comparison, a 5-fold **Stratified K-Fold Cross-Validation** approach was implemented.

A pipeline-based evaluation function was created to ensure that preprocessing and model training were handled consistently within the cross-validation process.

The models were compared using:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC

In this evaluation, **Random Forest achieved the best overall performance**, followed by LightGBM and XGBoost.

Random Forest again produced exceptionally high scores, including a precision of 1.0 and a ROC-AUC very close to 1.0. Although this result made overfitting or data leakage a concern, the implementation was reviewed and no apparent error was found.

### Final Results

The Stratified K-Fold evaluation was used as the decisive comparison because it provided a more robust estimate of model performance across multiple train-validation splits.

The final ranking was:

1. **Random Forest**
2. **LightGBM**
3. **XGBoost**
4. **KNN**

Random Forest was therefore selected as the best-performing candidate.

### Conclusion

The models achieved exceptionally high performance across both evaluation approaches. The results suggest that the dataset has a relatively simple class separation, allowing tree-based models to distinguish between the classes very effectively.

Although Random Forest achieved the best overall results, its nearly perfect performance should be interpreted cautiously. Further testing on an independent test set would be appropriate to confirm that the performance generalizes to unseen data and to further rule out potential data leakage.




