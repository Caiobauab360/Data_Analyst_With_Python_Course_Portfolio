# Introduction to Statistics in Python

**Course description:**

Statistics is the study of how to collect, analyze, and draw conclusions from data. It’s a hugely valuable tool that you can use to bring the future into focus and infer the answer to tons of questions. For example, what is the likelihood of someone purchasing your product, how many calls will your support team receive, and how many jeans sizes should you manufacture to fit 95% of the population? In this course, you'll discover how to answer questions like these as you grow your statistical skills and learn how to calculate averages, use scatterplots to show the relationship between numeric values, and calculate correlation. You'll also tackle probability, the backbone of statistical reasoning, and learn how to use Python to conduct a well-designed study to draw your own conclusions from data.

# Summary Statistics

**Description:**

Summary statistics gives you the tools you need to boil down massive datasets to reveal the highlights. In this chapter, you'll explore summary statistics including mean, median, and standard deviation, and learn how to accurately interpret them. You'll also develop your critical thinking skills, allowing you to choose the best summary statistics for your data.

# What is statistics?

**Personal notes:**

Statistics is the practice and study of collecting and analyzing data. It can also refer to summary statistics, which are facts or summaries of some data, such as the mean or a count.

With its use, we can answer different questions such as:

- What is the probability of a person buying a particular product?

- Are people more likely to purchase it if they can use a different payment system?

- How many occupants will your hotel have? How to optimize occupancy?

- How many sizes of jeans need to be manufactured to fit 95% of the population?

- Should the same number of each size be produced?

- Which advertisement is most effective in persuading people to buy a product?

Descriptive Statistics and Inferential Statistics: Descriptive statistics focus on describing and summarizing the available data. Inferential statistics use the available data, which are called sample data, to make inferences about a larger population.

Types of Data: Numerical (quantitative) data consist of numeric values. Categorical (qualitative) data consist of values that belong to distinct groups.

Numerical data can be further divided into:

- Continuous data: These are usually measurable quantities, such as speed or time.

- Discrete data: These are typically count data, such as the number of pets or packages shipped.

Categorical data can be:

- Nominal: Comprised of categories with no inherent order, such as marital status or country of residence.

- Ordinal: Possess an inherent order, such as a survey question where you need to indicate the degree to which you agree with a statement.

- They can be represented by numbers, with each situation assigned a specific number.

*There are other types beyond these.

# Measures of center

**Personal notes:**

Summary statistics like mean and median are used to understand the central tendency of a dataset:

- Mean (np.mean): Calculated by summing all the numbers of interest and dividing by the total number of data points. It represents the "average" value of the dataset.

- Median (np.median): The value at which 50% of the data is smaller than it and 50% of the data is larger. It is the middle value when the data is arranged in ascending order.

- Mode: The mode is the most frequently occurring value in the dataset.

The choice between mean and median depends on the distribution of the data:

- Mean: More sensitive to extreme values (outliers), so it works well for symmetric data distributions.

- Median: Less affected by extreme values and is often preferred for skewed or non-normally distributed data.

These measures help provide a central value to understand where the data is concentrated. Depending on the characteristics of your dataset and the specific insights you're looking for, you may choose one of these measures to represent the central tendency.

**Exercises:**

**Mean and median**

In this chapter, you'll be working with the 2018 Food Carbon Footprint Index from nu3. The food_consumption dataset contains information about the kilograms of food consumed per person per year in each country in each food category (consumption) as well as information about the carbon footprint of that food category (co2_emissions) measured in kilograms of carbon dioxide, or CO2, per person per year in each country.

In this exercise, you'll compute measures of center to compare food consumption in the US and Belgium using your pandas and numpy skills.

pandas is imported as pd for you and food_consumption is pre-loaded.

Instructions:

-Import numpy with the alias np.

-Create two DataFrames: one that holds the rows of food_consumption for 'Belgium' and another that holds rows for 'USA'. Call these be_consumption and usa_consumption.

-Calculate the mean and median of kilograms of food consumed per person per year for both countries.

    # Import numpy with alias np
    import numpy as np

    # Filter for Belgium
    be_consumption = food_consumption[food_consumption["country"] == "Belgium"]

    # Filter for USA
    usa_consumption = food_consumption[food_consumption["country"] == "USA"]

    # Calculate mean and median consumption in Belgium
    print(np.mean(be_consumption["consumption"]))
    print(np.median(be_consumption["consumption"]))

    # Calculate mean and median consumption in USA
    print(np.mean(usa_consumption["consumption"]))
    print(np.median(usa_consumption["consumption"]))

-Subset food_consumption for rows with data about Belgium and the USA.

-Group the subsetted data by country and select only the consumption column.

-Calculate the mean and median of the kilograms of food consumed per person per year in each country using .agg().

    # Import numpy as np
    import numpy as np

    # Subset for Belgium and USA only
    be_and_usa = food_consumption[(food_consumption["country"] == "Belgium") | (food_consumption["country"] == "USA")]

    # Group by country, select consumption column, and compute mean and median
    print(be_and_usa.groupby("country")["consumption"].agg([np.mean, np.median]))

**Mean vs. median**

In the video, you learned that the mean is the sum of all the data points divided by the total number of data points, and the median is the middle value of the dataset where 50% of the data is less than the median, and 50% of the data is greater than the median. In this exercise, you'll compare these two measures of center.

pandas is loaded as pd, numpy is loaded as np, and food_consumption is available.

Instructions:

-Import matplotlib.pyplot with the alias plt.

-Subset food_consumption to get the rows where food_category is 'rice'.

-Create a histogram of co2_emission for rice and show the plot.

    # Import matplotlib.pyplot with alias plt
    import matplotlib.pyplot as plt

    # Subset for food_category equals rice
    rice_consumption = food_consumption[food_consumption['food_category'] == 'rice']
    # Histogram of co2_emission for rice and show plot
    rice_consumption['co2_emission'].hist();
    plt.show()

![Image41](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/ce01fa42-4b8d-40ae-a872-8206caab8c30)

-Use .agg() to calculate the mean and median of co2_emission for rice.

    # Subset for food_category equals rice
    rice_consumption = food_consumption[food_consumption['food_category'] == 'rice']

    # Calculate mean and median of co2_emission with .agg()
    print(rice_consumption['co2_emission'].agg([np.mean, np.median]))

# Measures of spread

**Personal notes:**

Spread describes how dispersed or closely grouped the data points are.

There are several different measures of spread, and one of the most common is variance. Variance measures the average distance of each data point from the mean of the data. To calculate variance, we start by computing the distance between each data point and the mean, resulting in a number for each data point. Next, we square each of these distances and then sum them all together. Finally, we divide the sum of the squared distances by the number of data points minus 1, giving us the variance. The larger the variance, the more spread out the data is.

For example, if you have a dataset of test scores, a high variance indicates that the scores are spread out across a wide range, while a low variance means that the scores are clustered closely around the mean.

Other measures of spread include the range (the difference between the maximum and minimum values) and the standard deviation, which is the square root of the variance and provides a measure of spread in the same units as the data. These measures help us understand the extent to which data points deviate from the central value and provide insights into the overall distribution of the data.

The standard deviation is another measure of spread, calculated as the square root of the variance. It can be calculated using `np.std`, specifying `ddof=1`. In the case of standard deviation, the units are typically easier to understand because they are not squared. Here's an example:

```python
import numpy as np

data = [12, 15, 18, 22, 25]

# Calculate the standard deviation with ddof=1
std_dev = np.std(data, ddof=1)

print("Standard Deviation:", std_dev)
```

In this example, we calculate the standard deviation of a dataset `data`, setting `ddof=1` to account for it being a sample rather than a full population.

The Mean Absolute Deviation (MAD) takes the absolute values of the differences from the mean and then calculates the average of these differences. It may seem similar to the standard deviation, but while the standard deviation squares the differences, making larger differences penalized more than shorter ones, the Mean Absolute Deviation penalizes each difference equally. The standard deviation is more commonly used.

Quantiles, also known as percentiles, divide the data into equal parts. You can use the `np.quantile()` function, followed by the desired percentile (e.g., `0.5` for the median). You can also pass a list of numbers to obtain multiple quantiles at once. Boxplots in the Matplotlib library represent quartiles. The bottom of the box is the first quartile, the top of the box is the third quartile, and the middle line is the second quartile or median.

You can use the `np.linspace()` function to achieve the same as in the previous example but more quickly. The Interquartile Range (IQR) is another measure of spread. It is the distance between the 25th percentile and the 75th percentile, which is also the height of the box in a boxplot. You can calculate it using the `np.quantile()` function or by using the `iqr` function from the `scipy.stats` library.

Outliers are data points that are substantially different from the others. To determine if a value is an outlier, a rule is commonly used: any data point that is smaller than the first quartile minus 1.5 times the IQR is an outlier, as well as any data point greater than the third quartile plus 1.5 times the IQR.

To find outliers, start by calculating the IQR, then compute the lower and upper bounds following the previously mentioned formulas.

Many of the summary statistics we've covered so far can be calculated in just one line of code using the `.describe()` method, which can be used when you want to get a general sense of your data.

**Exercises:**

**Quartiles, quantiles, and quintiles**

Quantiles are a great way of summarizing numerical data since they can be used to measure center and spread, as well as to get a sense of where a data point stands in relation to the rest of the data set. For example, you might want to give a discount to the 10% most active users on a website.

In this exercise, you'll calculate quartiles, quintiles, and deciles, which split up a dataset into 4, 5, and 10 pieces, respectively.

Both pandas as pd and numpy as np are loaded and food_consumption is available.

Instructions:

-Calculate the quartiles of the co2_emission column of food_consumption.

    # Calculate the quartiles of co2_emission
    print(np.quantile(food_consumption["co2_emission"], np.linspace(0, 1, 5)))

-Calculate the six quantiles that split up the data into 5 pieces (quintiles) of the co2_emission column of food_consumption.

    # Calculate the quintiles of co2_emission
    print(np.quantile(food_consumption["co2_emission"], np.linspace(0, 1, 6)))

-Calculate the eleven quantiles of co2_emission that split up the data into ten pieces (deciles).

    # Calculate the deciles of co2_emission
    print(np.quantile(food_consumption["co2_emission"], np.linspace(0, 1, 11)))

**Variance and standard deviation**

Variance and standard deviation are two of the most common ways to measure the spread of a variable, and you'll practice calculating these in this exercise. Spread is important since it can help inform expectations. For example, if a salesperson sells a mean of 20 products a day, but has a standard deviation of 10 products, there will probably be days where they sell 40 products, but also days where they only sell one or two. Information like this is important, especially when making predictions.

Both pandas as pd and numpy as np are loaded, and food_consumption is available.

Instructions:

-Calculate the variance and standard deviation of co2_emission for each food_category by grouping and aggregating.

-Import matplotlib.pyplot with alias plt.

-Create a histogram of co2_emission for the beef food_category and show the plot.

-Create a histogram of co2_emission for the eggs food_category and show the plot.

    # Print variance and sd of co2_emission for each food_category
    print(food_consumption.groupby("food_category")["co2_emission"].agg([np.var, np.std]))

    # Import matplotlib.pyplot with alias plt
    import matplotlib.pyplot as plt

    # Create histogram of co2_emission for food_category 'beef'
    food_consumption[food_consumption["food_category"]=="beef"]['co2_emission'].hist()
    # Show plot
    plt.show()

    # Create histogram of co2_emission for food_category 'eggs'
    food_consumption[food_consumption["food_category"]=="eggs"]['co2_emission'].hist()

    # Show plot
    plt.show()

![Image42](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/4bb2f8b2-442f-4339-9b2e-a867f633c107)

![Image43](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/9817c027-b163-475b-9ea9-1cf967ceeff0)

Finding outliers using IQR
Outliers can have big effects on statistics like mean, as well as statistics that rely on the mean, such as variance and standard deviation. Interquartile range, or IQR, is another way of measuring spread that's less influenced by outliers. IQR is also often used to find outliers. If a value is less than \text{Q1} - 1.5 \times \text{IQR} or greater than \text{Q3} + 1.5 \times \text{IQR}, it's considered an outlier. In fact, this is how the lengths of the whiskers in a matplotlib box plot are calculated.

In this exercise, you'll calculate IQR and use it to find some outliers. pandas as pd and numpy as np are loaded and food_consumption is available.

Instructions:

-Calculate the total co2_emission per country by grouping by country and taking the sum of co2_emission. Store the resulting DataFrame as emissions_by_country.

-Compute the first and third quartiles of emissions_by_country and store these as q1 and q3.

-Calculate the interquartile range of emissions_by_country and store it as iqr.

-Calculate the lower and upper cutoffs for outliers of emissions_by_country, and store these as lower and upper.

-Subset emissions_by_country to get countries with a total emission greater than the upper cutoff or a total emission less than the lower cutoff.

    # Calculate total co2_emission per country: emissions_by_country
    emissions_by_country = food_consumption.groupby('country')['co2_emission'].sum()

    # Compute the first and third quantiles and IQR of emissions_by_country
    q1 = np.quantile(emissions_by_country, 0.25)
    q3 = np.quantile(emissions_by_country, 0.75)
    iqr = q3 - q1

    # Calculate the lower and upper cutoffs for outliers
    lower = q1 - 1.5 * iqr
    upper = q3 + 1.5 * iqr

    # Subset emissions_by_country to find outliers
    outliers = emissions_by_country[(emissions_by_country > upper) | (emissions_by_country < lower)]
    print(outliers)

