# Relationships in Data

**Description:**

Variables in datasets don't exist in a vacuum; they have relationships with each other. In this chapter, you'll look at relationships across numerical, categorical, and even DateTime data, exploring the direction and strength of these relationships as well as ways to visualize them.

# Patterns over time

**Personal notes**

When data includes dates or time values, we want to examine if there can be patterns over time.

The first step is to check if a particular column in the dataframe is, in fact, date or time data. They are usually interpreted as strings, so you need to change them:

- `divorce = pd.read_csv("divorce.csv", parse_dates=["marriage_date"])` - Add the `parse_dates` argument to the CSV import and set it to a list of column names that should be interpreted as DateTime data.

By checking `divorce.dtypes`, you can see that the column has been changed to `datetime64[ns]`, indicating it worked.

This type of data opens up many possibilities for analysis, such as observing patterns over years, months, or even days of the week.

- `divorce["marriage_date"] = pd.to_datetime(divorce["marriage_date"])` - You can use the `pd.to_datetime()` function to transform an object if you want to change it to datetime after using `pd.read`.

Creating datetime data:

- `divorce["marriage_date"] = pd.to_datetime(divorce[["month", "day", "year"]])` - If you have three separate columns in the dataframe and want to create a new datetime column containing the data from those columns, you can do it using `pd.to_datetime()` along with the columns of interest. The order of month-day-year needs to be respected for the code to work, but the columns can be in any order in the dataframe.

- `divorce["marriage_month"] = divorce["marriage_date"].dt.month` - This way, you can create a column containing only the months of the dates in the "marriage_date" column. You can use `dt.day` and `dt.year` for the day and year, respectively.

Line plots are a great way to examine relationships between variables.

- `sns.lineplot(data=, x=, y=)`

**Exercises:**

**Importing DateTime data**

You'll now work with the entire divorce dataset! The data describes Mexican marriages dissolved between 2000 and 2015. It contains marriage and divorce dates, education level, birthday, income for each partner, and marriage duration, as well as the number of children the couple had at the time of divorce.

The column names and data types are as follows:

    divorce_date          object
    dob_man               object
    education_man         object
    income_man           float64
    dob_woman             object
    education_woman       object
    income_woman         float64
    marriage_date         object
    marriage_duration    float64
    num_kids             float64

It looks like there is a lot of date information in this data that is not yet a DateTime data type! Your task is to fix that so that you can explore patterns over time.

pandas has been imported as pd.

Intructions:

-Import divorce.csv, saving as a DataFrame, divorce; indicate in the import function that the divorce_date, dob_man, dob_woman, and marriage_date columns should be imported as DateTime values.

        # Import divorce.csv, parsing the appropriate columns as dates in the import
        divorce = pd.read_csv("divorce.csv", parse_dates=["divorce_date", "dob_man", "dob_woman", "marriage_date"])

        print(divorce.dtypes)

**Updating data type to DateTime**

Now, the divorce DataFrame has been loaded for you, but one column is stored as a string that should be DateTime data. Which one is it? Once you've identified the column, you'll update it so that you can explore it more closely in the next exercise.

pandas has been imported as pd.

Instructions:

-Convert the marriage_date column of the divorce DataFrame to DateTime values.

        # Convert the marriage_date column to DateTime values
        divorce["marriage_date"] = pd.to_datetime(divorce["marriage_date"])

**Visualizing relationships over time**

Now that your date data is saved as DateTime data, you can explore patterns over time! Does the year that a couple got married have a relationship with the number of children that the couple has at the time of divorce? Your task is to find out!

The divorce DataFrame (with all dates formatted as DateTime data types) has been loaded for you. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

Instructions:

-Define a column called marriage_year, which contains just the year portion of the marriage_date column.

-Create a line plot showing the average number of kids a couple had during their marriage, arranged by the year that the couple got married.

        # Define the marriage_year column
        divorce["marriage_year"] = divorce["marriage_date"].dt.year

        # Create a line plot showing the average number of kids by year
        sns.lineplot(data=divorce, x="marriage_year", y="num_kids")
        plt.show()

![Image105](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/3e2e524d-8395-42e3-8ad2-137008f5ee41)

# Correlation

**Personal notes**

Getting a sense of the relationships between variables is important to assess how the data should be used. Correlation describes the direction of the relationship between two variables as well as its strength. Understanding this relationship can help us use variables to predict future outcomes.

To view the correlation of pairs of numeric columns in a dataframe:

- `DataFrame.corr()` - Use the `.corr()` function to calculate the Pearson correlation coefficient, which measures the linear relationship between two variables. A negative correlation coefficient indicates that as one variable increases, the other decreases. A value close to zero indicates a weak relationship, while values closer to one or negative one indicate stronger relationships.

Correlation Heatmap:

- `sns.heatmap(divorce.corr(), annot=True)` - Set the `annot` argument to `True`, and it labels the correlation coefficient within each cell of the heatmap. A heatmap has the benefit of strong color encoding for positive and negative points of correlations, making it easy to interpret. You can use a scatterplot to test the correlations and confirm if they are correct by simply comparing two variables of interest on the x and y axes.

Pairplots:

- `sns.pairplot(data=divorce)` - When you pass a dataframe, the pairplot plots all the pairwise relationships between numeric variables in one visualization. This is useful for a quick overview of relationships within the dataset.

- `sns.pairplot(data=divorce, vars=["income_man", "income_woman", "marriage_duration"])` - You can limit the number of relationships plotted by setting the `vars` argument to the variables of interest.

**Exercises:**

**Visualizing variable relationships**

In the last exercise, you may have noticed that a longer marriage_duration is correlated with having more children, represented by the num_kids column. The correlation coefficient between the marriage_duration and num_kids variables is 0.45.

In this exercise, you'll create a scatter plot to visualize the relationship between these variables. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

Instructions:

-Create a scatterplot showing marriage_duration on the x-axis and num_kids on the y-axis.

        # Create the scatterplot
        sns.scatterplot(data=divorce, x="marriage_duration", y="num_kids")
        plt.show()

![Image106](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/23b4ab02-b7fa-4cff-8d27-c6c2aa727f0e)

**Visualizing multiple variable relationships**

Seaborn's .pairplot() is excellent for understanding the relationships between several or all variables in a dataset by aggregating pairwise scatter plots in one visual.

Your task is to use a pairplot to compare the relationship between marriage_duration and income_woman. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

Instructions:

-Create a pairplot to visualize the relationships between income_woman and marriage_duration in the divorce DataFrame.

        # Create a pairplot for income_woman and marriage_duration
        sns.pairplot(data=divorce, vars=["income_woman", "marriage_duration"])
        plt.show()

![Image107](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/8ea37127-7850-4cf8-b9bc-721f696ef165)

# Factor relationships and distributions

**Personal notes**

Categorical variables are more challenging to summarize numerically, so we often rely on visualizations to explore their relationships.

You can use the `.value_counts()` function to initiate the analysis of categorical variables.

Histogram of the distribution:

- `sns.histplot(data=divorce, x="marriage_duration", hue="education_man", binwidth=1)` - In this example, we are creating a histogram of the "marriage_duration" column and then adding information about the male education level, setting the "education_man" column as the `hue` argument.

Kernel Density Estimate (KDE) plots:
Seaborn's Kernel Density Estimate or KDE plots, similar to histograms, allow us to visualize distributions. They are considered more interpretable, especially when multiple distributions need to be shown at the same time.

- `sns.kdeplot(data=divorce, x="marriage_duration", hue="education_man", cut=0)` - The `cut` argument tells Seaborn how far beyond the minimum and maximum data values the curve should go when smoothing is applied. When you set `cut` to zero, the curve will be confined to values between the minimum and maximum values of x.

If you are interested in the cumulative distribution function, you can set the `cumulative` argument to `True`:

- `sns.kdeplot(data=divorce, x="marriage_duration", hue="education_man", cut=0, cumulative=True)`

**Exercises:**

**Categorial data in scatter plots**

In the video, we explored how men's education and age at marriage related to other variables in our dataset, the divorce DataFrame. Now, you'll take a look at how women's education and age at marriage relate to other variables!

Your task is to create a scatter plot of each woman's age and income, layering in the categorical variable of education level for additional context.

The divorce DataFrame has been loaded for you, and woman_age_marriage has already been defined as a column representing an estimate of the woman's age at the time of marriage. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

Instructions:

-Create a scatter plot that shows woman_age_marriage on the x-axis and income_woman on the y-axis; each data point should be colored based on the woman's level of education, represented by education_woman.

        # Create the scatter plot
        sns.scatterplot(data=divorce, x="woman_age_marriage", y="income_woman", hue="education_woman")
        plt.show()

![Image108](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e993ccac-6b20-4d1e-996e-2b1c19761925)

**Exploring with KDE plots**

Kernel Density Estimate (KDE) plots are a great alternative to histograms when you want to show multiple distributions in the same visual.

Suppose you are interested in the relationship between marriage duration and the number of kids that a couple has. Since values in the num_kids column range only from one to five, you can plot the KDE for each value on the same plot.

The divorce DataFrame has been loaded for you. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns. Recall that the num_kids column in divorce lists only N/A values for couples with no children, so you'll only be looking at distributions for divorced couples with at least one child.

Instructions:

-Create a KDE plot that shows marriage_duration on the x-axis and a different colored line for each possible number of children that a couple might have, represented by num_kids.

    # Create the KDE plot
    sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids")
    plt.show()

![Image109](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/de6c7f8c-6c9a-41a2-9d2f-04134426d2a1)

-Notice that the plot currently shows marriage durations less than zero; update the KDE plot so that marriage duration cannot be smoothed past the extreme data points.

    # Update the KDE plot so that marriage duration can't be smoothed too far
    sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids", cut=0)
    plt.show()

![Image110](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/a961e8b1-2147-43fd-a1e1-4b58ccda6156)

-Update the code for the KDE plot from the previous step to show a cumulative distribution function for each number of children a couple has.

    # Update the KDE plot to show a cumulative distribution function
    sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids", cut=0, cumulative=True)
    plt.show()

![Image111](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/57ac257a-7124-4225-af04-03fdadea49fb)


