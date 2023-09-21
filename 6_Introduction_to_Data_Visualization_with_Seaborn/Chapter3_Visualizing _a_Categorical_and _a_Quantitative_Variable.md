#  Visualizing a Categorical and a Quantitative Variable

**Description**

Categorical variables are present in nearly every dataset, but they are especially prominent in survey data. In this chapter, you will learn how to create and customize categorical plots such as box plots, bar plots, count plots, and point plots. Along the way, you will explore survey data from young people about their interests, students about their study habits, and adult men about their feelings about masculinity.

# Count plots and bar plots

**Personal notes:**

Visualizations involving categorical variables. Count plots and bar plots are two types of visualizations that Seaborn refers to as "categorical plots." Categorical plots involve a categorical variable, which is a variable consisting of a fixed, typically small, number of possible values or categories. These types of plots are commonly used when we want to make comparisons between different groups.

Using `catplot()` - to create different types of categorical plots, it works similarly to `relplot`:

```python
sns.catplot(x="how_masculine", data=masculinity_data, kind="count")
```

Similar to `relplot`, you specify the x-axis, the DataFrame, and use `kind="count"` to generate a count plot.

Bar plots are similar to count plots, but instead of counting observations in each category, they show the average of a quantitative variable among observations in each category:

```python
sns.catplot(x="day", y="total_bill", data=tips, kind="bar")
```

By setting `kind="bar"`, you create a bar plot. Seaborn automatically shows a 95% confidence interval for the means.

To disable the confidence interval:

```python
sns.catplot(x="day", y="total_bill", data=tips, kind="bar", ci=None)
```

If you want to change the bars to be vertical, you simply switch the x and y variables. However, it's common practice to put the categorical variable on the x-axis.

**Exercises:**

**Count plots**

In this exercise, we'll return to exploring our dataset that contains the responses to a survey sent out to young people. We might suspect that young people spend a lot of time on the internet, but how much do they report using the internet each day? Let's use a count plot to break down the number of survey responses in each category and then explore whether it changes based on age.

As a reminder, to create a count plot, we'll use the catplot() function and specify the name of the categorical variable to count (x=____), the pandas DataFrame to use (data=____), and the type of plot (kind="count").

Seaborn has been imported as sns and matplotlib.pyplot has been imported as plt.

Instructions:

-Use sns.catplot() to create a count plot using the survey_data DataFrame with "Internet usage" on the x-axis.

        # Create count plot of internet usage
        sns.catplot(x="Internet usage", data=survey_data, kind="count")


        # Show plot
        plt.show()       

![Image74](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/25b1a6cc-6364-4b7f-bd48-be1e8c9de0f8)

-Make the bars horizontal instead of vertical.

-Separate this plot into two side-by-side column subplots based on "Age Category", which separates respondents into those that are younger than 21 vs. 21 and older.

        # Separate into column subplots based on age category
        sns.catplot(y="Internet usage", data=survey_data,
                    kind="count", col="Age Category")

        # Show plot
        plt.show()
    
![Image75](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/f2c53405-fee5-4351-a323-d7cc49cf813c)


**Bar plots with percentages**

Let's continue exploring the responses to a survey sent out to young people. The variable "Interested in Math" is True if the person reported being interested or very interested in mathematics, and False otherwise. What percentage of young people report being interested in math, and does this vary based on gender? Let's use a bar plot to find out.

As a reminder, we'll create a bar plot using the catplot() function, providing the name of categorical variable to put on the x-axis (x=____), the name of the quantitative variable to summarize on the y-axis (y=____), the pandas DataFrame to use (data=____), and the type of categorical plot (kind="bar").

Seaborn has been imported as sns and matplotlib.pyplot has been imported as plt.

Instructions:

-Use the survey_data DataFrame and sns.catplot() to create a bar plot with "Gender" on the x-axis and "Interested in Math" on the y-axis.

        # Create a bar plot of interest in math, separated by gender
        sns.catplot(x="Gender", y="Interested in Math", data=survey_data, kind="bar")


        # Show plot
        plt.show()

![Image76](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/961b7756-840b-4fea-a312-2023edf33c28)


**Customizing bar plots**

In this exercise, we'll explore data from students in secondary school. The "study_time" variable records each student's reported weekly study time as one of the following categories: "<2 hours", "2 to 5 hours", "5 to 10 hours", or ">10 hours". Do students who report higher amounts of studying tend to get better final grades? Let's compare the average final grade among students in each category using a bar plot.

Seaborn has been imported as sns and matplotlib.pyplot has been imported as plt.

Instructions:

-Use sns.catplot() to create a bar plot with "study_time" on the x-axis and final grade ("G3") on the y-axis, using the student_data DataFrame.

        # Create bar plot of average final grade in each study category
        sns.catplot(x="study_time", y="G3", data=student_data, kind="bar")



        # Show plot
        plt.show()

![Image77](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/47c0acac-bcec-4500-9483-80a0e8d8c726)
 

-Using the order parameter and the category_order list that is provided, rearrange the bars so that they are in order from lowest study time to highest.

-Update the plot so that it no longer displays confidence intervals.

        # List of categories from lowest to highest
        category_order = ["<2 hours", 
                        "2 to 5 hours", 
                        "5 to 10 hours", 
                        ">10 hours"]

        # Turn off the confidence intervals
        sns.catplot(x="study_time", y="G3",
                    data=student_data,
                    kind="bar",
                    order=category_order,
                    ci=None)

        # Show plot
        plt.show()

![Image78](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/50cc94b0-102b-4131-bbaa-159a46bce4ad)

# Box plots

**Personal notes:**

A box plot displays the distribution of quantitative data. The colored box represents the 25th to 75th percentiles, and the middle line inside the box represents the median. The whiskers provide an idea of the spread of the distribution, and the floating points represent outliers.

Box plots are commonly used as a way to compare the distribution of a quantitative variable across different groups of a categorical variable.

Creating a box plot with `catplot()`:

```python
sns.catplot(x="time", y="total_bills", data=tips, kind="box")
```

Setting `kind="box"` creates a box plot.

You can change the whiskers' behavior using the "whis" parameter. By default, whiskers extend up to 1.5 times the interquartile range (IQR). For example:

- `whis=2.0` modifies the whiskers to extend up to 2 times the IQR.
- To show the 5th and 95th percentiles, you can use `whis=[5, 95]`.
- To show the minimum and maximum values, use `whis=[0, 100]`.

```python
sns.catplot(x="time", y="total_bills", data=tips, kind="box", whis=[0, 100])
```

This will display whiskers covering the entire range of data.

**Exercises:**

**Create and interpret a box plot**

Let's continue using the student_data dataset. In an earlier exercise, we explored the relationship between studying and final grade by using a bar plot to compare the average final grade ("G3") among students in different categories of "study_time".

In this exercise, we'll try using a box plot look at this relationship instead. As a reminder, to create a box plot you'll need to use the catplot() function and specify the name of the categorical variable to put on the x-axis (x=____), the name of the quantitative variable to summarize on the y-axis (y=____), the pandas DataFrame to use (data=____), and the type of plot (kind="box").

We have already imported matplotlib.pyplot as plt and seaborn as sns.

Instructions:

-Use sns.catplot() and the student_data DataFrame to create a box plot with "study_time" on the x-axis and "G3" on the y-axis. Set the ordering of the categories to study_time_order.

        # Specify the category ordering
        study_time_order = ["<2 hours", "2 to 5 hours", 
                            "5 to 10 hours", ">10 hours"]

        # Create a box plot and set the order of the categories
        sns.catplot(x="study_time", y="G3",
                    data=student_data, kind="box",
                    order=study_time_order)

        # Show plot
        plt.show()

![Image79](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/88b8fae9-375c-4894-80a8-4c35d5c5b976)


**Omitting outliers**

Now let's use the student_data dataset to compare the distribution of final grades ("G3") between students who have internet access at home and those who don't. To do this, we'll use the "internet" variable, which is a binary (yes/no) indicator of whether the student has internet access at home.

Since internet may be less accessible in rural areas, we'll add subgroups based on where the student lives. For this, we can use the "location" variable, which is an indicator of whether a student lives in an urban ("Urban") or rural ("Rural") location.

Seaborn has already been imported as sns and matplotlib.pyplot has been imported as plt. As a reminder, you can omit outliers in box plots by setting the sym parameter equal to an empty string ("").

Instructions:

-Use sns.catplot() to create a box plot with the student_data DataFrame, putting "internet" on the x-axis and "G3" on the y-axis.

-Add subgroups so each box plot is colored based on "location".

-Do not display the outliers.

        # Create a box plot with subgroups and omit the outliers
        sns.catplot(x="internet", y="G3",
                    data=student_data, kind="box",
                    hue="location", sym="")

        # Show plot
        plt.show()

![Image80](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/de9efb7c-5249-4a76-93df-259bef972ec2)


**Adjusting the whiskers**

In the lesson we saw that there are multiple ways to define the whiskers in a box plot. In this set of exercises, we'll continue to use the student_data dataset to compare the distribution of final grades ("G3") between students who are in a romantic relationship and those that are not. We'll use the "romantic" variable, which is a yes/no indicator of whether the student is in a romantic relationship.

Let's create a box plot to look at this relationship and try different ways to define the whiskers.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Adjust the code to make the box plot whiskers to extend to 0.5 * IQR. Recall: the IQR is the interquartile range.

        # Set the whiskers to 0.5 * IQR
        sns.catplot(x="romantic", y="G3",
                    data=student_data,
                    kind="box", whis=0.5)

        # Show plot
        plt.show()

![Image81](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/8af10120-f148-4b7f-ba99-2aa123ef2453)


-Change the code to set the whiskers to extend to the 5th and 95th percentiles.

        # Extend the whiskers to the 5th and 95th percentile
        sns.catplot(x="romantic", y="G3",
                    data=student_data,
                    kind="box",
                    whis=[5,95])

        # Show plot
        plt.show()

![Image82](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/cd59f2c8-8923-43b4-b61f-ab42ebf9cf6f)


-Change the code to set the whiskers to extend to the min and max values.

        # Set the whiskers at the min and max values
        sns.catplot(x="romantic", y="G3",
                    data=student_data,
                    kind="box",
                    whis=[0, 100])

        # Show plot
        plt.show()

![Image83](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/00a6c5a0-e173-4a95-b2ed-bda0a29119e0)


# Point plots 

**Personal notes:**

Point plots show the mean of a quantitative variable for observations in each category, plotted as a single point. The vertical bars extending above and below the mean represent the 95% confidence intervals for that mean. Just like the confidence intervals we've seen in line plots and bar plots, these confidence intervals show the level of uncertainty we have about these mean estimates.

The line plots presented earlier are relational plots, so both the x and y axes are quantitative variables. In a point plot, one axis (usually the x-axis) is a categorical variable, making it a categorical plot.

```python
sns.catplot(x="age", y="masculinity_important", data=masculinity_data, hue="feel_masculine", kind="point")
```

To create a point plot, you use the `kind="point"` parameter.

You can remove the lines connecting each point by setting the `join` parameter to `False`:

```python
sns.catplot(x="age", y="masculinity_important", data=masculinity_data, hue="feel_masculine", kind="point", join=False)
```

If you want the points and confidence intervals to be calculated for the median instead of the mean, you can use the `estimator` parameter:

```python
from numpy import median

sns.catplot(x="smoker", y="total_bills", data=tips, kind="point", estimator=median)
```

The median is more robust to outliers, so if your dataset has many outliers, the median may be a better statistic to use.

You can also add caps to the end of confidence intervals using the `capsize` parameter:

```python
sns.catplot(x="smoker", y="total_bills", data=tips, kind="point", capsize=0.2)
```

To disable confidence intervals altogether, set `ci=None`:

```python
sns.catplot(x="smoker", y="total_bills", data=tips, kind="point", ci=None)
```

**Exercises:**

**Customizing point plots**

Let's continue to look at data from students in secondary school, this time using a point plot to answer the question: does the quality of the student's family relationship influence the number of absences the student has in school? Here, we'll use the "famrel" variable, which describes the quality of a student's family relationship from 1 (very bad) to 5 (very good).

As a reminder, to create a point plot, use the catplot() function and specify the name of the categorical variable to put on the x-axis (x=____), the name of the quantitative variable to summarize on the y-axis (y=____), the pandas DataFrame to use (data=____), and the type of categorical plot (kind="point").

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Use sns.catplot() and the student_data DataFrame to create a point plot with "famrel" on the x-axis and number of absences ("absences") on the y-axis.

-Add "caps" to the end of the confidence intervals with size 0.2.

-Remove the lines joining the points in each category.

        sns.catplot(x="famrel", y="absences",
			        data=student_data,
                    kind="point",
                    capsize=0.2, join=False)
            
        # Show plot
        plt.show()

![Image84](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d0844251-fda8-42c6-b7de-d6289c5416c0)


**Point plots with subgroups**

Let's continue exploring the dataset of students in secondary school. This time, we'll ask the question: is being in a romantic relationship associated with higher or lower school attendance? And does this association differ by which school the students attend? Let's find out using a point plot.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Use sns.catplot() and the student_data DataFrame to create a point plot with relationship status ("romantic") on the x-axis and number of absences ("absences") on the y-axis. Color the points based on the school that they attend ("school").

-Turn off the confidence intervals for the plot.

-Since there may be outliers of students with many absences, use the median function that we've imported from numpy to display the median number of absences instead of the average

        # Import median function from numpy
        from numpy import median

        # Plot the median number of absences instead of the mean
        sns.catplot(x="romantic", y="absences",
			        data=student_data,
                    kind="point",
                    hue="school",
                    ci=None, estimator=median)

        # Show plot
        plt.show()

![Image85](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/5bfa864e-9170-4460-80af-9059fda61da1)