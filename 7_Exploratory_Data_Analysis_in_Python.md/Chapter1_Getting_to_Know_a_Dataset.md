# Exploratory Data Analysis in Python

**Course Description**

So you’ve got some interesting data - where do you begin your analysis? This course will cover the process of exploring and analyzing data, from understanding what’s included in a dataset to incorporating exploration findings into a data science workflow.


Using data on unemployment figures and plane ticket prices, you’ll leverage Python to summarize and validate data, calculate, identify and replace missing values, and clean both numerical and categorical values. Throughout the course, you’ll create beautiful Seaborn visualizations to understand variables and their relationships.


For example, you’ll examine how alcohol use and student performance are related. Finally, the course will show how exploratory findings feed into data science workflows by creating new features, balancing categorical features, and generating hypotheses from findings.


By the end of this course, you’ll have the confidence to perform your own exploratory data analysis (EDA) in Python. You’ll be able to explain your findings visually to others and suggest the next steps for gathering insights from your data!

# Getting to Know a Dataset

**Description:**

What's the best way to approach a new dataset? Learn to validate and summarize categorical and numerical data and create Seaborn visualizations to communicate your findings.

# Initial exploration

**Personal notes**

Exploratory Data Analysis (EDA) is the process of examining and reviewing data with the aim of extracting insights, such as descriptive statistics and correlations, and generating hypotheses for experiments. The results of EDA often guide the next steps in data treatment, whether it's creating hypotheses, preparing data for use in machine learning models, or even discarding data and collecting new data.

*Importing a Dataset and Reviewing Useful Pandas Methods for Initial Exploration:*

- `books = pd.read_csv("books.csv")` - The first step is to import the dataset by creating a DataFrame.

- `books.head()` - This allows you to examine the columns present in the dataset.

- `books.info()` - It's a quick way to summarize the number of missing values in each column, the data type present in each column, and memory usage.

*To Discover the Amount of Data in Each Category in Categorical Columns within the Dataset:*

- `books.value_counts("genre")` - This helps determine how many values exist within the "genre" column.

- `books.describe()` - It provides a quick understanding of numerical data, including information such as mode, mean, and standard deviation.

*Visualizing Numeric Data:*

Histograms are a classic way to observe the distribution of numeric data by dividing numeric values into discrete bins and visualizing the count of values in each bin.

- `sns.histplot(data=books, x="rating")` - To create a histogram using Seaborn, use `.histplot`, set the dataset as `data`, and select one of the columns for the x-axis.

- `sns.histplot(data=books, x="rating", binwidth=1)` - This allows you to set the bin width to 1 using the `binwidth` parameter.

**Exercises:**

**Functions for initial exploration**

You are researching unemployment rates worldwide and have been given a new dataset to work with. The data has been saved and loaded for you as a pandas DataFrame called unemployment. You've never seen the data before, so your first task is to use a few pandas functions to learn about this new data.

pandas has been imported for you as pd.

Instructions:

-Use a pandas function to print the first five rows of the unemployment DataFrame.

        # Print the first five rows of unemployment
        print(unemployment.head())

-Use a pandas function to print a summary of column non-missing values and data types from the unemployment DataFrame.

        # Print a summary of non-missing values and data types in the unemployment DataFrame
        print(unemployment.info())

-Print the summary statistics (count, mean, standard deviation, min, max, and quartile values) of each numerical column in unemployment.

        # Print summary statistics for numerical columns in unemployment
        print(unemployment.describe())


**Counting categorical values**

Recall from the previous exercise that the unemployment DataFrame contains 182 rows of country data including country_code, country_name, continent, and unemployment percentages from 2010 through 2021.

You'd now like to explore the categorical data contained in unemployment to understand the data that it contains related to each continent.

The unemployment DataFrame has been loaded for you along with pandas as pd.

Instructions:

-Use a pandas function to count the values associated with each continent in the unemployment DataFrame.

        # Count the values associated with each continent in unemployment
        print(unemployment["continent"].value_counts())

**Global unemployment in 2021**

It's time to explore some of the numerical data in unemployment! What was typical unemployment in a given year? What was the minimum and maximum unemployment rate, and what did the distribution of the unemployment rates look like across the world? A histogram is a great way to get a sense of the answers to these questions.

Your task in this exercise is to create a histogram showing the distribution of global unemployment rates in 2021.

The unemployment DataFrame has been loaded for you along with pandas as pd.

Instructions:

-Import the required visualization libraries.

-Create a histogram of the distribution of 2021 unemployment percentages across all countries in unemployment; show a full percentage point in each bin.

        # Import the required visualization libraries
        import seaborn as sns
        import matplotlib.pyplot as plt

        #Create a histogram of 2021 unemployment; show a full percent in each bin
        sns.histplot(data=unemployment, x="2021", binwidth=1)
        plt.show()

![Image98](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/c0fcf878-ee8b-4e8e-ae76-3ef5ba3d96dd)

# Data validation

**Personal notes**

It's essential to understand whether the data types and data ranges are as expected before proceeding with our analysis.

- `books.dtypes` - This can be used in place of `.info` if you are only interested in the data types present in the dataset.

*Changing Data Types:*

- `books["year"] = books["year"].astype(int)` - The `.astype()` parameter can be used to change the "year" column to integer numbers. In the example, the "year" column was in float format. Inside `.astype()`, you can choose from:
   - String (str)
   - Integer (int)
   - Float (float)
   - Dictionary (dict)
   - List (list)
   - Boolean (bool)

*Validating Categorical Data:*

We can validate categorical data by comparing values in a column with a list of expected values using `.isin()`:

- `books["genre"].isin(["Fiction", "Non Fiction"])` - Checks if the values in the genre column are limited to "Fiction" and "Non Fiction" by passing these genres as a list of strings to `.isin`. The function returns a series of the same size and shape as the original but with True and False in place of the values, depending on whether the value from the original series was included in the list passed to `.isin`.

- `~books["genre"].isin(["Fiction", "Non Fiction"])` - Using the tilde operator at the beginning of the code will invert the True/False so that the function returns True if the value is not in the list passed to `.isin`.

- `books[books["genre"].isin(["Fiction", "Non Fiction"])].head()` - If you want to filter the DataFrame only for values that are in your list.

*Validating Numeric Data:*

- `books.select_dtypes("number").head()` - To select numeric data, use the `select_dtypes` method and pass "number" as an argument.

- `books["year"].min()` - If you want to know the range of years in the dataset. First, use `.min()`, and then you can use `.max()` in another code snippet.

- `sns.boxplot(data=books, x="year")` - You can create a box plot to discover the time range. It shows the boundaries of each quartile of annual data. The ends, the left vertical line indicating the minimum, and the right vertical line indicating the maximum.

- `sns.boxplot(data=books, x="year", y="genre")` - You can also visualize the year data grouped by a categorical variable, such as genre in the example, by setting the y-axis argument.

**Exercises:**

**Detecting data types**

A column has been changed in the unemployment DataFrame and it now has the wrong data type! This data type will stop you from performing effective exploration and analysis, so your task is to identify which column has the wrong data type and then fix it.

pandas has been imported as pd; unemployment is also available.

Instructions:

Question
Which of the columns below requires an update to its data type?

        country_name

-Update the data type of the 2019 column of unemployment to float.

-Print the dtypes of the unemployment DataFrame again to check that the data type has been updated!

        # Update the data type of the 2019 column to a float
        unemployment["2019"] = unemployment["2019"].astype(float)
        # Print the dtypes to check your work
        print(unemployment.dtypes)

**Validating continents**

Your colleague has informed you that the data on unemployment from countries in Oceania is not reliable, and you'd like to identify and exclude these countries from your unemployment data. The .isin() function can help with that!

Your task is to use .isin() to identify countries that are not in Oceania. These countries should return True while countries in Oceania should return False. This will set you up to use the results of .isin() to quickly filter out Oceania countries using Boolean indexing.

The unemployment DataFrame is available, and pandas has been imported as pd.

Instructions:

-Define a Series of Booleans describing whether or not each continent is outside of Oceania; call this Series not_oceania.

-Use Boolean indexing to print the unemployment DataFrame without any of the data related to countries in Oceania.

        # Define a Series describing whether each continent is outside of Oceania
        not_oceania = ~unemployment["continent"].isin(["Oceania"])

        # Print unemployment without records related to countries in Oceania
        print(unemployment[not_oceania])

**Validating range**

Now it's time to validate our numerical data. We saw in the previous lesson using .describe() that the largest unemployment rate during 2021 was nearly 34 percent, while the lowest was just above zero.

Your task in this exercise is to get much more detailed information about the range of unemployment data using Seaborn's boxplot, and you'll also visualize the range of unemployment rates in each continent to understand geographical range differences.

unemployment is available, and the following have been imported for you: Seaborn as sns, matplotlib.pyplot as plt, and pandas as pd

Instructions:

-Print the minimum and maximum unemployment rates, in that order, during 2021.

-Create a boxplot of 2021 unemployment rates, broken down by continent.

        # Print the minimum and maximum unemployment rates during 2021
        print(unemployment["2021"].min(), unemployment["2021"].max())

        # Create a boxplot of 2021 unemployment rates, broken down by continent
        sns.boxplot(data=unemployment, x="2021", y="continent")
        plt.show()

![Image99](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/643d7d3b-c5ec-4a20-994d-cd155d2eed50)

# Data summarization

**Personal notes**

We can further explore the characteristics of data subsets with the help of `.groupby()`, which groups data by a specific category, allowing users to chain an aggregation function like mean or count to describe the data within each group.

- `book.groupby("genre").mean()` - For instance, we can group book data by genre by passing the genre column's name to the `groupby` function. Then, using the aggregation function, in this case, `.mean`, to find the average value of the numeric columns for each genre.

Aggregation Functions:
- Sum: `.sum()`
- Count: `.count()`
- Minimum: `.min()`
- Maximum: `.max()`
- Variance: `.var()`
- Standard Deviation: `.std()`

The `.agg()` function allows us to apply these aggregation functions. By default, it aggregates data across all rows in a particular column and is usually used when we want to apply more than one function.

- `books.agg(["mean", "std"])` - In this example, we pass a list of aggregation functions to be applied, such as `.mean` and `.std`. It returns a DataFrame of aggregated results, and `.agg` applies the functions only to columns with numeric data in the DataFrame.

A dictionary can be used to specify which aggregation functions to apply to which columns:

- `books.agg({"rating": ["mean", "std"], "year": ["median"]}` - The keys of the dictionary are the columns to which aggregation should be applied, and each value is a list of specific aggregation functions to be applied to that column.

By combining `.agg()` with `.groupby()`, we can apply grouped data exploration.

- `books.groupby("genre").agg(
    - mean_rating=("rating", "mean"),
    - std_rating=("rating", "std"),
    - median_year=("year", "median")` - In this example, we want to show the mean and standard deviation of the rating for each book genre along with the median year. We can create named columns with our desired aggregations using the `.agg()` function and creating named tuples within it. Each named tuple should include a column name followed by the aggregation function to be applied to that column. The name of the tuple becomes the name of the resulting column.

Visualizing Categorical Summaries

We can display similar information visually using a barplot. In Seaborn, bar charts will automatically calculate the mean of a quantitative variable, such as rating, in grouped categorical data, like the genre category we're analyzing in the examples. Bar plots also show a 95% confidence interval for the mean as a vertical line at the top of each bar.

- `sns.barplot(data=books, x="genre", y="rating")`

**Exercises:**

**Summaries with .groupby() and .agg()**

In this exercise, you'll explore the means and standard deviations of the yearly unemployment data. First, you'll find means and standard deviations regardless of the continent to observe worldwide unemployment trends. Then, you'll check unemployment trends broken down by continent.

The unemployment DataFrame is available, and pandas has been imported as pd.

Instructions:

-Print the mean and standard deviation of the unemployment rates for each year.

-Print the mean and standard deviation of the unemployment rates for each year, grouped by continent.

        # Print the mean and standard deviation of rates by year
        print(unemployment.agg(["mean", "std"]))
    
        # Print yearly mean and standard deviation grouped by continent
        print(unemployment.groupby("continent").agg(["mean", "std"]))

**Named aggregations**

You've seen how .groupby() and .agg() can be combined to show summaries across categories. Sometimes, it's helpful to name new columns when aggregating so that it's clear in the code output what aggregations are being applied and where.

Your task is to create a DataFrame called continent_summary which shows a row for each continent. The DataFrame columns will contain the mean unemployment rate for each continent in 2021 as well as the standard deviation of the 2021 employment rate. And of course, you'll rename the columns so that their contents are clear!

The unemployment DataFrame is available, and pandas has been imported as pd.

Instructions:

-Create a column called mean_rate_2021 which shows the mean 2021 unemployment rate for each continent.

-Create a column called std_rate_2021 which shows the standard deviation of the 2021 unemployment rate for each continent.

        continent_summary = unemployment.groupby("continent").agg(
            # Create the mean_rate_2021 column
            mean_rate_2021 = ("2021", "mean"),
            # Create the std_rate_2021 column
            std_rate_2021 = ("2021", "std"),
        )
        print(continent_summary)

*Visualizing categorical summaries**

As you've learned in this chapter, Seaborn has many great visualizations for exploration, including a bar plot for displaying an aggregated average value by category of data.

In Seaborn, bar plots include a vertical bar indicating the 95% confidence interval for the categorical mean. Since confidence intervals are calculated using both the number of values and the variability of those values, they give a helpful indication of how much data can be relied upon.

Your task is to create a bar plot to visualize the means and confidence intervals of unemployment rates across the different continents.

unemployment is available, and the following have been imported for you: Seaborn as sns, matplotlib.pyplot as plt, and pandas as pd

Instructions:

-Create a bar plot showing continents on the x-axis and their respective average 2021 unemployment rates on the y-axis.

        # Create a bar plot of continents and their average unemployment
        sns.barplot(data=unemployment, x="continent", y="2021")
        plt.show()

![Image100](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/749d7711-50a6-4174-9a2b-8b1d6dd094bf)
