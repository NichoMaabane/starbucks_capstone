

# Starbucks Capstone Challenge: Customer Offer Response Analysis

**Project Overview**


The Starbucks Capstone Challenge aims to analyze customer interactions with various promotional offers to understand which demographic groups respond best to which types of offers. The goal is to develop a predictive model to determine customer engagement with offers, optimize marketing strategies, and maximize revenue.

# Problem we are solving for:

**The problem we are solving is to determine which demographic groups respond best to which types of offers on the Starbucks rewards mobile app**
    - Understand how different customer demographics (e.g., age, gender, income) interact with various types of offers
    - Determine which offers are most effective for specific customer segments.
    - Build a predictive model to forecast whether a customer will respond to a specific offer based on their demographic and transactional history.

# Metrics

**Why Accuracy and F1-Score Are Relevant for Starbucks Problem
Business Goal:**

The goal is to maximize the number of customers who respond to offers while minimizing unnecessary offers to customers who are unlikely to respond.

This requires balancing precision (avoiding false positives) and recall (identifying as many true positives as possible).

**Imbalanced Data:**

If the dataset is imbalanced (e.g., fewer customers respond to offers), accuracy alone is not sufficient.

The F1-score provides a better measure of model performance in such cases.

**Actionable Insights:**

The F1-score helps ensure that the model is not only accurate but also effective in identifying the right customers for offers


# Data Sources

**The project uses three datasets:**

Portfolio.json: Contains details about promotional offers, including type (bogo, discount, informational), duration, reward, and difficulty.

Profile.json: Contains demographic information about customers, including age, gender, income, and membership start date.

Transcript.json: Logs customer interactions with offers and transactions, including offer received, viewed, completed, and transaction amounts.

Data Preprocessing & Feature Engineering

Data Cleaning & Transformation

Handling Missing Values:

Missing values in the income column were replaced with the median income.

Missing values in the gender column were labeled as "Unknown".

Date Processing:

became_member_on was converted to datetime format.

membership_duration_days was derived as the number of days since a customer joined Starbucks.

Event Encoding:

Offer interactions (offer received, offer viewed, offer completed, transaction) were converted into binary features.

Categorical Encoding:

gender was one-hot encoded.

offer_type was label-encoded for modeling purposes.

Feature Engineering:

total_spent: Total amount a customer has spent.

average_transaction_amount: Mean transaction amount.

offer_response_rate: Ratio of completed offers to received offers.

Time differences between offer events (offer_received, offer_viewed, offer_completed) were calculated.

age_group and income_bracket were created to analyze behavioral trends across demographics.

# Exploratory Data Analysis

**Demographic Insights:**

Customers aged 40-60 and those with higher income responded best to discount and BOGO (Buy One Get One) offers.

Customers under 25 had the lowest offer completion rates.

Offer Response Trends:

Discount offers had the highest completion rates.

Informational offers had no recorded completions, indicating that they may not directly lead to transactions.

# Predictive Modeling

Target Variable

The target variable is offer_completed, indicating whether a customer successfully completed an offer.

Feature Selection

Selected features to avoid overfitting and improve model generalization:

age, income, membership_duration_days, offer_type_encoded, offer_difficulty, offer_reward, offer_duration

total_spent, average_transaction_amount, offer_response_rate

time_diff_received_viewed, time_diff_viewed_completed, time_diff_received_completed

Data Splitting

The dataset was split into 80% training and 20% testing sets.

Model Training

Random Forest Classifier was used with class weighting to address class imbalance (offer completion was rare compared to non-completion).

Model Evaluation


Model Accuracy: 0.97
Precision: 0.82
Recall: 0.96
ROC-AUC Score: 0.97
Accuracy: 0.89

Addressing Class Imbalance

Instead of SMOTE, class weighting was used to balance the dataset, ensuring the model gives more importance to minority class instances.

# Conclusion & Business Insights

**Demographic Targeting:**

Older customers (40-60 and 60+) with high incomes respond best to discount and BOGO offers.

Younger customers (<25) and those with lower incomes show significantly lower engagement with promotional offers.

Offer Type Effectiveness:

Informational offers are ineffective in driving transactions.

Discount offers lead to the highest completion rates.

Model Performance Challenges:

The model struggles to predict offer completions due to data imbalance.

Further refinements, such as alternative sampling techniques or deep learning approaches, may improve results.

Future Work

Experiment with alternative models (e.g., Gradient Boosting, Neural Networks) to improve predictive accuracy.

Refine feature engineering by exploring customer behavioral patterns in more depth.

A/B test marketing strategies by sending different offers to targeted groups based on insights.

This analysis provides Starbucks with actionable insights on customer behavior, enabling more effective marketing strategies tailored to different demographic groups.
