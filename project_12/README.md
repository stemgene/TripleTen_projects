# Project description

Rusty Bargain used car sales service is developing an app to attract new customers. In that app, you can quickly find out the market value of your car. You have access to historical data: technical specifications, trim versions, and prices. You need to build the model to determine the value.

Rusty Bargain is interested in:

* the quality of the prediction
* the speed of the prediction
* the time required for training

# Project process

1. Download and look at the data.
2. Train different models with various hyperparameters (You should make at least two different models, but more is better. Remember, various implementations of gradient boosting don't count as different models.) The main point of this step is to compare gradient boosting methods with random forest, decision tree, and linear regression.
3. Analyze the speed and quality of the models.

Note:
* Use the RMSE metric to evaluate the models.
*Linear regression is not very good for hyperparameter tuning, but it is perfect for doing a sanity check of other methods. If gradient boosting performs worse than linear regression, something definitely went wrong.
On your own, work with the LightGBM library and use its tools to build gradient boosting models.
* Ideally, your project should include linear regression for a sanity check, a tree-based algorithm with hyperparameter tuning (preferably, random forrest), LightGBM with hyperparameter tuning (try a couple of sets), and CatBoost and XGBoost with hyperparameter tuning (optional).
* Take note of the encoding of categorical features for simple algorithms. LightGBM and CatBoost have their implementation, but XGBoost requires OHE.
* You can use a special command to find the cell code runtime in Jupyter Notebook. Find that command.
* Since the training of a gradient boosting model can take a long time, change only a few model parameters.

# Model Analysis

Based on the "results" table, we can analyze the different models from both the quality and speed perspectives:

* Quality Analysis:

1. **Linear Regression**: The model has the highest Root Mean Squared Error (RMSE) of 2638.29, indicating that its predictive accuracy is sanity check.
2. Other models except the `Optimized CatBoost` obtain the metrics between 1500 to 1600. The worst among them is `LightGBM` with RMSE is 1591.93, the best among them is `CatBoost` with RMSE is 1516.50.
3. **Optimized CatBoost**: The optimized CatBoost model further improves its performance, achieving an RMSE of 1472.95, making it the best-performing model among all the listed models.

* Speed Analysis:

    I seperated the prediction time out from the training time.

    For training time, there are 3 hierarchies. `XGBoost` and the Random Forest models take the longest training duration. `Linear Regression` and the CatBoost models lie in the middle with tens seconds. LightGBM models are super fast, it only takes 2 - 3 seconds to train 3000000 entries data.

    For prediction time, all models except Random Forest only take less than 1 second. The fastest model is `CatBoost` with default settings, it only takes 0.06 second. The `Optimized CatBoost` and `Linear Regression` are slightly slower with 0.177 second. `XGBoost` and LightGBM take 0.2 - 0.4 second.

In summary, the `CatBoost` and `Optimized CatBoost` model achieves both the best quality and speed among all models. `CatBoost` takes 1/3 prediction time of `Optimized CatBoost`, while its RMSE is 3% worse than `Optimized CatBoost`. Alternatively, if a computation time of less than 0.2 second is acceptable, then the `Optimized CatBoost` can be chosen as it offers the highest accuracy.