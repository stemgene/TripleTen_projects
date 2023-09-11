# Project Description

Prepare a prototype of a machine learning model for Zyfra. The company develops efficiency solutions for heavy industry.

The model should predict the amount of gold recovered from gold ore. You have the data on extraction and purification.

The model will help to optimize the production and eliminate unprofitable parameters.

# Project Process

## Technological Process

How is gold extracted from ore? Let's look into the process stages.

Mined ore undergoes primary processing to get the ore mixture or rougher feed, which is the raw material for flotation (also known as the rougher process). After flotation, the material is sent to two-stage purification.

Let's break down the process:

![img](https://github.com/stemgene/TripleTen_projects/blob/main/datasets/project10_god_mix_process.jpg)

1. Flotation

Gold ore mixture is fed into the float banks to obtain rougher Au concentrate and rougher tails (product residues with a low concentration of valuable metals).

The stability of this process is affected by the volatile and non-optimal physicochemical state of the flotation pulp (a mixture of solid particles and liquid).

2. Purification

The rougher concentrate undergoes two stages of purification. After purification, we have the final concentrate and new tails.

## Revovery calculation

I need to simulate the process of recovering gold from gold ore.

Use the following formula to simulate the recovery process:

$$Recovery = \frac{C * (F - T)}{F * (C - T)} \times 100\%$$

where:
* C — share of gold in the concentrate right after flotation (for finding the rougher concentrate recovery)/after purification (for finding the final concentrate recovery)
* F — share of gold in the feed before flotation (for finding the rougher concentrate recovery)/in the concentrate right after flotation (for finding the final concentrate recovery)
* T — share of gold in the rougher tails right after flotation (for finding the rougher concentrate recovery)/after purification (for finding the final concentrate recovery)

To predict the coefficient, you need to find the share of gold in the concentrate and the tails. Note that both final and rougher concentrates matter.

## Evaluation metric

To solve the problem, we will need a new metric. It is called sMAPE, symmetric Mean Absolute Percentage Error.

It is similar to MAE, but is expressed in relative values instead of absolute ones. Why is it symmetrical? It equally takes into account the scale of both the target and the prediction.

Here’s how sMAPE is calculated:

$$sMAPE = \frac{1}{N}\sum_{i=1}^{N}\frac{|y_i-\hat{y_i}|}{(|y_i|+|\hat{y_i}|)/2}\times100\%$$


We need to predict two values:
1. rougher concentrate recovery rougher.output.recovery
2. final concentrate recovery final.output.recovery

The final metric includes the two values:

$$Final\ sMAPE=0.25 \times sMAPE(rougher) + 0.75 \times sMAPE(final)$$

## Project process

1. Prepare the data


    1.1. Open the files and look into the data.

    1.2. Check that recovery is calculated correctly. Using the training set, calculate recovery for the rougher.output.recovery feature. Find the MAE between your calculations and the feature values. Provide findings.

    1.3. Analyze the features not available in the test set. What are these parameters? What is their type?

    1.4. Perform data preprocessing.

2. Analyze the data

    2.1. Take note of how the concentrations of metals (Au, Ag, Pb) change depending on the purification stage.

    2.2. Compare the feed particle size distributions in the training set and in the test set. If the distributions vary significantly, the model evaluation will be incorrect.

    2.3. Consider the total concentrations of all substances at different stages: raw feed, rougher concentrate, and final concentrate. Do you notice any abnormal values in the total distribution? If you do, is it worth removing such values from both samples? Describe the findings and eliminate anomalies.

3. Build the model

    3.1. Write a function to calculate the final sMAPE value.

    3.2. Train different models. Evaluate them using cross-validation. Pick the best model and test it using the test sample. Provide findings.


# Conclusion
In this project, I mainly finished three tasks.

* Prepare the data

    Unlike previous projects which provide a single dataset, this time a train set and a test set have been given, and they are different in features. Additionally, in order to follow and answer the project instuction questions, it won't be clear if I use the traditional process of data cleaning, such as check duplicated, missing value and so on.
    
    Then main data validity issue are missing and zero values on important features. According to the distribution plot, I found the concentrate of metals in some stages are zero at the same time. As they are the essential raw materials, their coefficients are crutial too, if their values are zero, it's impossible to calculate their coefficients. Therefore I decide to delete those rows with zero values.
    
    To address the missing values, if there are missing values in the target columns, I drop them directly. Otherwise, due to the whole gold recovery process is time series, I filled the missing values with the pervious time.
    

* Analyze the data

    I'm confused with the question of comparing the feed size distributions. I proposed a hypothesis and calculated they are not the same mean values or distribution. If they are not belong to the same distribution, I should generate new train and test sets from the full dataset. But it conflict with the project instruction. It will be appreciated if you could give me some advice.
    

* Build the model and calculate the sMAPE metric

    The most challenge is how to deal with two targets. I designed an experiment that divide the targets into two seperate stages. 
    
    In the Rougher stage, I chose the features before the `rougher.output.recovery` was generated and train a model. Then I saved the prediction of `rougher.output.recovery` for the next stage. 
    
    In the final stage, I used all features but replace the `rougher.output.recovery` with the predicted values.
    
    I applied the cross validation approach to choose the best model from 4 regression models. Unexpectedly, the simplest one, the linear regression, was the winner.
    
    Finally, I calculated the combined sMAPE score. It showed the model was not good enough.
    

* Future optimization plan


    * Fine tuning the models. Although the linear regression is the best model through the cross validation selection, it performed worse than Randome Forest and XGBoot when abandoned the cross validation. A better model selection method or fine tuning the hyperparameters might work for the metrics.
    
    * Time series models. I should consider the whole process as assembly line. The parameters of a certian hour should affect the target from subsequent hours rather than the same hour (row). Therefore a time series solution might be better. 
    
    * Feature engineering. There are some optimization options on feature engineering, such as fill missing values with the mean or median, check the correlationship between features.