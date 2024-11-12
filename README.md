# Crowdfunding Campaign Success Prediction

This project aims to predict the success of crowdfunding campaigns using machine learning models: **Ensemble Learning (Bagging - Random Forest & Boosting - AdaBoost, Gradient Boost, XGBoost), Naive Bayes, and Support Vector Machine (SVM)** . The dataset used contains features like campaign financial goals, funds raised, campaign duration, and backer engagement. This project evaluates which model performs best in classifying campaign success based on accuracy and other factors.

## Project Overview

Crowdfunding campaigns have varying success rates, influenced by factors like the amount raised, campaign duration, and backer engagement. In this project, I apply machine learning techniques to predict campaign success. The following steps were carried out:

1. **Data Preprocessing**: Missing values were handled, categorical features were encoded, and data was split for training and testing.
2. **Modeling**: Three classifiers were built and tuned:
   - Random Forest
   - Naive Bayes
   - Support Vector Machine (SVM)
3. **Evaluation**: Each model was evaluated based on accuracy.

## Dataset

The dataset used for this project can be found [here](https://raw.githubusercontent.com/ArchanaInsights/Datasets/refs/heads/main/crowdfunding_campaign.csv).

### Features
- **CampaignID**: Unique identifier for each campaign.
- **GoalAmount**: The target funding goal set by the campaign owner.
- **RaisedAmount**: The actual amount raised by the campaign during its duration.
- **DurationDays**: Total number of days the campaign was active.
- **NumBackers**: Number of backers who contributed to the campaign.
- **Category**: The category or type of campaign (e.g., Technology, Art, Health).
- **LaunchMonth**: The month in which the campaign was launched.
- **Country**: Country where the campaign originated.
- **Currency**: Currency used for the campaign's financial transactions.
- **OwnerExperience**: Experience level of the campaign owner, which may indicate familiarity with running crowdfunding campaigns.
- **VideoIncluded**: Indicates if a promotional video was included (1 = Yes, 0 = No).
- **SocialMediaPresence**: Indicates if the campaign had an active social media presence (1 = Yes, 0 = No).
- **NumUpdates**: Number of updates the campaign owner posted throughout the campaign.

### Target
- **Success**: Binary label indicating campaign success (1) or failure (0).

## Exploratory Data Analysis (EDA)

## Exploratory Data Analysis (EDA)

- **Outlier Detection**: `RaisedAmount` shows high values linked to successful campaigns.
- **Dataset Balance**: 50% success rate, enabling unbiased model training.
- **Distribution**: `GoalAmount` is normally distributed; `RaisedAmount` is right-skewed due to high-performing campaigns.
- **Success Classification**: Most campaigns fall under "Strong Success" (Raised Amount > 120% of Goal).
- **Feature Insights**: Success rates are consistent across `Currency`, `Category`, and `Country`, with slight increases for campaigns in Germany/EUR.
- **Seasonality**: Success peaks in April, with fluctuations across the year.
- **Statistical Tests**: **OwnerExperience** strongly influences success; minimal impact from `SocialMediaPresence`, `VideoIncluded`, and `Currency`.

## Machine Learning Models and Evaluation

### 1. Ensemble Learning - Bagging (Bootstrap Aggregation)
#### **Random Forest**
- **Tuning Parameters**: `n_estimators`, `max_depth`
- **Evaluation Metric**: Accuracy on test data
  
   ![image](https://github.com/user-attachments/assets/fe754038-dcc0-4b5f-97d7-9b2fdfe90a40)

### 2. Ensemble Learning - Boosting
#### **Adaptive Boosting (AdaBoost)**
- **Tuning Parameters**: `n_estimators`, `max_depth`
- **Evaluation Metric**: Accuracy on test data
  
   ![image](https://github.com/user-attachments/assets/76085aea-4e74-4cf6-b573-82511a5a6ee4)

#### **Gradient Boosting**
- **Tuning Parameters**: `n_estimators`
- **Evaluation Metric**: Accuracy on test data

   ![image](https://github.com/user-attachments/assets/2df257cb-1fa7-47e1-9555-b90b2f86f0a3)

#### **Extreme Gradient Boosting (XGBoost)**
- **Tuning Parameters**: `n_estimators`, `max_depth`
- **Evaluation Metric**: Accuracy on test data

   ![image](https://github.com/user-attachments/assets/50fb90ce-f1dc-4c1a-92d9-cf610aede7ac)

### 3. Naive Bayes
- **Type**: Chose Gaussian, Multinomial, or Bernoulli based on feature distribution
- **Evaluation Metric**: Accuracy on test data

### 4. Support Vector Machine (SVM)
- **Kernel Options**: Experimented with `linear` and `RBF` kernels
- **Evaluation Metric**: Accuracy on test data

### 5. **Comparison and Analysis**
- **Best Model**: SVM with a linear kernel showed the highest accuracy (99.87%). However, for real-time use with large datasets, **XGBoost** (99.27%) is more efficient and robust.
- **Random Forest**: Good performance but less efficient than XGBoost.
- **Naive Bayes**: Inaccurate for this dataset due to its independence assumptions.

### 6. **Strengths and Weaknesses**
- **SVM**: Strong performance but may demand high memory for large datasets.
- **XGBoost**: Best balance between accuracy and computational efficiency.
- **Naive Bayes**: Performs poorly with complex, high-dimensional datasets like this one.
