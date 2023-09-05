# Project description

You work for the online store Ice, which sells video games all over the world. User and expert reviews, genres, platforms (e.g. Xbox or PlayStation), and historical data on game sales are available from open sources. You need to identify patterns that determine whether a game succeeds or not. This will allow you to spot potential big winners and plan advertising campaigns.

In front of you is data going back to 2016. Let’s imagine that it’s December 2016 and you’re planning a campaign for 2017.

(The important thing is to get experience working with data. It doesn't really matter whether you're forecasting 2017 sales based on data from 2016 or 2017 sales based on data from 2016.)

The dataset contains the abbreviation ESRB. The Entertainment Software Rating Board evaluates a game's content and assigns an age rating such as Teen or Mature.

# Project steps:

## Step 1. Prepare the data
* Replace the column names (make them lowercase).
* Convert the data to the required types.
* Describe the columns where the data types have been changed and why.
* If necessary, decide how to deal with missing values:
  * Explain why you filled in the missing values as you did or why you decided to leave them blank.
  * Why do you think the values are missing? Give possible reasons.
* Pay attention to the abbreviation TBD (to be determined). Specify how you intend to handle such cases.
* Calculate the total sales (the sum of sales in all regions) for each game and put these values in a separate column.

## Step 2. Analyze the data
* Look at how many games were released in different years. Is the data for every period significant?
* Look at how sales varied from platform to platform. Choose the platforms with the greatest total sales and build a distribution based on data for each year. Find platforms that used to be popular but now have zero sales. How long does it generally take for new platforms to appear and old ones to fade?
* Determine what period you should take data for. To do so, look at your answers to the previous questions. The data should allow you to build a prognosis for 2017.
* Work only with the data that you've decided is relevant. Disregard the data for previous years.
* Which platforms are leading in sales? Which ones are growing or shrinking? Select several potentially profitable platforms.
* Build a box plot for the global sales of all games, broken down by platform. Are the differences in sales significant? What about average sales on various platforms? Describe your findings.
* Take a look at how user and professional reviews affect sales for one popular platform (you choose). Build a scatter plot and calculate the correlation between reviews and sales. Draw conclusions.
* Keeping your conclusions in mind, compare the sales of the same games on other platforms.
* Take a look at the general distribution of games by genre. What can we say about the most profitable genres? Can you generalize about genres with high and low sales?

## Step 3. Create a user profile for each region
For each region (NA, EU, JP), determine:
* The top five platforms. Describe variations in their market shares from region to region.
* The top five genres. Explain the difference.
* Do ESRB ratings affect sales in individual regions?

## Step 4. Test the following hypotheses:
* Average user ratings of the Xbox One and PC platforms are the same.
* Average user ratings for the Action and Sports genres are different.
Set the alpha threshold value yourself. Explain:
* How you formulate the null and alternative hypotheses
* What significance level you choose to test the hypotheses, and why

# Conclusion

During preprocessing, the biggest problem is there are many missing values in `name` and two scores. I extracted some missing names from WikiPedia by a web crawler script. Then I found `user_score` and `critic_score` had positive correlation, so I predicted partial missing values for each other. But the missing values still happen in `user_score`, `critic_score` and `rating` columns at the same time. I couldn't fill them rationally, therefore I left them with 'NA' or 'Unknown'.

Then I tried to analyze the relationship between columns.

* **Years of release:** There are three stages throughout the numbers of video games: beginning, peak stage and slump stage. The same situation happened in game platforms, the life period of them is about 10 years. To analyze and predict sales in 2017, I only need to care about the top 6 platforms which still release games in recent 5 years.

* **Platforms:** Among these 6 platforms, The 'PS4' has the greatest sale profits. For the means of platforms, "PS4" has the highest mean values. The platforms of '3DS', 'WiiU' and 'XOne' have similar mean values but less sales than 'PS4'.

* **Reviews:** Perfessional reviews make weak positive effect to sales, but user reviews don't affect sales.

* **Genres:** The most profitable genres are "Action", "Shooter", and "Role-Playing", they are more competitive. On the other hand, the genres of 'Puzzle', 'Adventrue' and 'Strategy' are more leisure with less pressure during playing, they have worst sales.

* **Regions:** Game sales in North America and Europe are homogeneous, they have same top 5 platforms, genres and ESRB rating. However, popular platforms, genres and rating are different in Japan market. Players like portable platforms and less competitive games.

At last I made two statistical inferences and proved the average user ratings of two platforms and two genres are different.

**Suggestions for games sales in 2017:**

In order to pursue potential profit, our stores should use different sale strategy in seperate marketing regions. 

In NA and EU regions, we need to give more marketing resources to "PC", "PS4", "3DS" and "XOne" platforms as well as 'Action', 'Shooter', 'Role-Playing', 'Sports' and 'Simulation' games.

On the other hand, in JP market, we need to pay more attention on "3DS", 'PSV', 'PS4' and 'WiiU', as well as 'Role-Playing' and 'Action' games. Additionally, the ESRB rating doesn't make siginifant effect on JP market, we can sale games without ESRB rating.

We still need to invite more professional reviews, since the critic scores will be helpful for game sales.
