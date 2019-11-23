![IronHack Logo](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_d5c5793015fec3be28a63c4fa3dd4d55.png)

# Project: Visualizing Real World Data

## Overview

The goal of this project is to practice creating and interpreting different types of visualizations using real world data.

## Assumption

France is still the best recognized and awarded country in terms of wine

### Wine_categories

The first step was uploading the data. It was on 2 csv-files, that is why I had to create two separate dataframes. Then I've concated them and dropped the duplicates. I've also dropped the rows, where either price or points were nulls, because these were my main variables and I wasn't willing to have any problems later.

After that I've added two additional columns in order to evaluate the wines: grades and ratio.
For grades I've defined a function, that evaluates the points column and depending on range returns the value from 0 to 5. For ratio, which represents dollar per point ratio, I've divided the column price by column points.

My starting point was to analyze the main numerical variables, such as points and price. I've decided to start with points and figured out, that they start from 80 and end at 100. They are also normaly distributed as I've seen by plotting histogram and boxplot.

Next was the price. Like average is 34.75, 75%-quantile is 40, but the maximum is 3300. Instead of dropping such outliers I've decided to split my dataframe into different ones based on the price. For this reason I've checked the top-25% using quantiles and after that top 1% using .001 range.
My splitting was based only on my personal assumption: luxury(above 800), very expensive(from 300 to 800), expensive(from 100 to 300), medium(from 40 to 100), low(from 25 to 40) and cheap(from 0 to 25).

I decided to look at the distribution of each category by plotting them using boxplot.

Going into each category I've decided to start with cheap category of wines.
Since I was interested in checking only the best rated wine, I've used only the best 2 available grades in each category as well as to use the countries only with significant frequency. In all categories this frequency was 100, while in very expensive and luxury 15 and 2 because of the small sample. Another criteria was to use only 25% since we are interested in spending less.

Unfortunately, these steps didn't help me to support my assumption, that is why I decided to create another notebook.

### us_vs_france_vs_italy_wine

This one was created in order to be able to identify the best country out of the top-3 provided by winefolly.com: France, Italy, the US. 

In our case, there are unequal samples of each of the countries, that is why it makes sense to check the relative percentage of each grade compared to all the grades received by this country.

The results obtained justified our assumption since France is a leader in grades 3, 4, 5.

## Additional research

### wine_words

Out of the curiousity I've decided to check what are the most frequent words used in description column.

For this case I've imported an additional package nltk. 

The first idea was to check all the descriptions. It turned out, that the most frequent one is 'wine'. What a surprise! 

Next step was to check the luxury versus cheap categories.

### top_wine

In order to be useful and keep my classmates engaged, I've decided to choose the best 3 from all categories and plot them. The choice was based on best grade available and 3 smalles ratios.