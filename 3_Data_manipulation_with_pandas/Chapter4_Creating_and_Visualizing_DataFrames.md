# Creating and Visualizing DataFrames

**Description:**

Learn to visualize the contents of your DataFrames, handle missing data values, and import data from and export data to CSV files.

# Visualizing your data

**Personal Notes**

To create bar charts:

- `.plot(kind="bar")`

- `.plot(kind="bar", title="write the title")`

Line charts - great for visualizing changes in numeric variables over time:

- `.plot(x="date", y="weight_kg", kind="line")` - To plot a line chart while selecting the x and y axes and specifying the chart type as a line.

- `.plot(x="date", y="weight_kg", kind="line", rot=45)` - The `rot` parameter rotates the x-axis labels for better chart visualization.

Scatter plots - excellent for visualizing relationships between two numeric variables:

- `.plot(x="height_cm", y="weight_kg", kind="scatter")` - To create a scatter plot with selected x and y axes.

Layering plots with legends and transparency:

- `plot.legend(["F", "M"])` - Add a legend to the histogram.

- `.hist(alpha=0.7)` - To make the chart slightly transparent and differentiate the results in distinguishable layers while making both visible; 0 = fully transparent and 1 fully opaque.

**Exercises:**

**Which avocado size is most popular?**

Avocados are increasingly popular and delicious in guacamole and on toast. The Hass Avocado Board keeps track of avocado supply and demand across the USA, including the sales of three different sizes of avocado. In this exercise, you'll use a bar plot to figure out which size is the most popular.

Bar plots are great for revealing relationships between categorical (size) and numeric (number sold) variables, but you'll often have to manipulate your data first in order to get the numbers you need for plotting.

pandas has been imported as pd, and avocados is available.

Instructions:

-Print the head of the avocados dataset. What columns are available?

-For each avocado size group, calculate the total number sold, storing as nb_sold_by_size.

-Create a bar plot of the number of avocados sold by size.

-Show the plot.

    # Import matplotlib.pyplot with alias plt
    import matplotlib.pyplot as plt

    # Look at the first few rows of data
    print(avocados.head())

    # Get the total number of avocados sold of each size
    nb_sold_by_size = avocados.groupby("size")["nb_sold"].sum()

    # Create a bar plot of the number of avocados sold by size
    nb_sold_by_size.plot(kind="bar",title="Number of avocados sold by size")

    # Show the plot
    plt.show()

![Image22](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e33c0d6b-d603-46c0-a627-1ca1f04c0c7d)

**Changes in sales over time**

Line plots are designed to visualize the relationship between two numeric variables, where each data values is connected to the next one. They are especially useful for visualizing the change in a number over time since each time point is naturally connected to the next time point. In this exercise, you'll visualize the change in avocado sales over three years.

pandas has been imported as pd, and avocados is available.

Instructions:

-Get the total number of avocados sold on each date. The DataFrame has two rows for each date—one for organic, and one for conventional. Save this as nb_sold_by_date.

-Create a line plot of the number of avocados sold.

-Show the plot.

    # Import matplotlib.pyplot with alias plt
    import matplotlib.pyplot as plt

    # Get the total number of avocados sold on each date
    nb_sold_by_date = avocados.groupby("date")["nb_sold"].sum()

    # Create a line plot of the number of avocados sold by date
    nb_sold_by_date.plot(x="date",y="nb_sold",kind="line")

    # Show the plot
    plt.show()

![Image23](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b6327783-d071-4dd8-b9c7-9535b4ef8d7d)

**vocado supply and demand**

Scatter plots are ideal for visualizing relationships between numerical variables. In this exercise, you'll compare the number of avocados sold to average price and see if they're at all related. If they're related, you may be able to use one number to predict the other.

matplotlib.pyplot has been imported as plt, pandas has been imported as pd, and avocados is available.

Instructions:

-Create a scatter plot with nb_sold on the x-axis and avg_price on the y-axis. Title it "Number of avocados sold vs. average price".

-Show the plot.

    # Scatter plot of avg_price vs. nb_sold with title
    avocados.plot(x="nb_sold",y="avg_price",kind="scatter",title="Number of avocados sold vs. average price")

    # Show the plot
    plt.show()

![image24](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d88bcdb8-a6e5-46a2-8e93-75efec6ab0e4)

**Price of conventional vs. organic avocados**

Creating multiple plots for different subsets of data allows you to compare groups. In this exercise, you'll create multiple histograms to compare the prices of conventional and organic avocados.

matplotlib.pyplot has been imported as plt and pandas has been imported as pd.

Instructions:

-Subset avocados for the conventional type, and the average price column. Create a histogram.

-Create a histogram of avg_price for organic type avocados.

-Add a legend to your plot, with the names "conventional" and "organic".

-Show your plot.

    # Histogram of conventional avg_price 
    avocados[avocados["type"]=="conventional"]["avg_price"].hist()

    # Histogram of organic avg_price
    avocados[avocados["type"]=="organic"]["avg_price"].hist()

    # Add a legend
    plt.legend(["conventional", "organic"])

    # Show the plot
    plt.show()

![Image25](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/4aae8210-eeb8-4a6b-a266-a7f672c73fe2)

-Modify your code to adjust the transparency of both histograms to 0.5 to see how much overlap there is between the two distributions.

    # Modify histogram transparency to 0.5 
    avocados[avocados["type"] == "conventional"]["avg_price"].hist(alpha=0.5)

    # Modify histogram transparency to 0.5
    avocados[avocados["type"] == "organic"]["avg_price"].hist(alpha=0.5)

    # Add a legend
    plt.legend(["conventional", "organic"])

    # Show the plot
    plt.show()

![Image26](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b1b3072b-a1e9-49e5-adf3-3f0a316faa19)

-Modify your code to use 20 bins in both histograms.

    # Modify bins to 20
    avocados[avocados["type"] == "conventional"]["avg_price"].hist(bins=20, alpha=0.5)

    # Modify bins to 20
    avocados[avocados["type"] == "organic"]["avg_price"].hist(bins=20, alpha=0.5)

    # Add a legend
    plt.legend(["conventional", "organic"])

    # Show the plot
    plt.show()

![Image27](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b5f26bf6-45ef-467c-a98e-0d499e98c96b)

# Missing Values

**Personal Notes**

Dataframes with empty values - NaN "Not a Number"

To detect missing values:

- `DataFrame.isna()` - obtains a boolean for each value indicating True when it is an empty value - not efficient for a large number of data.

- `DataFrame.isna().any()` - shows by columns a boolean indicating whether there are empty values.

- `DataFrame.isna().sum()` - Sums the empty numbers in each column.

- `DataFrame.isna().sum().plot(kind="bar")` - To plot a bar chart and help visualize the sum of empty numbers in each column of the dataframe.

- `DataFrame.dropna()` - To remove empty values, not ideal for a large number of empty values.

- `DataFrame.fillna(0)` - To replace empty values with the number inside the brackets, in this case, 0.

**Exercises:**

**Finding missing values**

Missing values are everywhere, and you don't want them interfering with your work. Some functions ignore missing data by default, but that's not always the behavior you might want. Some functions can't handle missing values at all, so these values need to be taken care of before you can use them. If you don't know where your missing values are, or if they exist, you could make mistakes in your analysis. In this exercise, you'll determine if there are missing values in the dataset, and if so, how many.

pandas has been imported as pd and avocados_2016, a subset of avocados that contains only sales from 2016, is available.

Instructions:

-Print a DataFrame that shows whether each value in avocados_2016 is missing or not.

-Print a summary that shows whether any value in each column is missing or not.

-Create a bar plot of the total number of missing values in each column.

    # Import matplotlib.pyplot with alias plt
    import matplotlib.pyplot as plt

    # Check individual values for missing values
    print(avocados_2016.isna())

    # Check each column for missing values
    print(avocados_2016.isna().any())

    # Bar plot of missing values by variable
    avocados_2016.isna().sum().plot(kind="bar")


    # Show plot
    plt.show()

![Image28](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/24e89b1b-c8cb-4992-be97-db1440979bc6)

**Removing missing values**

Now that you know there are some missing values in your DataFrame, you have a few options to deal with them. One way is to remove them from the dataset completely. In this exercise, you'll remove missing values by removing all rows that contain missing values.

pandas has been imported as pd and avocados_2016 is available.

Instructions:

-Remove the rows of avocados_2016 that contain missing values and store the remaining rows in avocados_complete.

-Verify that all missing values have been removed from avocados_complete. Calculate each column that has NAs and print.

    # Remove rows with missing values
    avocados_complete = avocados_2016.dropna()

    # Check if any columns contain missing values
    print(avocados_complete.isna().any())

**Replacing missing values**

Another way of handling missing values is to replace them all with the same value. For numerical variables, one option is to replace values with 0— you'll do this here. However, when you replace missing values, you make assumptions about what a missing value means. In this case, you will assume that a missing number sold means that no sales for that avocado type were made that week.

In this exercise, you'll see how replacing missing values can affect the distribution of a variable using histograms. You can plot histograms for multiple variables at a time as follows:

dogs[["height_cm", "weight_kg"]].hist()

pandas has been imported as pd and matplotlib.pyplot has been imported as plt. The avocados_2016 dataset is available.

Instructions:

-A list has been created, cols_with_missing, containing the names of columns with missing values: "small_sold", "large_sold", and "xl_sold".

-Create a histogram of those columns.

-Show the plot.

    # List the columns with missing values
    cols_with_missing = ["small_sold", "large_sold", "xl_sold"]

    # Create histograms showing the distributions cols_with_missing
    avocados_2016[cols_with_missing].hist()

    # Show the plot
    plt.show()

![Image29](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/f5cb0f9e-b4dc-4328-a05c-4e823bbf4446)


-Replace the missing values of avocados_2016 with 0s and store the result as avocados_filled.

-Create a histogram of the cols_with_missing columns of avocados_filled.

    # From previous step
    cols_with_missing = ["small_sold", "large_sold", "xl_sold"]
    avocados_2016[cols_with_missing].hist()
    plt.show()

    # Fill in missing values with 0
    avocados_filled = avocados_2016.fillna(0)

    # Create histograms of the filled columns
    avocados_filled[cols_with_missing].hist()

    # Show the plot
    plt.show()

![Image30](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b469def6-8e87-4288-b430-9801bb23ee63)

# Creating DataFrames

**Personal Notes**

Basically, a class that has already been given about creating DataFrames using dictionaries and lists.

- `pd.DataFrame()` - Creates a DataFrame by placing a previously made list or dictionary inside the brackets.

**Exercises:**

**List of dictionaries**

You recently got some new avocado data from 2019 that you'd like to put in a DataFrame using the list of dictionaries method. Remember that with this method, you go through the data row by row.

date	small_sold	large_sold

"2019-11-03"	10376832	7835071

"2019-11-10"	10717154	8561348

pandas as pd is imported.

Instructions:

-Create a list of dictionaries with the new data called avocados_list.

-Convert the list into a DataFrame called avocados_2019.

-Print your new DataFrame.

    # Create a list of dictionaries with new data
    avocados_list = [
        {"date": "2019-11-03", "small_sold": 10376832, "large_sold": 7835071},
        {"date": "2019-11-10", "small_sold": 10717154, "large_sold": 8561348},
    ]

    # Convert list into DataFrame
    avocados_2019 = pd.DataFrame(avocados_list)

    # Print the new DataFrame
    print(avocados_2019)

**Dictionary of lists**

Some more data just came in! This time, you'll use the dictionary of lists method, parsing the data column by column.

date	small_sold	large_sold

"2019-11-17"	10859987	7674135

"2019-12-01"	9291631	6238096

pandas as pd is imported.

Instructions:
-Create a dictionary of lists with the new data called avocados_dict.

-Convert the dictionary to a DataFrame called avocados_2019.

-Print your new DataFrame.

    # Create a dictionary of lists with new data
    avocados_dict = {
    "date": ["2019-11-17","2019-12-01"],
    "small_sold": [10859987, 9291631],
    "large_sold": [7674135, 6238096]
    }

    # Convert dictionary into DataFrame
    avocados_2019 = pd.DataFrame(avocados_dict)

    # Print the new DataFrame
    print(avocados_2019)

