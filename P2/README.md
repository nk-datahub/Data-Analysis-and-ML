# Credit Card Fraud Detection

This project focuses on detecting fraudulent credit card transactions using machine learning models. The primary goal is to analyze transaction patterns, handle class imbalance, and build predictive models to accurately identify fraud.  

## Table of Contents
- [Project Overview](#project-overview)  
- [Dataset](#dataset)  
- [Data Cleaning & Preprocessing](#data-cleaning--preprocessing)  
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)  
- [Handling Class Imbalance](#handling-class-imbalance)  
- [Predictive Modeling](#predictive-modeling)  
- [Key Insights](#key-insights)  
- [Technologies Used](#technologies-used)  
- [Future Work](#future-work)  

## Project Overview
The objective of this project is to:  
- Analyze credit card transaction data to identify patterns that distinguish fraudulent and legitimate transactions.  
- Address the class imbalance problem inherent in fraud detection datasets.  
- Build and evaluate machine learning models (Logistic Regression, Random Forest) to predict fraudulent transactions.  

## Dataset
The dataset `creditcard.csv` contains 284,807 transactions with 31 columns:  

- `Time` – Seconds elapsed between the first transaction and the current one  
- `V1` to `V28` – PCA-transformed anonymized features  
- `Amount` – Transaction amount  
- `Class` – Target variable (0 = Normal, 1 = Fraud)  

No missing values are present in the dataset.  

## Data Cleaning & Preprocessing
Key preprocessing steps:  
1. Dropped rows with missing values (none in this dataset).  
2. Standardized `Time` and `Amount` using `StandardScaler` to prevent magnitude dominance.  
3. Split the dataset into features `X` and target `y`.  
4. Split train and test sets with stratification to preserve class distribution:  
   - Training: 227,845 samples  
   - Testing: 56,962 samples  

## Exploratory Data Analysis (EDA)
- **Transaction Amount:** Fraudulent transactions tend to have smaller amounts compared to normal transactions.  
- **Transaction Time:** Fraudulent transactions show different time distributions, suggesting peak fraud periods.  
- **PCA Features (V1–V4):** Some components display clear differences between normal and fraudulent transactions.  
- **Correlation Analysis:** Strong correlations among certain features can guide feature selection and engineering.  

## Handling Class Imbalance
Fraud is rare (0.17% of transactions). Techniques used:  

1. **Class Weights:** Balanced weighting in model training to penalize misclassification of frauds.  
2. **Random Undersampling:** Reduced majority class to 1:3 ratio with minority class.  
3. **SMOTE (Synthetic Minority Oversampling Technique):** Generated synthetic fraud samples to achieve 1:3 ratio.  

**Decision:** SMOTE-resampled data was used to provide sufficient fraud examples for training.  

## Predictive Modeling

### Logistic Regression
- Trained on SMOTE-resampled data with class weights.  
- Evaluation on test set:  
  - Confusion matrix:  
    ```
    [[55431  1433]
     [    8    90]]
    ```  
- Logistic Regression effectively identifies most frauds with minimal false negatives.  

### Random Forest Classifier
- Trained on SMOTE-resampled data with balanced class weights.  
- Confusion matrix on test set visualized via heatmap.  
- Feature importance analysis revealed the top predictors of fraud.  
- Top 3 features analyzed using histograms for Normal vs. Fraud classes.  

## Key Insights
1. Fraudulent transactions are often smaller in amount and occur at specific times.  
2. Certain PCA-transformed features (V1–V4) strongly differentiate fraud vs. normal.  
3. Handling class imbalance is crucial; SMOTE significantly improves model training.  
4. Random Forest provides interpretable feature importance, highlighting key fraud indicators.  

## Technologies Used
- Python (pandas, numpy, matplotlib, seaborn)  
- Machine Learning: scikit-learn (Logistic Regression, Random Forest)  
- Imbalanced-learn (SMOTE, RandomUnderSampler)  
- Data Visualization: Matplotlib, Seaborn  

## Future Work
- Explore advanced algorithms like XGBoost, LightGBM, or neural networks for better performance.  
- Incorporate temporal analysis to detect fraud patterns over time.  
- Develop a real-time fraud detection pipeline with streaming data.  
