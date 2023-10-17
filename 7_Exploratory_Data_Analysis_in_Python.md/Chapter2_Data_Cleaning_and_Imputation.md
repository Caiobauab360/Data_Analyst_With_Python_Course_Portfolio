# Data Cleaning and Imputation

**Description:**

Exploring and analyzing data often means dealing with missing values, incorrect data types, and outliers. In this chapter, you’ll learn techniques to handle these issues and streamline your EDA processes!


# Addressing missing data

**Personal notes**

Missing data can hinder the results of an analysis and may affect distributions, reduce the representation of the population, and lead to incorrect conclusions.

Looking for missing values:

- `print(dataframe.isna().sum())` - You can use `isna` along with `sum` to find the missing values for each column in the dataframe.

Strategies for dealing with missing values:

A practical rule is to remove observations if they account for five percent or less of all values. If there are more missing values, they can be replaced with a summary statistic such as the mean, median, or mode, depending on the context. This is known as imputation. Alternatively, imputation can be performed by subgroups.

In the example used in class, using data from a company, we observed that the average salary varies according to experience, so we could impute different salaries depending on experience.

- `threshold = len(salaries) * 0.05` - To calculate our threshold for missing values, we multiply the length of our dataframe by 5%, giving an upper limit of 30.

- `cols_to_drop = salaries.columns[salaries.isna().sum() <= threshold]` - Using boolean indexing to filter columns with missing values less than or equal to this threshold, storing them as a variable called `cols_to_drop`.

- `salaries.dropna(subset=cols_to_drop, inplace=True)` - We discard the missing values by calling `.dropna`, passing `cols_to_drop` to the subset argument. Setting `inplace` as True, to update the dataframe.

- `cols_with_missing_values = salaries.columns[salaries.isna().sum() > 0]` - Next, we filter the remaining columns with missing values.

- ```python
  for col in cols_with_missing_values[:-1]:
      salaries[col].fillna(salaries[col].mode()[0])
  ```

  To impute the mode for the first three columns, we iterate through them and call the `.fillna` method, passing the mode of the respective column and indexing the first item, which contains the mode, in square brackets.

Imputing by subgroups:

- `salaries_dict = salaries.groupby("Experience")["salary_usd"].median().to_dict()` - We will impute the median salary by level of experience and calculate the median. The `.to_dict` method stores the grouped data as a dictionary containing the median salary for each level of experience.

- `salaries["salaries_USD"] = salaries["Salary_USD"].fillna(salaries["Experience"].map(salaries_dict))` - Then, we impute using `.fillna`, providing the Experience column and calling `.map`, within which we pass the salary dictionary.

**Exercises:**

**Dealing with missing data**

It is important to deal with missing data before starting your analysis.

One approach is to drop missing values if they account for a small proportion, typically five percent, of your data.

Working with a dataset on plane ticket prices, stored as a pandas DataFrame called planes, you'll need to count the number of missing values across all columns, calculate five percent of all values, use this threshold to remove observations, and check how many missing values remain in the dataset.

Instructions:

-Print the number of missing values in each column of the DataFrame.

-Calculate how many observations five percent of the planes DataFrame is equal to.

-Create cols_to_drop by applying boolean indexing to columns of the DataFrame with missing values less than or equal to the threshold.

-Use this filter to remove missing values and save the updated DataFrame.

    # Count the number of missing values in each column
    print(planes.isna().sum())

    # Find the five percent threshold
    threshold = len(planes) * 0.05

    # Create a filter
    cols_to_drop = planes.columns[planes.isna().sum() <= threshold]

    # Drop missing values for columns below the threshold
    planes.dropna(subset=cols_to_drop, inplace=True)

    print(planes.isna().sum())

**Strategies for remaining missing data**

The five percent rule has worked nicely for your planes dataset, eliminating missing values from nine out of 11 columns!

Now, you need to decide what to do with the "Additional_Info" and "Price" columns, which are missing 300 and 368 values respectively.

You'll first take a look at what "Additional_Info" contains, then visualize the price of plane tickets by different airlines.

The following imports have been made for you:

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

Instructions:

-Print the values and frequencies of "Additional_Info".

-Create a boxplot of "Price" by "Airline".

    # Check the values of the Additional_Info column
    print(planes["Additional_Info"].value_counts())

    # Create a box plot of Price by Airline
    sns.boxplot(data=planes, x="Airline", y="Price")

    plt.show()

![Image101](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/609307b2-1e3d-44bc-8580-643c235ae723)

**Imputing missing plane prices**

Now there's just one column with missing values left!

You've removed the "Additional_Info" column from planes—the last step is to impute the missing data in the "Price" column of the dataset.

Instructions:

-Group planes by airline and calculate the median price.

-Convert the grouped median prices to a dictionary.

    # Calculate median plane ticket prices by Airline
    airline_prices = planes.groupby("Airline")["Price"].median()

    print(airline_prices)

    # Convert to a dictionary
    prices_dict = planes.groupby("Airline")["Price"].median().to_dict()

-Conditionally impute missing values for "Price" by mapping values in the "Airline column" based on prices_dict.

-Check for remaining missing values.

    # Calculate median plane ticket prices by Airline
    airline_prices = planes.groupby("Airline")["Price"].median()

    print(airline_prices)

    # Convert to a dictionary
    prices_dict = airline_prices.to_dict()

    # Map the dictionary to missing values of Price by Airline
    planes["Price"] = planes["Price"].fillna(planes["Airline"].map(prices_dict))

    # Check for missing values
    print(planes.isna().sum())

# Converting and analyzing categorical data

**Personal notes**

As seen previously, using `select_dtypes()`, we can filter any non-numeric data.

- `print(salaries.select_dtypes("object").head())`
- `print(salaries["Designation"].value_counts())` - To examine the frequency of values in the "Designation" column.
- `print(salaries["Designation"].nunique())` - To count how many unique job titles exist within the "Designation" column using `.nunique()`.

Extracting values from categories:

- `pandas.Series.str.contains()` - We can use this pandas method, which allows us to search a column for a specific string or multiple strings.
- `salaries["Designation"].str.contains("Scientist")` - In this case, it is searching for which job titles contain "Scientist," returning a dataframe with True and False for each row.

Finding multiple phrases in strings:

- `salaries["Designation"].str.contains("Machine learning|AI")` - Using the same method but separating the phrases with a pipe symbol `|` (left-shift + backslash). You cannot include spaces before or after the pipe, as it will cause the search to include the space.
- `salaries["Designation"].str.contains("^Data")` - The `^` symbol is used to indicate that we are looking for the word "Data" at the beginning of the string. So in this case, it would be True for "Data Scientist" but False for "Big Data Engineer."

You can use a list to find different categories of data, step by step:

```python
job_categories = ["Data Science", "Data Analytics", "Data Engineering", "Machine Learning", "Managerial", "Consultant"]
```

Create variables containing the filters needed:

```python
data_science = "Data Scientist|NLP"
data_analyst = "Analyst|Analytics"
data_engineer = "Data Engineer|ETL|Architect|Infrastructure"
ml_engineer = "Machine Learning|ML|Big Data|AI"
manager = "Manager|Head|Director|Lead|Principal|Staff"
consultant = "Consultant|Freelance"
```

The next step is to create a list with all the conditions to use with the `str.contains()` method using the variables created earlier:

```python
conditions = [
    (salaries["Designation"].str.contains(data_science)), 
    (salaries["Designation"].str.contains(data_analyst)),
    (salaries["Designation"].str.contains(data_engineer)),
    (salaries["Designation"].str.contains(ml_engineer)),
    (salaries["Designation"].str.contains(manager)),
    (salaries["Designation"].str.contains(consultant))
]
```

Finally, we can create the new column:

- `salaries["Job_Category"] = np.select(conditions, job_categories, default="Other")` - We create a new column called "Job_Category" using the `np.select` function. The first argument is a list of conditions, followed by a list of arrays where the search will be performed according to the specified conditions, and the `default` argument will determine "Other" for any value that does not fit the condition.

To visualize the frequency of each category, a countplot can be created:

- `sns.countplot(data=salaries, x="Job_Category")`

**Exercises:**

**Finding the number of unique values**

You would like to practice some of the categorical data manipulation and analysis skills that you've just seen. To help identify which data could be reformatted to extract value, you are going to find out which non-numeric columns in the planes dataset have a large number of unique values.

pandas has been imported for you as pd, and the dataset has been stored as planes.

Instructions:

-Filter planes for columns that are of "object" data type.

-Loop through the columns in the dataset.

-Add the column iterator to the print statement, then call the function to return the number of unique values in the column.

    # Filter the DataFrame for object columns
    non_numeric = planes.select_dtypes("object")

    # Loop through columns
    for column_name in non_numeric.columns:
  
      # Print the number of unique values
      print(f"Number of unique values in {column_name} column: ", non_numeric[column_name].nunique())

**Flight duration categories**

As you saw, there are 362 unique values in the "Duration" column of planes. Calling planes["Duration"].head(), we see the following values:

0        19h

1     5h 25m

2     4h 45m

3     2h 25m

4    15h 30m

Name: Duration, dtype: object

Looks like this won't be simple to convert to numbers. However, you could categorize flights by duration and examine the frequency of different flight lengths!

You'll create a "Duration_Category" column in the planes DataFrame. Before you can do this you'll need to create a list of the values you would like to insert into the DataFrame, followed by the existing values that these should be created from.

Instructions:

-Create a list of categories containing "Short-haul", "Medium", and "Long-haul".

-Create short_flights, a string to capture values of "0h", "1h", "2h", "3h", or "4h" taking care to avoid values such as "10h".

-Create medium_flights to capture any values between five and nine hours.

-Create long_flights to capture any values from 10 hours to 16 hours inclusive.

    # Create a list of categories
    flight_categories = ["Short-haul", "Medium", "Long-haul"]

    # Create short_flights
    short_flights = "^0h|^1h|^2h|^3h|^4h"

    # Create medium_flights
    medium_flights = "^5h|^6h|^7h|^8h|^9h"

    # Create long_flights
    long_flights = "10h|11h|12h|13h|14h|15h|16h"
  
**Adding duration categories**

Now that you've set up the categories and values you want to capture, it's time to build a new column to analyze the frequency of flights by duration!

The variables flight_categories, short_flights, medium_flights, and long_flights that you previously created are available to you.

Additionally, the following packages have been imported: pandas as pd, numpy as np, seaborn as sns, and matplotlib.pyplot as plt.

-Create conditions, a list containing subsets of planes["Duration"] based on short_flights, medium_flights, and long_flights.

-Create the "Duration_Category" column by calling a function that accepts your conditions list and flight_categories, setting values not found to "Extreme duration".

-Create a plot showing the count of each category.

    # Create conditions for values in flight_categories to be created
      conditions = [
        (planes["Duration"].str.contains(short_flights)),
        (planes["Duration"].str.contains(medium_flights)),
        (planes["Duration"].str.contains(long_flights))
        ]

    # Apply the conditions list to the flight_categories
    planes["Duration_Category"] = np.select(conditions, 
                                        flight_categories,
                                        default="Extreme duration")

    # Plot the counts of each category
    sns.countplot(data=planes, x="Duration_Category")
    plt.show()

![Image102](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d4c8a7ac-a0cd-4c25-85f1-ce721918644b)

# Working with numeric data

**Personal notes**

Converting strings to numbers - In the example used in the class, the salary column is in Indian Rupees, so we need to convert it to US Dollars. First, we need to remove the commas present in the column. Then, change the data type to float. Finally, we need to create a new column converting the currency value.

- `salaries["Salary_In_Rupees"] = salaries["Salary_In_Rupees"].str.replace(",", " ")` - This replaces all commas in the column with spaces, effectively removing the commas.

- `salaries["Salary_In_Rupees"] = salaries["Salary_In_Rupees"].astype(float)` - This changes the values in the column to the float data type.

- `salaries["Salary_USD"] = salaries["Salary_In_Rupees"] * 0.012` - This creates a new column and converts the values in the Rupees column to the Dollar value.

Creating a new column containing statistical data about the dataframe:

- `salaries["std_dev"] = salaries.groupby("Experience")["Salary_USD"].transform(lambda x: x.std())` - This creates a new column containing the standard deviation of "Salary_USD," where the values are conditional based on the "Experience" column.

We can select more than one column and use the `value_counts()` method:

- `print(salaries[["Experience", "std_dev"]].value_counts())` - It will print the combinations of values for the chosen columns, in this case, "Experience" and "std_dev."

**Exercises:**

**Flight duration**

You would like to analyze the duration of flights, but unfortunately, the "Duration" column in the planes DataFrame currently contains string values.

You'll need to clean the column and convert it to the correct data type for analysis.

Instructions:

-Print the first five values of the "Duration" column.

-Remove "h" from the column.

-Convert the column to float data type.

-Plot a histogram of "Duration" values.

    # Preview the column
    print(planes["Duration"].head())

    # Remove the string character
    planes["Duration"] = planes["Duration"].str.replace("h", "")

    # Convert to float data type
    planes["Duration"] = planes["Duration"].astype(float)

    # Plot a histogram
    sns.histplot(data=planes, x="Duration")
    plt.show()

![Image103](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/044a3c8a-3c23-4a2c-ab6c-322478489a7c)

**Adding descriptive statistics**

Now "Duration" and "Price" both contain numeric values in the planes DataFrame, you would like to calculate summary statistics for them that are conditional on values in other columns.

Instructions:

-Add a column to planes containing the standard deviation of "Price" based on "Airline".

    # Price standard deviation by Airline
    planes["airline_price_st_dev"] = planes.groupby("Airline")["Price"].transform(lambda x: x.std())

    print(planes[["Airline", "airline_price_st_dev"]].value_counts())

-Calculate the median for "Duration" by "Airline", storing it as a column called "airline_median_duration".

    # Median Duration by Airline
    planes["airline_median_duration"] = planes.groupby("Airline")["Duration"].transform(lambda x: x.median())

    print(planes[["Airline","airline_median_duration"]].value_counts())

-Find the mean "Price" by "Destination", saving it as a column called "price_destination_mean".

    # Mean Price by Destination
    planes["price_destination_mean"] = planes.groupby("Destination")["Price"].transform(lambda x: x.mean())

    print(planes[["Destination","price_destination_mean"]].value_counts())

# Handling outliers

**Personal notes**

An outlier is an observation that is significantly different from other data points. Using the `.describe` method, we can compare statistics to identify outliers. Outliers are extreme values and may not accurately represent the data. Furthermore, they can distort the mean and standard deviation. If we plan to perform statistical tests or build machine learning models, they generally require data that is normally distributed and not distorted.

We can define an outlier mathematically:

First, we need to know the interquartile range, or IQR, which is the difference between the 75th and 25th percentiles. Remember that these percentiles are included in the Box Plot as diamond-shaped points outside the box.

Once we have the IQR, we can find an upper outlier by looking for values above the sum of the 75th percentile + 1.5 times the IQR. A lower outlier has values below the sum of the 25th percentile - 1.5 times the IQR.

- `seventy_fifth = salaries["Salary_USD"].quantile(0.75)` - We can calculate the percentiles using the `.quantile` method, using 0.75 to find the 75th percentile.
- `twenty_fifth = salaries["Salary_USD"].quantile(0.25)` - To calculate the 25th percentile.
- `salaries_iqr = seventy_fifth - twenty_fifth` - To calculate the IQR, subtract the 75th percentile from the 25th percentile.

Finding outliers:

- `upper = seventy_fifth + (1.5 * salaries_iqr)` - For upper outliers.
- `lower = twenty_fifth - (1.5 * salaries_iqr)` - For lower outliers.
- `salaries[(salaries["Salary_USD"] < lower) | (salaries["Salary_USD"] > upper)]`

We can remove outliers:

- `no_outliers = salaries[(salaries["Salary_USD"] >= lower) & (salaries["Salary_USD"] <= upper)]`

**Exercises:**

**Identifying outliers**

You've proven that you recognize what to do when presented with outliers, but can you identify them using visualizations?

Try to figure out if there are outliers in the "Price" or "Duration" columns of the planes DataFrame.

matplotlib.pyplot and seaborn have been imported for you as plt and sns respectively.

Instructions:

-Plot the distribution of "Price" column from planes.

-Display the descriptive statistics for flight duration.

    # Plot a histogram of flight prices
    sns.histplot(data=planes, x="Price")
    plt.show()

    # Display descriptive statistics for flight duration
    print(planes["Duration"].describe())

![Image104](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/93802668-e35e-45ec-80ba-c0272de2d053)

**Removing outliers**

While removing outliers isn't always the way to go, for your analysis, you've decided that you will only include flights where the "Price" is not an outlier.

Therefore, you need to find the upper threshold and then use it to remove values above this from the planes DataFrame.

pandas has been imported for you as pd, along with seaborn as sns

Instructions:

-Find the 75th and 25th percentiles, saving as price_seventy_fifth and price_twenty_fifth respectively.

-Calculate the IQR, storing it as prices_iqr.

-Calculate the upper and lower outlier thresholds.

-Remove the outliers from planes.

    # Find the 75th and 25th percentiles
    price_seventy_fifth = planes["Price"].quantile(0.75)
    price_twenty_fifth = planes["Price"].quantile(0.25)

    # Calculate iqr
    prices_iqr = price_seventy_fifth - price_twenty_fifth

    # Calculate the thresholds
    upper = price_seventy_fifth + (1.5 * prices_iqr)
    lower = price_twenty_fifth - (1.5 * prices_iqr)

    # Subset the data
    planes = planes[(planes["Price"] > lower) & (planes["Price"] < upper)]

    print(planes["Price"].describe())
