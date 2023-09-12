# Project description

The supermarket chain Good Seed would like to explore whether Data Science can help them adhere to alcohol laws by making sure they do not sell alcohol to people underage. You are asked to conduct that evaluation, so as you set to work, keep the following in mind:
* The shops are equipped with cameras in the checkout area which are triggered when a person is buying alcohol
* Computer vision methods can be used to determine age of a person from a photo
* The task then is to build and evaluate a model for verifying people's age
To start working on the task, you'll have a set of photographs of people with their ages indicated.

# Project process

1. Perform exploratory data analysis to get an overall impression of the dataset.
2. Train and evaluate the model (it needs to be done on the GPU platform).
3. Combine your code, output and findings (from the previous points) in the final Jupyter notebook.
4. Make conclusions of the model evaluation, add them to the notebook.
5. Build and train a convolutional neural network on the GPU platform, using the dataset with photos of people. Get the MAE score for the test set no higher than 8.

# Conclusions

I've implemented a ResNet50 model with the pretrained hyperparameters as the backbone, then added an average pooling layer plus a fully connection layer. Next I used the Adam optimizer and set the learning rate to 0.0001.

For the training process, after the 4th epoch, the MAE metric on the validation set was dramaticly improved from 22.54 to 8.35. When finished 20 epochs training, the MAE on the validation set was as low as 5.85. Finally the MAE score on the test set was 5.85 too, it met the project reqirement.