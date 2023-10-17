# Turning Exploratory Analysis into Action

**Description:**

Exploratory data analysis is a crucial step in the data science workflow, but it isn't the end! Now it's time to learn techniques and considerations you can use to successfully move forward with your projects after you've finished exploring!

# Considerations for categorical data

**Personal notes**

Remember that Exploratory Data Analysis (EDA) is conducted for various reasons, such as pattern and relationship detection in data, generating questions or hypotheses, or preparing data for machine learning models. There is a requirement that our data must satisfy regardless of our plans after conducting EDA—it should be representative of the population we wish to study.

With categorical data, one of the most important considerations is about class representation, which is another term for labels.

Class Frequencies:
- `dataframe.value_counts()` - To perform frequency counting.
- `dataframe.value_counts(normalize=True)` - Will return relative frequencies for each class.

Another method to check class frequencies is cross-tabulation, which allows us to examine the frequency of combinations of classes.

- `pd.crosstab(planes["Source"], planes["Destination"])` - First, we use the `pd.crosstab()` function. Then, we select the column to be used as the index of the table, in this case, "Source." Next, we select which column provides the values that will become the column names in the table, and the values will be the count of combined observations.

We can calculate the average price for these routes in our DataFrame and compare the difference with these expected values. We do this by adding two keyword arguments inside the `crosstab`:

- `pd.crosstab(planes["Source"], planes["Destination"], values=planes["Price"], aggfunc="median")` - We pass the "Price" column to the `values` argument and use `aggfunc` to select the aggregate calculation we want to use. The results show median values for all possible routes in the dataset.

**Exercises:**

**Checking for class imbalance**

The 2022 Kaggle Survey captures information about data scientists' backgrounds, preferred technologies, and techniques. It is seen as an accurate view of what is happening in data science based on the volume and profile of responders.

Having looked at the job titles and categorized to align with our salaries DataFrame, you can see the following proportion of job categories in the Kaggle survey:

    Job Category	Relative Frequency
    Data Science	0.281236
    Data Analytics	0.224231
    Other	0.214609
    Managerial	0.121300
    Machine Learning	0.083248
    Data Engineering	0.075375

Thinking of the Kaggle survey results as the population, your task is to find out whether the salaries DataFrame is representative by comparing the relative frequency of job categories.

Instructions:

-Print the relative frequency of the "Job_Category" column from salaries DataFrame.

    # Print the relative frequency of Job_Category
    print(salaries["Job_Category"].value_counts(normalize=True))

**Cross-tabulation**

Cross-tabulation can help identify how observations occur in combination.

Using the salaries dataset, which has been imported as a pandas DataFrame, you'll perform cross-tabulation on multiple variables, including the use of aggregation, to see the relationship between "Company_Size" and other variables.

pandas has been imported for you as pd.

Instructions:

-Perform cross-tabulation, setting "Company_Size" as the index, and the columns to classes in "Experience".

    # Cross-tabulate Company_Size and Experience
    print(pd.crosstab(salaries["Company_Size"], salaries["Experience"]))

-Cross-tabulate "Job_Category" and classes of "Company_Size" as column names.

    # Cross-tabulate Job_Category and Company_Size
    print(pd.crosstab(salaries["Job_Category"], salaries["Company_Size"]))

-Update pd.crosstab() to return the mean "Salary_USD" values.

    # Cross-tabulate Job_Category and Company_Size
    print(pd.crosstab(salaries["Job_Category"], salaries["Company_Size"],
                values=salaries["Salary_USD"], aggfunc="mean"))

# Generating new features

**Personal notes**

The format of data can limit our ability to detect relationships or inhibit the potential performance of machine learning models. One method to overcome these issues is to generate new features from the data.

- `dt.weekday` - Can be used to indicate which day of the week a date falls on, generating numbers from 0 to 6 to represent the days of the week.

Descriptive Statistics:

In the example from the lesson, it's shown that you could use descriptive statistics to label flights by classes. First, you need to equally divide the price range using quartiles.

- `twenty_fifth = planes["Price"].quantile(0.25)` - First, store the 25th percentile using the `quantile` method.

- `median = planes["Price"].median()` - Obtain the median by calling the `median` function.

- `seventy_fifth = planes["Price"].quantile(0.75)` - Next, get the 75th percentile.

- `maximum = planes["Price"].max()` - Finally, store the maximum value.

The next step is to create the labels, in this case, the ticket types, and store them as a list:

- `labels = ["Economy", "Premium Economy", "Business Class", "First Class"]`

Then, create the bins, a list starting from zero and including the descriptive statistics variables created above:

- `bins = [0, twenty_fifth, median, seventy_fifth, maximum]`

- `planes["Price_Category"] = pd.cut(planes["Price"], labels=labels, bins=bins)` - Using the `pd.cut` function, pass the "Price" column, define the labels argument, and the bins argument. This reorganizes the dataframe by adding a column that indicates which of the classes, separated into labels, each row belongs to.

**Exercises:**

**Extracting features for correlation**

In this exercise, you'll work with a version of the salaries dataset containing a new column called "date_of_response".

The dataset has been read in as a pandas DataFrame, with "date_of_response" as a datetime data type.

Your task is to extract datetime attributes from this column and then create a heat map to visualize the correlation coefficients between variables.

Seaborn has been imported for you as sns, pandas as pd, and matplotlib.pyplot as plt.

Instructions:

-Extract the month from "date_of_response", storing it as a column called "month".

-Create the "weekday" column, containing the weekday that the participants completed the survey.

-Plot a heat map, including the Pearson correlation coefficient scores.

        # Get the month of the response
        salaries["month"] = salaries["date_of_response"].dt.month

        # Extract the weekday of the response
        salaries["weekday"] = salaries["date_of_response"].dt.weekday

        # Create a heatmap
        sns.heatmap(salaries.corr(), annot=True)
        plt.show()

![Image112](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/f0c65da1-b684-4c7b-9a3a-6d861c8acea9)

**Calculating salary percentiles**

In the video, you saw that the conversion of numeric data into categories sometimes makes it easier to identify patterns.

Your task is to convert the "Salary_USD" column into categories based on its percentiles. First, you need to find the percentiles and store them as variables.

pandas has been imported as pd and the salaries dataset read in as DataFrame called salaries.

Instructions:

-Find the 25th percentile of "Salary_USD".

-Store the median of "Salary_USD" as salaries_median.

-Get the 75th percentile of salaries.

    # Find the 25th percentile
    twenty_fifth = salaries["Salary_USD"].quantile(0.25)

    # Save the median
    salaries_median = salaries["Salary_USD"].median()

    # Gather the 75th percentile
    seventy_fifth = salaries["Salary_USD"].quantile(0.75)
    print(twenty_fifth, salaries_median, seventy_fifth)

**Categorizing salaries**

Now it's time to make a new category! You'll use the variables twenty_fifth, salaries_median, and seventy_fifth, that you created in the previous exercise, to split salaries into different labels.

The result will be a new column called "salary_level", which you'll incorporate into a visualization to analyze survey respondents' salary and at companies of different sizes.

pandas has been imported as pd, matplotlib.pyplot as plt, seaborn as sns, and the salaries dataset as a pandas DataFrame called salaries.

Instructions:

-Create salary_labels, a list containing "entry", "mid", "senior", and "exec".

-Finish salary_ranges, adding the 25th percentile, median, 75th percentile, and largest value from "Salary_USD".

-Split "Salary_USD" based on the labels and ranges you've created.

-Use sns.countplot() to visualize the count of "Company_Size", factoring salary level labels.

    # Create salary labels
    salary_labels = ["entry", "mid", "senior", "exec"]

    # Create the salary ranges list
    salary_ranges = [0, twenty_fifth, salaries_median, seventy_fifth, salaries["Salary_USD"].max()]

    # Create salary_level
    salaries["salary_level"] = pd.cut(salaries["Salary_USD"],
                                    bins=salary_ranges,
                                    labels=salary_labels)

    # Plot the count of salary levels at companies of different sizes
    sns.countplot(data=salaries, x="Company_Size", hue="salary_level")
    plt.show()

![Image113](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/ae33c02e-ca46-4638-874d-193099b5d919)

# Generating hypotheses

**Exercises:**

**Comparing salaries**

Exploratory data analysis is a crucial step in generating hypotheses!

You've had an idea you'd like to explore—do data professionals get paid more in the USA than they do in Great Britain?

You'll need to subset the data by "Employee_Location" and produce a plot displaying the average salary between the two groups.

The salaries DataFrame has been imported as a pandas DataFrame.

pandas has been imported as pd, maplotlib.pyplot as plt and seaborn as sns.

Instructions:

-Filter salaries where "Employee_Location" is "US" or "GB", saving as usa_and_gb.

-Use usa_and_gb to create a barplot visualizing "Salary_USD" against "Employee_Location".

    # Filter for employees in the US or GB
    usa_and_gb = salaries[salaries["Employee_Location"].isin(["US", "GB"])]

    # Create a barplot of salaries by location
    sns.barplot(data=usa_and_gb, x="Employee_Location", y="Salary_USD")
    plt.show()

![Image114](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b21c6297-35e3-476a-8a52-61a9236e2b40)

**Choosing a hypothesis**

You've seen how visualizations can be used to generate hypotheses, making them a crucial part of exploratory data analysis!

In this exercise, you'll generate a bar plot to inspect how salaries differ based on company size and employment status. For reference, there are four values:

    Value	Meaning
    CT	Contractor
    FL	Freelance
    PT	Part-time
    FT	Full-time

pandas has been imported as pd, matplotlib.pyplot as plt, seaborn as sns, and the salaries dataset as a pandas DataFrame called salaries.

Instructions:

-Produce a barplot comparing "Salary_USD" by "Company_Size", factoring "Employment_Status".

    # Create a bar plot of salary versus company size, factoring in employment status
    sns.barplot(data=salaries, x="Company_Size", y="Salary_USD", hue="Employment_Status")
    plt.show()

![Image115](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/692e7e2f-4d3b-446b-be87-ece4823f20e7)
