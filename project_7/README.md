# Project description

Mobile carrier Megaline has found out that many of their subscribers use legacy plans. They want to develop a model that would analyze subscribers' behavior and recommend one of Megaline's newer plans: Smart or Ultra.

You have access to behavior data about subscribers who have already switched to the new plans (from the project for the Statistical Data Analysis course). For this classification task, you need to develop a model that will pick the right plan. Since you’ve already performed the data preprocessing step, you can move straight to creating the model.

Develop a model with the highest possible accuracy. In this project, the threshold for accuracy is 0.75. Check the accuracy using the test dataset.

# Conclusion

In this project, I implemented 5 models to make the classification experiment.

At first, I used the default setting of these models, then I applied grid search to find the best hyperparameters of Decision Tree, Random Forest and XGBoost. After optimized, these models performed better than with the default settings.

For metrics, I used the accuracy, the auc score and the f1 score. I noticed that the f1 scores of all models were less than 0.65. The main reason is the dataset is not balance enough, there are only a few True Positive values while with lots of True Negative values, but the TN values doesn't affact the f1 score.