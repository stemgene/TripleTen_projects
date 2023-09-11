# Project Description

Beta Bank customers are leaving: little by little, chipping away every month. The bankers figured out it’s cheaper to save the existing customers rather than to attract new ones.

We need to predict whether a customer will leave the bank soon. You have the data on clients’ past behavior and termination of contracts with the bank.

Build a model with the maximum possible F1 score. To pass the project, you need an F1 score of at least 0.59. Check the F1 for the test set.

Additionally, measure the AUC-ROC metric and compare it with the F1.

# Conclusion

In this project, I implement 3 steps: Preprocessing, Training and Testing.

* Preprocessing:
    * Data cleaning: 
        * Fill the missing values
        * Drop useless columns
    * Preparing for training
        * Label encoding categorical features.
        * Checking if the data is imbalanced. The negative labels are 4 time more than positive classes.
        * Split the data for training and testing.
* Training:
    * Train the models without taking into account the imbalance
        
        I applied 5 popular classification models to train the dataset. Due to the imbalance, the performance was bad. Although the accuracies of models were around 0.8, the best F1 score is 0.579.
        
        
    * Addressing the imbalanced dataset.
        * Method 1: Upsampling the positive classes.
        
        After upsampling, the performance was increased significantly.
        
        The best two models are XGBoost and Random Forest. I chose them to the next steps.