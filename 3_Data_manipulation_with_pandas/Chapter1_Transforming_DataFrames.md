# Data Manipulation with pandas course

**Course Description:**

pandas is the world's most popular Python library, used for everything from data manipulation to data analysis. In this course, you'll learn how to manipulate DataFrames, as you extract, filter, and transform real-world datasets for analysis. Using pandas you’ll explore all the core data science concepts. Using real-world data, including Walmart sales figures and global temperature time series, you’ll learn how to import, clean, calculate statistics, and create visualizations—using pandas to add to the power of Python!

# Transforming DataFrames

**Description:**

Let’s master the pandas basics. Learn how to inspect DataFrames and perform fundamental manipulations, including sorting rows, subsetting, and adding new columns.

#  Introducing DataFrames

**Personal Notes**

pandas is built on top of two major Python libraries, NumPy and Matplotlib. NumPy provides multidimensional array objects for efficient data manipulation, which pandas uses to store data. Matplotlib, on the other hand, offers powerful data visualization capabilities that pandas leverages.

Rectangular data is represented in pandas as DataFrames. Languages like R also have dataframes, and SQL has database tables.

Here are some commonly used DataFrame methods and attributes:

- `DataFrame.head()`: Returns the first few rows of the DataFrame.

- `DataFrame.info()`: Provides information about the DataFrame, including column names, data types, and whether there are any missing values.

- `DataFrame.shape`: Returns the number of rows and columns in the DataFrame.

- `DataFrame.describe()`: Calculates summary statistics for numeric columns, such as mean and median. "Count" indicates the number of missing values in each column.

- `DataFrame.values`: Contains the data values in a two-dimensional NumPy array.

- `DataFrame.columns`: Returns the names of the columns in the DataFrame.

- `DataFrame.index`: Returns either the number of rows or their names, depending on the index used.

Note that `DataFrame` in these methods and attributes represents the name of the variable assigned to a DataFrame object.

**Exercises:**

**Inspecting a DataFrame**

When you get a new DataFrame to work with, the first thing you need to do is explore it and see what it contains. There are several useful methods and attributes for this.

.head() returns the first few rows (the “head” of the DataFrame).

.info() shows information on each of the columns, such as the data type and number of missing values.

.shape returns the number of rows and columns of the DataFrame.

.describe() calculates a few summary statistics for each column.

homelessness is a DataFrame containing estimates of homelessness in each U.S. state in 2018. The individual column is the number of homeless individuals not part of a family with children. The family_members column is the number of homeless individuals part of a family with children. The state_pop column is the state's total population.

pandas is imported for you.

Instructions:

-Print the head of the homelessness DataFrame.

-Print information about the column types and missing values in homelessness.

-Print the number of rows and columns in homelessness.

-Print some summary statistics that describe the homelessness DataFrame.

    # Print the head of the homelessness data
    print(homelessness.head())

    # Print information about homelessness
    print(homelessness.info())

    # Print the shape of homelessness
    print(homelessness.shape)

    # Print a description of homelessness
    print(homelessness.describe())

**Parts of a DataFrame**

To better understand DataFrame objects, it's useful to know that they consist of three components, stored as attributes:

.values: A two-dimensional NumPy array of values.

.columns: An index of columns: the column names.

.index: An index for the rows: either row numbers or row names.

You can usually think of indexes as a list of strings or numbers, though the pandas Index data type allows for more sophisticated options. (These will be covered later in the course.)

homelessness is available.

Instructions:

-Import pandas using the alias pd.

-Print a 2D NumPy array of the values in homelessness.

-Print the column names of homelessness.

-Print the index of homelessness.

    # Import pandas using the alias pd
    import pandas as pd

    # Print the values of homelessness
    print(homelessness.values)

    # Print the column index of homelessness
    print(homelessness.columns)

    # Print the row index of homelessness
    print(homelessness.index)

# Sorting and subsetting

**Personal Notes**

Sorting involves changing the order of rows to arrange them in a specific way, often to bring more interesting data to the top of the DataFrame:

- `DataFrame.sort_values("weight_kg")`: This sorts the DataFrame by a specific column, such as "weight_kg," in ascending order by default. It rearranges the rows so that the lowest values in the "weight_kg" column are at the top of the DataFrame, followed by rows in increasing order of the selected column.

- `DataFrame.sort_values("weight_kg", ascending=False)`: This sorts the DataFrame in descending order, with the highest values in the "weight_kg" column at the top.

- `DataFrame.sort_values(["weight_kg", "height_cm"], ascending=[True, False])`: You can sort by multiple columns by providing a list of column names. You can also specify different sorting directions (ascending or descending) for each column.

Subsetting involves selecting specific rows or columns from a DataFrame:

- `DataFrame["weight_kg"]`: This returns only the specified column and its respective rows enclosed in brackets.

- `DataFrame[["weight_kg", "height_cm"]]`: To select multiple columns, use double brackets.

- `col_to_subset = ["weight_kg", "height_cm"]`: You can create a new variable to store specific columns that you want to work with.

- `DataFrame["weight_kg"] > 50`: To create a logical condition and find specific values in a column, this returns `True` and `False` for each row in the selected column, indicating which values meet the condition.

- `DataFrame[DataFrame["weight_kg"] > 50]`: To directly print the DataFrame with rows that satisfy a given condition.

- `DataFrame[DataFrame["breed"] == "Labrador"]`: You can use strings to filter rows based on specific criteria in a DataFrame.

- `DataFrame[DataFrame["date_of_birth"] < "2015-01-01"]`: To filter by date, use the international date format (year, month, day).

- To filter multiple values from a categorical variable, you can use the `.isin()` method.

**Exercises:**

**Sorting rows**

Finding interesting bits of data in a DataFrame is often easier if you change the order of the rows. You can sort the rows by passing a column name to .sort_values().

In cases where rows have the same value (this is common if you sort on a categorical variable), you may wish to break the ties by sorting on another column. You can sort on multiple columns in this way by passing a list of column names.

Sort on …	Syntax

one column	df.sort_values("breed")

multiple columns	df.sort_values(["breed", "weight_kg"])

By combining .sort_values() with .head(), you can answer questions in the form, "What are the top cases where…?".

homelessness is available and pandas is loaded as pd.

Instructions:

-Sort homelessness by the number of homeless individuals, from smallest to largest, and save this as homelessness_ind.

-Print the head of the sorted DataFrame.

    # Sort homelessness by individuals
    homelessness_ind = homelessness.sort_values("individuals")

    # Print the top few rows
    print(homelessness_ind.head())

-Sort homelessness by the number of homeless family_members in descending order, and save this as homelessness_fam.

-Print the head of the sorted DataFrame.

    # Sort homelessness by descending family members
    homelessness_fam = homelessness.sort_values("family_members", ascending = False)

    # Print the top few rows
    print(homelessness_fam.head())

-Sort homelessness first by region (ascending), and then by number of family members (descending). Save this as homelessness_reg_fam.

-Print the head of the sorted DataFrame.

    # Sort homelessness by region, then descending family members
    homelessness_reg_fam = homelessness.sort_values(["region", "family_members"], ascending = [True, False])

    # Print the top few rows
    print(homelessness_reg_fam.head())

**Subsetting columns**

When working with data, you may not need all of the variables in your dataset. Square brackets ([]) can be used to select only the columns that matter to you in an order that makes sense to you. To select only "col_a" of the DataFrame df, use

df["col_a"]

To select "col_a" and "col_b" of df, use

df[["col_a", "col_b"]]

homelessness is available and pandas is loaded as pd.

Instructions:

-Create a DataFrame called individuals that contains only the individuals column of homelessness.

-Print the head of the result.

    # Select the individuals column
    individuals = homelessness["individuals"]

    # Print the head of the result
    print(individuals.head())

-Create a DataFrame called state_fam that contains only the state and family_members columns of homelessness, in that order.

-Print the head of the result.

    # Select the state and family_members columns
    state_fam = homelessness[["state", "family_members"]]

    # Print the head of the result
    print(state_fam.head())

-Create a DataFrame called ind_state that contains the individuals and state columns of homelessness, in that order.

-Print the head of the result.

    # Select only the individuals and state columns, in that order
    ind_state = homelessness[["individuals", "state"]]

    # Print the head of the result
    print(ind_state.head())

**Subsetting rows**

A large part of data science is about finding which bits of your dataset are interesting. One of the simplest techniques for this is to find a subset of rows that match some criteria. This is sometimes known as filtering rows or selecting rows.

There are many ways to subset a DataFrame, perhaps the most common is to use relational operators to return True or False for each row, then pass that inside square brackets.

dogs[dogs["height_cm"] > 60]

dogs[dogs["color"] == "tan"]

You can filter for multiple conditions at once by using the "bitwise and" operator, &.

dogs[(dogs["height_cm"] > 60) & (dogs["color"] == "tan")]

homelessness is available and pandas is loaded as pd.

Instructions:

-Filter homelessness for cases where the number of individuals is greater than ten thousand, assigning to ind_gt_10k. View the printed result.

    # Filter for rows where individuals is greater than 10000
    ind_gt_10k = homelessness[homelessness["individuals"] > 10000]

    # See the result
    print(ind_gt_10k)

-Filter homelessness for cases where the USA Census region is "Mountain", assigning to mountain_reg. View the printed result.

    # Filter for rows where region is Mountain
    mountain_reg = homelessness[homelessness["region"] == "Mountain"]

    # See the result
    print(mountain_reg)

-Filter homelessness for cases where the number of family_members is less than one thousand and the region is "Pacific", assigning to fam_lt_1k_pac. View the printed result.

    # Filter for rows where family_members is less than 1000 
    # and region is Pacific
    fam_lt_1k_pac = homelessness[(homelessness["family_members"] < 1000) & (homelessness["region"] == "Pacific")]

    # See the result
    print(fam_lt_1k_pac)

**Subsetting rows by categorical variables**

Subsetting data based on a categorical variable often involves using the "or" operator (|) to select rows from multiple categories. This can get tedious when you want all states in one of three different regions, for example. Instead, use the .isin() method, which will allow you to tackle this problem by writing one condition instead of three separate ones.

colors = ["brown", "black", "tan"]

condition = dogs["color"].isin(colors)

dogs[condition]

homelessness is available and pandas is loaded as pd.

Instructions:

-Filter homelessness for cases where the USA census region is "South Atlantic" or it is "Mid-Atlantic", assigning to south_mid_atlantic. View the printed result.

    # Subset for rows in South Atlantic or Mid-Atlantic regions
    south_mid_atlantic = homelessness[(homelessness['region']=="South Atlantic") | (homelessness['region']=="Mid-Atlantic")]

    # See the result
    print(south_mid_atlantic)

-Filter homelessness for cases where the USA census state is in the list of Mojave states, canu, assigning to mojave_homelessness. View the printed result.

    # The Mojave Desert states
    canu = ["California", "Arizona", "Nevada", "Utah"]

    # Filter for rows in the Mojave Desert states
    mojave_homelessness = homelessness[homelessness['state'].isin(canu)]

    # See the result
    print(mojave_homelessness)

# New Columns

**Personal Notes**

`DataFrame["height_m"] = DataFrame["height_cm"] / 100` - This creates a new column called "height_m" by taking the values from the existing "height_cm" column and dividing each value by 100 to convert it to meters.

**Exercises:**

**Adding new columns**

You aren't stuck with just the data you are given. Instead, you can add new columns to a DataFrame. This has many names, such as transforming, mutating, and feature engineering.

You can create new columns from scratch, but it is also common to derive them from other columns, for example, by adding columns together or by changing their units.

homelessness is available and pandas is loaded as pd.

Instructions:

    # Add total col as sum of individuals and family_members
    homelessness["total"] = homelessness["individuals"] + homelessness["family_members"]

    # Add p_individuals col as proportion of total that are individuals
    homelessness["p_individuals"] = homelessness["individuals"] / homelessness["total"]

    # See the result
    print(homelessness)

**Combo-attack!**

You've seen the four most common types of data manipulation: sorting rows, subsetting columns, subsetting rows, and adding new columns. In a real-life data analysis, you can mix and match these four manipulations to answer a multitude of questions.

In this exercise, you'll answer the question, "Which state has the highest number of homeless individuals per 10,000 people in the state?" Combine your new pandas skills to find out.

Instructions:

-Add a column to homelessness, indiv_per_10k, containing the number of homeless individuals per ten thousand people in each state.

-Subset rows where indiv_per_10k is higher than 20, assigning to high_homelessness.

-Sort high_homelessness by descending indiv_per_10k, assigning to high_homelessness_srt.

-Select only the state and indiv_per_10k columns of high_homelessness_srt and save as result. Look at the result.

    # Create indiv_per_10k col as homeless individuals per 10k state pop
    homelessness["indiv_per_10k"] = 10000 * homelessness["individuals"] / homelessness["state_pop"] 

    # Subset rows for indiv_per_10k greater than 20
    high_homelessness = homelessness[homelessness["indiv_per_10k"] > 20]

    # Sort high_homelessness by descending indiv_per_10k
    high_homelessness_srt = high_homelessness.sort_values("indiv_per_10k", ascending=False)

    # From high_homelessness_srt, select the state and indiv_per_10k cols
    result = high_homelessness_srt[["state", "indiv_per_10k"]]

    # See the result
    print(result)
