---
layout: single
author_profile: true
title: Group Assignments
---

## Assignment 1 

### Project overview
Our overall objective is to support calculations of stafety stock values for individual SKU's. Assignment 1 focused on cleaning and transforming the dataset by standardizing column names, inspecting for anomalies, identifying and addressing missing values and extracting country informatiobn from manufacturing sites. We also created a separate cloumn containing the full name of each country.

#### Question 1
As you load and inspect your transaction dataframe, you'll notice the column names don't follow a consistent convention. Make the necessary changes to ensure all column names follow the same convention as the metadata.
![alt text](<Screenshot 2026-11-20 at 5.21.10 PM.png>)

#### Question 2
Inspect the numeric features of your dataframe with the describe function. Provide a summary of these features, and in case there are any oddities/anomalies in your dataframe, locate and correct them.  Please include a note on any oddities you find and a rationale for your suggested correction. You can do so by including a text note in a corresponding markdown shell.
![alt text](<Screenshot 2026-11-20 at 5.21.46 PM.png>)

#### Question 3
Your transactional dataset includes many missing values. Find and address (in your dataframe) the missing values by column. Again, remember to note the NaN values you found and provide a rationale for your suggested action.
![alt text](<Screenshot 2026-11-20 at 5.16.52 PM.png>)

#### Question 4
To apply broader breakdowns of your transactional dataset, it will be helpful to add a country column. Recall that the metadata indicates the country information is somewhat captured in the site column. Create a new country column by using the manufacturing_site information. To do so, you will need the helper function str.startswith() (here is a link to the official documentation), which is defined for a pandas Series object. As the documentation states, str.startswith() tests if the start of each string element matches a given pattern.
![alt text](<Screenshot 2026-11-20 at 5.18.49 PM.png>)

#### Question 5
It's time to focus on the subset of this dataset we need. Since we ultimately want to calculate safety stock, focus on finished goods designated as "make to stock." Create a filtered subset of your transaction dataset and write appropriate code to answer the following questions (for the filtered data).
![alt text](<Screenshot 2026-11-20 at 5.19.44 PM.png>)

### What we found
We found 612 unique SKU's after filtering for finsihed goods classified as make-to-stock. We identifed 19 known manufacturing sites and 54 known divisions. We found some lead-time anomalies and adjusted the values that appeared to have been multipied by 100. We identifed 40630 negative order quantities but retained the values because they could represent returns, cancellations or inventory adjustments. We labled missing classifications as unknown to preserve useful transactions. 

## Assignment 2
### Project overview
Assingment 2 is addressing a key part of inventory managment. There are many challenges in managing on-hand stock at appropriate levels. Because of unforseen challenges, such as supply chain disruptions, backorders, seasonal demand fluctuations, it is difficult to prevent stockouts. Saftey stock is what companies use to mitigate the risk of stockouts. Assignment 2 uses a formuala to evaluate the appropriate level of saftey stock. 

The analysis will focus on three objectives:

1. Transform the transaction dataset to calculate descriptive statistics for each eligible SKU.
2. Calculate safety stock at service levels of 75%, 90%, and 95%.
3. Identify the SKUs with the highest and lowest safety stock requirements and calculate the average safety stock.

#### Question 1
Create a transformed dataset to filter for appropriate SKUs that are also aggregated with the following statistics: minimum, maximum, average, median, variance, and standard deviation of quantity, along with average lead time.
![alt text](<Screenshot 2026-11-20 at 5.27.12 PM.png>)

#### Question 2
Calculate safety stock for each SKU using the standard deviation of order quantity, average lead time, and Z-scores corresponding to service levels of 75%, 90%, and 95%.
![alt text](<Screenshot 2026-11-20 at 5.28.19 PM.png>)

#### Question 3
For this question, we'll use the 95% service level to identify:
1. The SKU with the highest safety stock.
2. The SKU with the lowest safety stock.
3. The average safety stock across all SKUs.

![alt text](<Screenshot 2026-11-20 at 5.29.20 PM.png>)
![alt text](<Screenshot 2026-11-20 at 5.29.39 PM.png>)
![alt text](<Screenshot 2026-11-20 at 5.30.14 PM.png>)

#### Question 3 Results

At the 95% service level, SKU `53767219` had the highest safety stock requirement of 372.58 units, while SKU `9BC2A5C4` had the lowest at 52.37.

The average safety stock across all 482 SKUs was 141.61 units per SKU. With service level held constant, differences in saftey stock reflect differences in order quantity variability, average lead time, or both.
