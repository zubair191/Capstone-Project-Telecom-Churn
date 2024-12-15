# Capstone-Project-Telecom-Churn

# Telecom Churn Prediction

## Problem Statement

Customer churn is a critical issue in the telecom industry, where retaining existing customers is more cost-effective than acquiring new ones. In this project, we aim to predict which customers are at high risk of churn and identify the key indicators that contribute to churn behavior. The focus is on high-value customers, as they represent the majority of the company's revenue.

## Business Problem Overview

The telecom industry, especially in regions like India and Southeast Asia, faces a high churn rate, with customers frequently switching service providers. Customer retention is essential to reduce revenue leakage. By predicting churn in advance, telecom companies can take proactive steps to retain valuable customers and reduce churn, thereby minimizing the cost of customer acquisition.

## Churn Definition

We define churn as customers who have stopped using the services for a certain period, specifically those who:

- Have not used any services (calls, mobile internet) during the churn phase (Month 9).
  
This usage-based definition is applicable to prepaid customers, who may not inform the operator when switching to another network.

## High-Value Churn

High-value customers are defined as those who contribute significantly to revenue. In this project, we focus on predicting churn among high-value customers, as they account for about 80% of the total revenue.

## Understanding Customer Behavior During Churn

Customer behavior typically follows a pattern:

1. **Good Phase**: The customer is satisfied and using the service regularly (Month 6 and 7).
2. **Action Phase**: The customer starts showing signs of dissatisfaction (Month 8).
3. **Churn Phase**: The customer has churned (Month 9).

This project focuses on predicting churn in the Churn Phase (Month 9) based on data from the first three months.

## Dataset Overview

The dataset contains customer-level information over four months: June (Month 6), July (Month 7), August (Month 8), and September (Month 9). Key features include usage statistics (e.g., call minutes, mobile internet usage) and recharge amounts.

### Data Dictionary

The data dictionary explains the meaning of abbreviations used in the dataset. Some frequently used terms include:

- **loc**: Local
- **IC**: Incoming Calls
- **OG**: Outgoing Calls
- **T2T**: Telecom operator to telecom operator
- **RECH**: Recharge amount

### Data Columns

- **Month 6-8**: Features related to customer usage and recharge for months 6, 7, and 8.
- **Month 9**: Features for month 9, used to define churn (e.g., total_ic_mou_9, total_og_mou_9, vol_2g_mb_9, vol_3g_mb_9).

## Data Preparation

### 1. Deriving New Features

We derive features based on business understanding to better predict churn, such as:

- Average monthly recharge in the first two months.
- Usage patterns over time (e.g., total calls, data usage).

### 2. Filter High-Value Customers

High-value customers are defined as those whose average recharge amount in months 6 and 7 is greater than or equal to the 70th percentile of recharge amounts.

### 3. Tagging Churners

Churn is tagged based on month 9 data:

- Churners are customers who have not made calls or used mobile internet in month 9.

After tagging churners, we remove all attributes related to the churn phase (Month 9).

## Modelling Approach

### 1. Data Preprocessing

We preprocess the data to handle missing values, convert columns to appropriate formats, and normalize features if necessary.

### 2. Exploratory Data Analysis (EDA)

We conduct EDA to:

- Understand customer behavior.
- Identify patterns of usage that correlate with churn.
  
### 3. Feature Engineering

We derive new features and handle class imbalance through techniques like SMOTE (Synthetic Minority Over-sampling Technique).

### 4. Dimensionality Reduction (PCA)

Since the dataset contains many features, we reduce dimensionality using Principal Component Analysis (PCA) to improve model performance and interpretability.

### 5. Model Training

We train multiple classification models, including:

- Logistic Regression
- Decision Trees
- Random Forests
- Support Vector Machines (SVM)

We evaluate models based on performance metrics like:

- **Precision**: As churn prediction is a class-imbalance problem, it is more important to correctly identify churners.
- **Recall** and **F1-Score**: To balance false positives and false negatives.

### 6. Model Evaluation

We use cross-validation to assess model performance and select the best model based on evaluation metrics.

## Identifying Key Predictors

We build a separate model to identify the most important predictors of churn. This can be done using:

- Logistic Regression (for interpretability).
- Tree-based models (like Random Forest) for feature importance.

We visualize the most important features using bar plots, heatmaps, or summary tables.

## Recommended Strategies

Based on the analysis, we recommend the following strategies for reducing churn:

1. **Offer Competitive Plans**: For customers showing signs of dissatisfaction in the action phase, offer competitive recharge plans or discounts.
2. **Improve Customer Service**: Focus on resolving issues that cause customers to become unhappy with service quality.
3. **Target High-Value Customers**: Use the churn prediction model to proactively retain high-value customers, as they contribute significantly to revenue.

## Files Included

- **`main_script.py`**: The Python script performing the analysis and model building.
- **`presentation.pdf`**: A PDF presentation summarizing the analysis and business recommendations.
- **`README.md`**: This file, providing an overview of the project.

