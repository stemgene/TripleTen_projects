# Proposed work Plan

According to the project criterion, the AUC-ROC, we know it's a classification project. The target of this project is to predict whether the customer will be chrun or not.

Based on the given information, I will design the working plan which will carry out the following steps:

1. preprocess data. In this step, I'll investigate all columns one by one and apply appropriate methods on them.
    * Replace all column names into the snake_case type
    * Convert to appropriate data types, e.g. datetime, float, int...
    * Fill missing values
    * Other preprocess approaches if necessary.
2. EDA.
    * Check data distribution and outliers.
    * Target balance
    * Check correlations between target and features
    * Analyze some categorical features, e.g. `Type` and `InternetService`
3. Feature Engineering
    * `EndDate`: The target column is not a simple binary type, but it contains churn date. If I convert it to 'Yes' or 'No', it will loss important information. I plan to save this information, such like make a new feature 'tenure' to represent the contract peroid.
    * Make a new feature to indicate if customer use extra internet services
    * One-hot encoding or label encoding based on the model adaptability.
    * Scaling the numeric data
    * Remove redundant features
    * Split the data to training, validation and test sets
4. Train models. In this part, I will choose some popular classifiers, e.g. Logistic Regression, Decision Tree, Random Forest, XGBoost, LightGBM, CatBoost.
5. Fine tune the models. I'll use the RandomSearchCV and optuna to find the best parameters for those models.
6. Test the model on the test set. I'll evaluate ROC-AUC metric on the testset.
7. Conclusion and the next step suggestion.

# Conclusion

## Conclusion on the project

In this project, the quality of data is good, there is not many data clean process to do except there are many missing values in internet and phone tables. The target is imbalanced, so I've applied the upsample method to generate more positive target labels.

There are some interesting facts when I worked on EDA.

* All churned data are from last 5 months
* The IQR of monthly_charges from the churned customers are greater than stay customers.
* According to the type column, most of (88.6%) churned customers are 'month-to-month'.
* Only 25% churned customer use automatic payment method, while 50% for stay customers.
* One thing to note that the columns of total_charges and usage_months will cause data leak, so I've dropped them before training.

After encoding and scaling the data, I applied 6 classification models with their default settings to train the data.

During the fine tuning part, I printed out the default hyperparameters of each model, and generated couples of values smaller and greater than them and store them into the variable of params_grid. Then I introduced the RandomizeSearchcv to look for the best hyperparameters. Some of models took long time for searching because I list many hyperparameters. After a searching session finished, I list another group of hyperparameters based on the searching result. However, not all fine tuned models had better results than the default settings.

Finally, I chose the best preformance model to evaluate on the test set and get the ROC-AUC score 0.860.

### Next step ideas:

I still have two ideas about improving the ROC-AUC score.

* Since RandomizeSearchcv combines the hyperparameter group randomly for a faster searching speed. It might skip some good groups. I'd like to try GridSearchcv right after RandomizeSearchcv, especially for those models which got worse performance after fine tuning.
* In the current version, I replaced the 'Unknown' to the missing values. But my tutor told me that the missing values can be seemed as 'No'. Once I changed this, all dataset will be changed too. I'd like to try it out.

## Suggestions

The top 3 important features are `monthly_charges`, `begin_date` and `payment_method`.

As I descibed before, there is significant different on `monthly_charges` of churned and stay customers, as well as the `payment_method`.

Based on the summary of this project, I have some suggestions to the company.

Suggestions:
* Encourage customers to sign the one year or two years contracts.
* Give more promotional resources to automatic payment methods.
* Pay more attention on customers who are in monthly contract but spend higher cost. If they have sign to leave, some retention solutions should be applied.