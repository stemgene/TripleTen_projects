# Project description

You work as an analyst for the telecom operator Megaline. The company offers its clients two prepaid plans, Surf and Ultimate. The commercial department wants to know which of the plans brings in more revenue in order to adjust the advertising budget.

You are going to carry out a preliminary analysis of the plans based on a relatively small client selection. You'll have the data on 500 Megaline clients: who the clients are, where they're from, which plan they use, and the number of calls they made and text messages they sent in 2018. Your job is to analyze clients' behavior and determine which prepaid plan brings in more revenue.

# Description of the plans

Note: Megaline rounds seconds up to minutes, and megabytes to gigabytes. For calls, each individual call is rounded up: even if the call lasted just one second, it will be counted as one minute. For web traffic, individual web sessions are not rounded up. Instead, the total for the month is rounded up. If someone uses 1025 megabytes this month, they will be charged for 2 gigabytes.

**Surf**

1. Monthly charge: $20
2. 500 monthly minutes, 50 texts, and 15 GB of data
3. After exceeding the package limits:
    * 1 minute: 3 cents
    * 1 text message: 3 cents
    * 1 GB of data: $10

**Ultimate**

1. Monthly charge: $70
2. 3000 monthly minutes, 1000 text messages, and 30 GB of data
3. After exceeding the package limits:
    * 1 minute: 1 cent
    * 1 text message: 1 cent
    * 1 GB of data: $7

# Project process

## Step 1: Prepare the data

* Convert the data to the necessary types
* Find and eliminate errors in the data

Explain what errors you found and how you removed them.

For each user, find:
* The number of calls made and minutes used per month
* The number of text messages sent per month
* The volume of data per month
* The monthly revenue from each user (subtract the free package limit from the total number of calls, text messages, and data; multiply the result by the calling plan value; add the monthly charge depending on the calling plan)

## Step 2: Analyze the data

Describe the customers' behavior. Find the minutes, texts, and volume of data the users of each plan require per month. Calculate the mean, variance, and standard deviation. Plot histograms. Describe the distributions.

## Step 3: Test the hypotheses

* The average revenue from users of Ultimate and Surf calling plans differs.
* The average revenue from users in NY-NJ area is different from that of the users from other regions.

Decide what alpha value to use.

# General conclusion

[List your important conclusions in this final section, make sure they cover all those important decisions (assumptions) that you've made and that led you to the way you processed and analyzed the data.]

## Data Description and Preprocessing

There are 5 tables. The 'users' table contains user's demographics and plan information. The 'calls', 'messages', and 'internet' tables contain users' behavior. The 'plans' table shows detailed prices and provided services of two plans.

The general quality of data is good, although there are some columns need to be cleaned, e.g. some columns were transformed to appropriate data types, some columns need to be ceiled to integers, etc.

There is a considerable proportion of zero values in 'calls' and 'internet' tables. I assume the reason is users manipulate the phone in a flash that less than the minimum charging limit. According to someone's suggestion from Discord, I round those zero values up to 1. 

I also found 10 users didn't have any transactions, so I dropped them.

## Analysis 

After merging and aggregating users and their consumption behavior, I mainly compared three kinds of comsumption between two plans. 

There is tiny difference between calls and internet of two plans, they have similar distributions. For messages, the distribution of users from 'surf' plan is a right skew normal distribution, whereas the distribution of the 'ultimate' plan is more likely a uniform distribution.

There is significant difference of anvenue between two plans. The first reason, of course, is the monthly fix charge. But I found the users from 'ultimate' plan didn't have more consumption behavior than users of the 'surf' plan, they rarely touch the package limit. On the contrary, users from the 'surf' plan uaually exceed the plan limit and be charged by individual call or extra data traffic.

Both distributions are more likely to Pareto principle, i.e.80-20 rule. That means the most of user renvenues equal to the monthly fix charge of each plan and gather in a certain range which greater than monthly fix charge. For the 'surf' plan, although the monthly fix charge is only 20, there is 75% users spend a range between 20 to 72.5. For the 'ultimate' plan, the users who only spend monthly fix charge are dominant (more than 75%), so that the mean is only 71.82 with a samll std 7.42.

## Hypothesis Test

Finally I proposed two hypothese to test if there are anvenue diffences between two plans and between two areas. 

For user anvenue between two plans, there is a significant difference to prove they are not same.

For user anvenue in two areas, there isn't a significant evidence to show diffence.

## Suggestions for two plans

Obviously, the 'ultimate' plan brings more average anvenue per person than the 'surf' plan. However, the users from the 'ultimate' plan don't show enthusiasm of uasge corresponding to the abundant free service. Conversely, many users from the 'surf' plan exceed the package limit and have to pay extra. Those are not reasonable. As the time goes by, customers tend to churn.

I have two suggestions. 
1. Encourage customers in the ultimate plan to use more free services in order to increase the loyalty. At the same time, I suggest that the company should boost the 'ultimate' plan since it brings more revenue.

2. Increase the 'surf' plan service limit or create a new plan in the middle of two plans so that make more choices for users.

## Next Steps

I didn't have chance to use all information at this project. For example, the revenue would change or have different pattern based on the age groups or city of users. 

Another important indicator is the churn date. It can reflect which plan is more popular or friendly to users. Due to  very limited churn data, I cannot find any useful information.

Explain:
* How to formulated the null and alternative hypotheses.
* What criterion be used to test the hypotheses and why.
