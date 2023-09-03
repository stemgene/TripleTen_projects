# Project description
For this project, you’ll work with data from Instacart.

Instacart is a grocery delivery platform where customers can place a grocery order and have it delivered to them, similar to how Uber Eats and DoorDash work. This particular dataset was publicly released by Instacart in 2017 for a Kaggle competition. Although the original dataset is no longer available on the Instacart website, we’ve created CSV files that contain a modified version of that data. Download these files and use them for your project.

The dataset we've provided for you has been modified from the original. We've reduced the size of the dataset so that your calculations run faster and we’ve introduced missing and duplicate values. We were also careful to preserve the distributions of the original data when we made our changes.

Your mission is to clean up the data and prepare a report that gives insight into the shopping habits of Instacart customers. After answering each question, write a brief explanation of your results in a markdown cell of your Jupyter notebook.

This project will require you to make plots that communicate your results. Make sure that any plots you create have a title, labeled axes, and a legend if necessary; and include `plt.show()` at the end of each cell with a plot.

# General Conclusion:

There is high redundancy between these 3 data frames (top_20_product, top_20_reorder, and top_20_cart), we only use 27 products to cover all top lists. Especially top_20_product and top_20_reorder, they are almost the same except for one product even the order of purchase times, which shows the two have a strong positive correlationship. There are 6 products in top_20_cart which not in other data frames.

For specific products, the top 8 products (regular and organic) are banana, strawberry, baby spinach, avocado, lemon and lime, raspberry, onion and whole milk. 18 organic products out of total 27 products. Customers perfer hava a healthy life.
