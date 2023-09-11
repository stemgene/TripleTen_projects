# Project Description

The Sure Tomorrow insurance company wants to solve several tasks with the help of Machine Learning, and you are asked to evaluate that possibility.

* Task 1: Find customers who are similar to a given customer. This will help the company's agents with marketing.
* Task 2: Predict whether a new customer is likely to receive an insurance benefit. Can a prediction model do better than a dummy model?
* Task 3: Predict the number of insurance benefits a new customer is likely to receive using a linear regression model.
* Task 4: Protect clients' personal data without breaking the model from the previous task.

It's necessary to develop a data transformation algorithm that would make it hard to recover personal information if the data fell into the wrong hands. This is called data masking, or data obfuscation. But the data should be protected in such a way that the quality of machine learning models doesn't suffer. You don't need to pick the best model, just prove that the algorithm works correctly.

# Project Process

1. Load the data.
2. Check that the data is free of issues — there is no missing data, extreme values, and so on.
3. Work on each task and answer the questions posed in the project template.
4. Draw conclusions based on your experience working on the project.

# Conclusions

In this project, I implemented a KNN classification model and a customed linear regression model on the dataset.

Based on the KNN technique, we could not only find the similar vectors by a given vector, we can also make a classification. The prediction results are influenced by the hyperparameter K, but in the classification case, the factor of whether the data has been scaled plays more important role.

On the other hand, for the regression mission, feature scaling seems not as important as in classification task. I also applied two models with different distance algorithms, but the results were very close.

Additionally, for the sake of protecting customers privacy, it's important to de-indificate customer personal information. The method is to dot multiple an invertible matrix to make the original data meaningless. This operation will affact the parameter matrix, but won't change the predition results as well as RMSE or R2 metrics.