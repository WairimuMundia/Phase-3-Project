
# SyriaTel Customer Churn Analysis

## Overview


'project analyzes the SyriaTel Customer Churn dataset to explore if there are any predictable patterns with customer turnover. By identifying these patterns, we aim to provide actionable insights to help SyriaTel reduce its customer churn rate, thereby saving costs and improving customer satisfaction.

## Business Problem

Customer churn is a significant issue for SyriaTel, leading to substantial financial losses. Understanding the reasons behind customer churn and predicting which customers are likely to leave can enable SyriaTel to implement targeted retention strategies. This project aims to analyze customer data to uncover patterns associated with churn and develop models to predict future churn.

## Data Understanding

The analysis begins by importing all necessary packages, including those for data manipulation, visualization, and machine learning. The data is imported from SyriaTel, and initial exploration is conducted to understand its structure and content.

### Data Description
The dataset contains various features, including customer demographics, usage metrics, service subscription details, and whether the customer has churned. Some columns, such as state, area code, and phone number, are deemed irrelevant for the analysis and are subsequently dropped.

### Data Cleaning
To prepare the dataset for analysis, we perform several cleaning steps:
- **Dropping irrelevant columns**: Columns like state, area code, and phone number are removed.
- **Handling categorical variables**: We use onehotencoder to convert categorical variables into a suitable format for modeling. For binary variables like international plan and voicemail plan, 'yes' is converted to 1 and 'no' to 0.
- **Data type conversion**: The churn column is converted to an integer type for easier manipulation during modeling.

## Data Exploration

Data exploration involves visualizing relationships between various features and the churn variable. By plotting different categories against churn, we identify potential predictors of customer churn. For instance, features like customer service calls, day charges, and day minutes are examined to see how they correlate with churn rates.

## Data Preparation

### Feature Engineering
We split the dataset into feature (X) and target (y) dataframes. The feature dataframe (X) includes all variables except 'churn', while the target dataframe (y) consists solely of the 'churn' variable.

### Data Scaling
To ensure that all features contribute equally to the model performance, we scale the X variables. This step standardizes the range of independent variables, which is particularly important for algorithms sensitive to feature scaling.

## Data Modeling

We employ three different machine learning models to predict customer churn:
1. **Logistic Regression**
2. **DecisionTreeClassifier**
3. **XGBClassifier**

### Logistic Regression Model #1
The initial logistic regression model did not perform as well as expected. To address this, we applied Synthetic Minority Over-sampling Technique (SMOTE) to balance the dataset, creating synthetic instances of the minority class (churn).

### Logistic Regression Model #2
After applying SMOTE, the second logistic regression model showed improved performance, with better precision, recall, and f1-scores.

### DecisionTreeClassifier
The DecisionTreeClassifier model performed significantly better than logistic regression. It achieved high scores across precision, recall, and f1-score metrics, and the confusion matrix indicated a majority of true positives.

### XGBClassifier
The XGBClassifier outperformed the other two models, showing the highest scores for the test data and perfect scores on the training data. This model exhibited robust performance, indicating its suitability for predicting customer churn.

## Evaluation

### Model Comparison
The three models were evaluated and compared based on their performance metrics. The ranking from highest to lowest performance is as follows:
1. **XGBClassifier**
2. **DecisionTreeClassifier**
3. **Logistic Regression**

The XGBClassifier was chosen as the final model due to its superior performance, both on training and test datasets. It exhibited high precision, recall, and f1-scores, with minimal false positives and true negatives.

## Conclusion

### Key Findings
- **Customer Service Calls**: Higher number of customer service calls is correlated with increased churn.
- **Day Charges and Day Minutes**: High day charges and extensive usage minutes are also linked to higher churn rates.

### Recommendations
Based on the analysis and modeling results, we recommend the following actions for SyriaTel to reduce customer churn:
1. **Reduce Costs of Day Charges**: Implement pricing strategies to lower day charges, making the service more attractive to customers.
2. **Offer Bonuses for Minutes Used**: Provide incentives for customers based on their usage minutes to encourage loyalty.
3. **Improve Customer Service**: Focus on enhancing customer service to address and resolve issues promptly, reducing the likelihood of churn.

By implementing these recommendations, SyriaTel can address the key factors contributing to customer churn and improve overall customer retention.

## Future Work
Future analyses could explore additional data sources, such as customer feedback or social media sentiment, to gain deeper insights into customer satisfaction. Furthermore, incorporating advanced machine learning techniques and model tuning could further enhance the predictive accuracy of the models.
