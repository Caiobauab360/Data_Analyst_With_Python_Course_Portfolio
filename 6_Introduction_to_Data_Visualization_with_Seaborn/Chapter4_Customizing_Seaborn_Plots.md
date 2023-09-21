# Customizing Seaborn Plots

**Description**

In this final chapter, you will learn how to add informative plot titles and axis labels, which are one of the most important parts of any data visualization! You will also learn how to customize the style of your visualizations in order to more quickly orient your audience to the key takeaways. Then, you will put everything you have learned together for the final exercises of the course!

# Changing plot style and color

**Personal notes:**

Changing the style of a plot can be motivated by personal preference but can also help improve readability or guide the audience more quickly to key insights.

Seaborn has five predefined figure styles that alter the background and axes of the plot. You can refer to them by name: "white," "dark," "whitegrid," "darkgrid," and "ticks." The default style is "white," which provides clean axes with a solid white background. Changing to "whitegrid" will add a gray grid in the background, which can be helpful if you want your audience to determine specific values of plotted points rather than making higher-level observations. The others are variations: "ticks" is similar to "white" but adds small ticks to the x and y axes. "dark" provides a gray background, and "darkgrid" offers a gray background with a white grid.

To set one of these styles as the global style for all your plots, use the `sns.set_style()` function.

```python
sns.set_style("darkgrid")
```

In this example, we are changing the style to "darkgrid," which is set before using `sns.catplot`.

Changing the Palette:

You can change the color of the main plot elements with the `set_palette` function. Seaborn has a group of predefined palettes called divergent palettes that are great to use when your visualization deals with a scale where both ends of the scale are opposites, and there's a neutral midpoint.

Diverging palettes are recommended when the visualization involves a scale where both ends of the scale are opposites, and there is a neutral midpoint.

- "RdBu" - Color palette that goes from red to blue.
- "PRGn" - Color palette that goes from purple to green.
- "RdBu_r" - Reverse of RdBu, goes from blue to red.
- "PRGn_r" - Reverse of PRGn, goes from green to purple.

Sequential palettes are a single color (or two blended colors) moving from light to dark values:

- "Greys" - Color gradient that goes from light gray to dark gray (black).
- "Blues" - Color gradient that goes from light blue to navy blue.
- "PuRd" - Color gradient that goes from light pink to dark pink (almost red).
- "GnBu" - Gradient that starts with light green and moves to navy blue.

Sequential palettes are great for emphasizing a variable on a continuous scale.

Custom palettes can be created by passing a list of color names:

```python
custom_palette = ["red", "green", "orange", "blue", "yellow", "purple"]
```

You need to create a variable containing the sequence of colors you want to form the palette.

How to use palettes:

```python
sns.set_palette("RdBu")
```

Set the `set_palette` function to the desired palette before creating the code to plot the graph.

Changing the Scale:

You can change the scale of your plot using the `sns.set_context()` function. The scale options, from smallest to largest, are "paper," "notebook," "talk," and "poster." The default is set to "paper."

The "talk" scale option can be used for posters or presentations where the audience is further away from the plot.

**Exercises:**

**Changing style and palette**

Let's return to our dataset containing the results of a survey given to young people about their habits and preferences. We've provided the code to create a count plot of their responses to the question "How often do you listen to your parents' advice?". Now let's change the style and palette to make this plot easier to interpret.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Set the style to "whitegrid" to help the audience determine the number of responses in each category.

-Set the color palette to the sequential palette named "Purples".

        # Set the color palette to "Purples"
        sns.set_style("whitegrid")
        sns.set_palette("Purples")

        # Create a count plot of survey responses
        category_order = ["Never", "Rarely", "Sometimes", 
                        "Often", "Always"]

        sns.catplot(x="Parents Advice", 
                    data=survey_data, 
                    kind="count", 
                    order=category_order)

        # Show plot
        plt.show()

![Image86](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/42da5f23-fad4-4ff0-83b4-c28d20597fb8)

-Change the color palette to the diverging palette named "RdBu".

        # Change the color palette to "RdBu"
        sns.set_style("whitegrid")
        sns.set_palette("RdBu")

        # Create a count plot of survey responses
        category_order = ["Never", "Rarely", "Sometimes", 
                        "Often", "Always"]

        sns.catplot(x="Parents Advice", 
                    data=survey_data, 
                    kind="count", 
                    order=category_order)

        # Show plot
        plt.show()

![Image87](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e0b6705a-18ce-4d62-80ee-44bdd637db1d)

**Changing the scale**

In this exercise, we'll continue to look at the dataset containing responses from a survey of young people. Does the percentage of people reporting that they feel lonely vary depending on how many siblings they have? Let's find out using a bar plot, while also exploring Seaborn's four different plot scales ("contexts").

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Set the scale ("context") to "paper", which is the smallest of the scale options.

        # Set the context to "paper"
        sns.set_context("paper")

        # Create bar plot
        sns.catplot(x="Number of Siblings", y="Feels Lonely",
                    data=survey_data, kind="bar")

        # Show plot
        plt.show()

![Image88](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/6c1aa7c9-acc5-42be-88ab-cf2df56b1e5f)


-Change the context to "notebook" to increase the scale.

        # Set the context to "notebook"
        sns.set_context("notebook")

        # Create bar plot
        sns.catplot(x="Number of Siblings", y="Feels Lonely",
                    data=survey_data, kind="bar")

        # Show plot
        plt.show()

![Image89](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/af8673a9-ea35-468a-8824-94cd402d5e06)


-Change the context to "talk" to increase the scale.

        # Set the context to "talk"
        sns.set_context("talk")

        # Create bar plot
        sns.catplot(x="Number of Siblings", y="Feels Lonely",
                    data=survey_data, kind="bar")

        # Show plot
        plt.show()

![Image90](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/af56d1b8-4b0c-43d0-931e-97ad8e0da1a2)

-Change the context to "poster", which is the largest scale available.

    # Set the context to "poster"
        sns.set_context("poster")

        # Create bar plot
        sns.catplot(x="Number of Siblings", y="Feels Lonely",
                    data=survey_data, kind="bar")

        # Show plot
        plt.show()

![Image91](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/95d686f0-f125-45af-b276-421fa7b76190)

**Using a custom palette**

So far, we've looked at several things in the dataset of survey responses from young people, including their internet usage, how often they listen to their parents, and how many of them report feeling lonely. However, one thing we haven't done is a basic summary of the type of people answering this survey, including their age and gender. Providing these basic summaries is always a good practice when dealing with an unfamiliar dataset.

The code provided will create a box plot showing the distribution of ages for male versus female respondents. Let's adjust the code to customize the appearance, this time using a custom color palette.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Set the style to "darkgrid".

-Set a custom color palette with the hex color codes "#39A7D0" and "#36ADA4".

      # Set the style to "darkgrid"
        sns.set_style("darkgrid")

        # Set a custom color palette
        sns.set_palette(['#39A7D0', '#36ADA4'])

        # Create the box plot of age distribution by gender
        sns.catplot(x="Gender", y="Age", 
                    data=survey_data, kind="box")

        # Show plot
        plt.show()

![Image92](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/a2acf204-edd8-466f-8a17-9a578dfe52b2)


# Adding titles and labels: Part 1

**Personal notes:**

Seaborn's plotting functions create two different types of objects: FacetGrids and AxesSubplot. A FacetGrid consists of one or more AxesSubplots, which is how it supports subplots. `relplot()` and `catplot()` are examples of FacetGrids, while `scatterplot()` and `countplot()` are examples of AxesSubplots.

Adding a title to a FacetGrid:

```python
g.fig.suptitle("New Title")
```

First, you need to assign a variable to the plot, in this case, the variable is `g`. By using the `fig.suptitle("")` parameter, you can change or add a name to the plot.

To adjust the height of the title in a FacetGrid:

```python
g.fig.suptitle("New Title", y=1.03)
```

To adjust the height of the title, you can use the `y` parameter. The default value is 1, so setting it to 1.03 makes the title slightly higher than the default.

**Exercises:**

**FacetGrids vs. AxesSubplots**

In the recent lesson, we learned that Seaborn plot functions create two different types of objects: FacetGrid objects and AxesSubplot objects. The method for adding a title to your plot will differ depending on the type of object it is.

In the code provided, we've used relplot() with the miles per gallon dataset to create a scatter plot showing the relationship between a car's weight and its horsepower. This scatter plot is assigned to the variable name g. Let's identify which type of object it is.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Identify what type of object plot g is and assign it to the variable type_of_g.

        # Create scatter plot
        g = sns.relplot(x="weight", 
                        y="horsepower", 
                        data=mpg,
                        kind="scatter")

        # Identify plot type
        type_of_g = type(g)

        # Print type
        print(type_of_g)

**Adding a title to a FacetGrid object**

In the previous exercise, we used relplot() with the miles per gallon dataset to create a scatter plot showing the relationship between a car's weight and its horsepower. This created a FacetGrid object. Now that we know what type of object it is, let's add a title to this plot.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Add the following title to this plot: "Car Weight vs. Horsepower".

        # Create scatter plot
        g = sns.relplot(x="weight", 
                        y="horsepower", 
                        data=mpg,
                        kind="scatter")

        # Add a title "Car Weight vs. Horsepower"
        g.fig.suptitle("Car Weight vs. Horsepower")

        # Show plot
        plt.show()

![Image93](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/22410eed-df35-49bf-b178-4225ebd150ec)

# Adding titles and labels: Part 2

**Personal notes:**

Adding a title to an AxesSubplot:

```python
g.set_title("New Title", y=1.03)
```

Similar to before, you need to have a variable assigned to the plot, and you can use the `set_title()` parameter to add or change the title. The `y` parameter can also be used here to adjust the height.

Titles in subplots - If you want to use the variable name in the title:

```python
g.set_titles("This is {col_name}")
```

By using the `{col_name}` parameter, you can differentiate the subplots using the variable names.

Adding axis labels:

```python
g.set(xlabel="New X Label", ylabel="New Y Label")
```

You can define the `xlabel` and `ylabel` parameters to add or change the labels associated with each axis. This can be used with both FacetGrid and AxesSubplot objects.

Rotating the X-axis label:

```python
plt.xticks(rotation=90)
```

After creating the plot, you can use `plt.xticks` and set the rotation angle of the label. Setting it to 90 will make the label vertical. This can be used with both FacetGrid and AxesSubplot objects.

**Exercises:**

**Adding a title and axis labels**

Let's continue to look at the miles per gallon dataset. This time we'll create a line plot to answer the question: How does the average miles per gallon achieved by cars change over time for each of the three places of origin? To improve the readability of this plot, we'll add a title and more informative axis labels.

In the code provided, we create the line plot using the lineplot() function. Note that lineplot() does not support the creation of subplots, so it returns an AxesSubplot object instead of an FacetGrid object.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Add the following title to the plot: "Average MPG Over Time".

-Label the x-axis as "Car Model Year" and the y-axis as "Average MPG"

        # Create line plot
        g = sns.lineplot(x="model_year", y="mpg_mean", 
                        data=mpg_mean,
                        hue="origin")

        # Add a title "Average MPG Over Time"
        g.set_title("Average MPG Over Time")

        # Add x-axis and y-axis labels
        g.set(xlabel="Car Model Year" , ylabel="Average MPG")


        # Show plot
        plt.show()

![Image94](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/68f78a06-8be2-4e32-aaaf-18442143b7c0)


**Rotating x-tick labels**

In this exercise, we'll continue looking at the miles per gallon dataset. In the code provided, we create a point plot that displays the average acceleration for cars in each of the three places of origin. Note that the "acceleration" variable is the time to accelerate from 0 to 60 miles per hour, in seconds. Higher values indicate slower acceleration.

Let's use this plot to practice rotating the x-tick labels. Recall that the function to rotate x-tick labels is a standalone Matplotlib function and not a function applied to the plot object itself.

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instruction:

-Rotate the x-tick labels 90 degrees.

        # Create point plot
        sns.catplot(x="origin", 
                    y="acceleration", 
                    data=mpg, 
                    kind="point", 
                    join=False, 
                    capsize=0.1)

        # Rotate x-tick labels
        plt.xticks(rotation=90)

        # Show plot
        plt.show()

![Image95](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/bd887455-bf2d-4b0f-ba10-0bc72dafb14b)


# Putting it all together

**Exercises:**

**Box plot with subgroups**

In this exercise, we'll look at the dataset containing responses from a survey given to young people. One of the questions asked of the young people was: "Are you interested in having pets?" Let's explore whether the distribution of ages of those answering "yes" tends to be higher or lower than those answering "no", controlling for gender.

Instructions:

-Set the color palette to "Blues".

-Add subgroups to color the box plots based on "Interested in Pets".

-Set the title of the FacetGrid object g to "Age of Those Interested in Pets vs. Not".

-Make the plot display using a Matplotlib function.

        # Set palette to "Blues"
        sns.set_palette("Blues")

        # Adjust to add subgroups based on "Interested in Pets"
        g = sns.catplot(x="Gender",
                        y="Age", data=survey_data, 
                        kind="box", hue="Interested in Pets")

        # Set title to "Age of Those Interested in Pets vs. Not"
        g.fig.suptitle("Age of Those Interested in Pets vs. Not")

        # Show plot
        plt.show()

![Image96](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/cff16c64-3119-4ad6-826e-7ec930083d68)


**Bar plot with subgroups and subplots**

In this exercise, we'll return to our young people survey dataset and investigate whether the proportion of people who like techno music ("Likes Techno") varies by their gender ("Gender") or where they live ("Village - town"). This exercise will give us an opportunity to practice the many things we've learned throughout this course!

We've already imported Seaborn as sns and matplotlib.pyplot as plt.

Instructions:

-Set the figure style to "dark".

-Adjust the bar plot code to add subplots based on "Gender", arranged in columns.

-Add the title "Percentage of Young People Who Like Techno" to this FacetGrid plot.

-Label the x-axis "Location of Residence" and y-axis "% Who Like Techno".

        # Set the figure style to "dark"
        sns.set_style("dark")

        # Adjust to add subplots per gender
        g = sns.catplot(x="Village - town", y="Likes Techno", 
                        data=survey_data, kind="bar",
                        col="Gender")

        # Add title and axis labels
        g.fig.suptitle("Percentage of Young People Who Like Techno", y=1.02)
        g.set(xlabel="Location of Residence", 
            ylabel="% Who Like Techno")

        # Show plot
        plt.show()

![Image97](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/14e36dc4-3861-4f04-b6bc-3a920f5c1f8e)


