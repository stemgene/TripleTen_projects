# Project Description

The Film Junky Union, a new edgy community for classic movie enthusiasts, is developing a system for filtering and categorizing movie reviews. The goal is to train a model to automatically detect negative reviews. You'll be using a dataset of IMBD movie reviews with polarity labelling to build a model for classifying positive and negative reviews. It will need to reach an F1 score of at least 0.85.

# Project process

1. Load the data.
2. Preprocess the data, if required.
3. Conduct an EDA and make your conclusion on the class imbalance.
4. Preprocess the data for modeling.
5. Train at least three different models for the given train dataset.
6. Test the models for the given test dataset.
7. Compose a few of your own reviews and classify them with all the models.
8. Check for differences between the testing results of models in the above two points. Try to explain them.
9. Present your findings.

Important! The project template already contains some code snippets for your convenience, so you can use them if you'd like. If you want to start right away from a clean sheet, just remove all those code snippets. Here's the list of code snippets:

* A bit of EDA with some plots
* `1evaluate_model()`
    * a routine to evaluate a classification model which conforms to the scikit-learn predict interface
* `BERT_text_to_embeddings()`
    * a routing to convert a list of texts into embedding with BERT

# Conclusions

I've applied 3 machine learning models (Linear Regression, XGBoost and LightGBM) on 2 datasets (NLTK & TF-IDF and spaCy & TF-IDF), all perform well on the test set.

Specifically, for the dataset with NLTK and TF-IDF vectorization method, Linear Regression obtains the best F1-score of 0.88 and XGBoost gets 0.85. For the dataset with spaCy and TF-IDF vectorization method, Linear Regression obtains the best F1-score of 0.88 too, LightGBM and XGBoost get 0.86 and 0.85 corresponsely.

When those models predicted the dataset of "my_review", the model_2, model_4 and model_5 obtained the best F1-score of 0.89 while other 2 models got the F1-score of 0.67.

It shows if only considering to analyze the sentiment of sentences, most regular machine learning models will obtain a good enough result once the corpus were vectorized proporly.