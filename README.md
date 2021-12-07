# introml-g2t4 (Predicting Customer Credit Card Churn)
This project was one of the assessment components for the Singapore Management University (SMU) module CS421 - Introduction to Machine Learning.

---

### Table of Contents
- [Description](#Description)
- [Dataset & Preprocessing](#Dataset)
- [Preprocessing](#Preprocessing)
- [Modelling & Results](#Modelling)
- [Contributors](#Contributors)

---

## Description
With retail banking becoming increasingly competitive recent years, effective customer retention strategies are necessary for traditional financial institutions (FIs) such as banks and credit card companies because an attrited customer is a loss in revenue. Credit cards are an especially important source of revenue for FIs, however, these financial products are often exploited by "churners" who repeatedly open and close credit cards in order to benefit from the sign-up bonuses. Through machine learning, we can discover hidden insights from customer financial activity datasets. Through these insights, FIs may then more concretely ‘define’ retention and proactively offer further personalized promotions and offers to retain the right customers.

## Dataset & Preprocessing
The dataset used is entitled 'Credit Card customers', and was sourced from [Kaggle](https://www.kaggle.com/sakshigoyal7/credit-card-customers). The dataset is a sample of credit card customer accounts from a single bank, which was kept confidential. It contains 10,127 rows of unique customer information and 21 features that describe their spending behaviours and background. The target variable is attrition_flag, which shows whether the customer has closed their credit card account.

EDA was conducted to understand the data better, after which, the following preprocessing steps were conducted:
- Imputation of unknown values
- Feature encoding
- Feature transformation 
- Feature scaling

Due to the large number of features in the dataset, several feature selection techniques were used to reduce dimensionality:
- Pearson's correlation coefficient
- Filter methods (Chi-square test and ANOVA)
- Embedded methods (Random Forest and XGBoost feature importance)

The occurrence of features obtained from the three techniques were collated into an Excel spreadsheet. Based on the number of occurrences of each feature, along with our team’s understanding of the features from EDA, we made deductions on which columns to drop. After feature selection, the number of features was reduced to 10. 


## Modelling & Results
An 80-20 train-test split was performed on the preprocessed dataset to obtain a train and test set with 8,101 and 2,026 records respectively. Following this, four machine learning models were trained using three rounds of hyperparameter tuning for each of the four models, using a 5-fold stratified cross-validation grid search. An overview of the machine learning model workflow can be found below.

### Diagram of machine learning model workflow
![Machine learning model workflow](https://i.postimg.cc/3rfRMmV9/model-plan.png)

To evaluate our models, recall score was prioritized because we want to maximise the number of actual attrited customers we can identify: to minimise the number of false negatives, which are the attrited customers wrongly predicted as existing customers. It was found that XGBoost performed the best, with a Recall = 0.873846, F2 score = 0.86479, and AUC = 0.919874. 

The top five features from this XGBoost model are: total_trans_count, total_revolving_bal, total_relationship_count, months_inactive_12_mon and contacts_count_12_mon. Based on these top five features, only total_relationship_count is related to a customer’s background, while the rest are related to their bank usage patterns. This could be due to the fact that the interaction between the customer and the bank determines how satisfied the customer is with their services and responses. Banks could focus more on card usage trends and customer feedback to find new strategies to improve customer retention rates. Through this, they may also be able to identify potential customers who may churn and offer them attractive deals to retain them.



### Contributors
1. Joshua Wong Yeung Nguon ([LinkedIn](https://www.linkedin.com/in/joshuawong96/), [Github](https://github.com/joshuawong96))
2. Ow Ling Jia ([LinkedIn](https://www.linkedin.com/in/owlingjia/), [Github](https://github.com/owlingjia))
