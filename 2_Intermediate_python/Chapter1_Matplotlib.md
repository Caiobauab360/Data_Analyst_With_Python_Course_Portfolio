# Intermediate Python Course

**Course Description:**

Learning Python is crucial for any aspiring data science practitioner. Learn to visualize real data with Matplotlib’s functions and get acquainted with data structures such as the dictionary and pandas DataFrame. This four-hour intermediate course will help you to build on your existing Python skills and explore new Python applications and functions that expand your repertoire and help you work more efficiently.

You'll discover how dictionaries offer an alternative to Python lists, and why the pandas dataframe is the most popular way of working with tabular data. In the second chapter of this course, you’ll find out how you can create and manipulate datasets, and how to access them using these structures. Hands-on practice throughout the course will build your confidence in each area.

As you progress, you’ll look at logic, control flow, filtering and loops. These functions work to control decision-making in Python programs and help you to perform more operations with your data, including repeated statements. You’ll finish the course by applying all of your new skills by using hacker statistics to calculate your chances of winning a bet.

Once you’ve completed all of the chapters, you’ll be ready to apply your new skills in your job, new career, or personal project, and be prepared to move onto more advanced Python learning.

# MatPlotlib

**Description:**

Data visualization is a key skill for aspiring data scientists. Matplotlib makes it easy to create meaningful and insightful plots. In this chapter, you’ll learn how to build various types of plots, and customize them to be more visually appealing and interpretable.

**Personal notes:**

Plotting graphs with Python:

Import the Matplotlib library as plt with the command import matplotlib.pyplot as plt.

Assuming you have two lists, one with years and the other with the world population, you can create a graph with this information:

Use plt.plot(year, pop) where the first argument corresponds to the horizontal axis, and the second argument corresponds to the vertical axis.

To display how the graph looks before adding more information, use plt.show().

Scatter plot - a scatter graph:

To create a scatter graph, you can use plt.scatter(year, pop). This works similarly to the plot function, but it creates a scatter graph where Python doesn't connect the points with a line.

**Exercises:**

**Line plot (1)**

With matplotlib, you can create a bunch of different plots in Python. The most basic plot is the line plot. A general recipe is given here.

import matplotlib.pyplot as plt

plt.plot(x,y)

plt.show()

In the video, you already saw how much the world population has grown over the past years. Will it continue to do so? The world bank has estimates of the world population for the years 1950 up to 2100. The years are loaded in your workspace as a list called year, and the corresponding populations as a list called pop.

This course touches on a lot of concepts you may have forgotten, so if you ever need a quick refresher, download the Python For Data Science Cheat Sheet and keep it handy!

Instructions:

-print() the last item from both the year and the pop list to see what the predicted population for the year 2100 is. Use two print() functions.

-Before you can start, you should import matplotlib.pyplot as plt. pyplot is a sub-package of matplotlib, hence the dot.

-Use plt.plot() to build a line plot. year should be mapped on the horizontal axis, pop on the vertical axis. Don't forget to finish off with the plt.show() function to actually display the plot.

    # Print the last item from year and pop
    print(year[-1])
    print(pop[-1])

    # Import matplotlib.pyplot as plt
    import matplotlib.pyplot as plt

    # Make a line plot: year on the x-axis, pop on the y-axis
    plt.plot(year, pop)

    # Display the plot with plt.show()
    plt.show()

![image2](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/6fd978ac-aab9-4de8-b102-b683770b135f)

**Line Plot (2): Interpretation**

Have another look at the plot you created in the previous exercise; it's shown on the right. Based on the plot, in approximately what year will there be more than ten billion human beings on this planet?

![image1](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/4949cc3f-e7eb-4fa9-bb37-0cf668855c25)

    2060

**Line plot (3)**

Now that you've built your first line plot, let's start working on the data that professor Hans Rosling used to build his beautiful bubble chart. It was collected in 2007. Two lists are available for you:

life_exp which contains the life expectancy for each country and
gdp_cap, which contains the GDP per capita (i.e. per person) for each country expressed in US Dollars.
GDP stands for Gross Domestic Product. It basically represents the size of the economy of a country. Divide this by the population and you get the GDP per capita.

matplotlib.pyplot is already imported as plt, so you can get started straight away.

Instructions:

-Print the last item from both the list gdp_cap, and the list life_exp; it is information about Zimbabwe.

-Build a line chart, with gdp_cap on the x-axis, and life_exp on the y-axis. Does it make sense to plot this data on a line plot?

-Don't forget to finish off with a plt.show() command, to actually display the plot.

    # Print the last item of gdp_cap and life_exp
    print(gdp_cap[-1])
    print(life_exp[-1])

    # Make a line plot, gdp_cap on the x-axis, life_exp on the y-axis
    plt.plot(gdp_cap,life_exp)

    # Display the plot
    plt.show()

![image3](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/8c5faddc-034e-4f0e-9b76-c2a8c8a3050b)

**Scatter Plot (1)**

When you have a time scale along the horizontal axis, the line plot is your friend. But in many other cases, when you're trying to assess if there's a correlation between two variables, for example, the scatter plot is the better choice. Below is an example of how to build a scatter plot.

import matplotlib.pyplot as plt

plt.scatter(x,y)

plt.show()

Let's continue with the gdp_cap versus life_exp plot, the GDP and life expectancy data for different countries in 2007. Maybe a scatter plot will be a better alternative?

Again, the matplotlib.pyplot package is available as plt.

Instructions:

-Change the line plot that's coded in the script to a scatter plot.

-A correlation will become clear when you display the GDP per capita on a logarithmic scale. Add the line plt.xscale('log').

-Finish off your script with plt.show() to display the plot.

    # Change the line plot below to a scatter plot
    plt.scatter(gdp_cap, life_exp)

    # Put the x-axis on a logarithmic scale
    plt.xscale('log')

    # Show plot
    plt.show()

![image4](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/a191b559-089f-49db-9994-2664ce7dca66)

**Scatter plot (2)**

In the previous exercise, you saw that the higher GDP usually corresponds to a higher life expectancy. In other words, there is a positive correlation.

Do you think there's a relationship between population and life expectancy of a country? The list life_exp from the previous exercise is already available. In addition, now also pop is available, listing the corresponding populations for the countries in 2007. The populations are in millions of people.

Instructions:

-Start from scratch: import matplotlib.pyplot as plt.

-Build a scatter plot, where pop is mapped on the horizontal axis, and life_exp is mapped on the vertical axis.

-Finish the script with plt.show() to actually display the plot. Do you see a correlation?

    # Import package
    import matplotlib.pyplot as plt

    # Build Scatter plot
    plt.scatter(pop, life_exp)

    # Show plot
    plt.show()

![Image5](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/68780bd0-9a10-46de-846a-945625e5bf4f)


# Histogram

**Personal notes:**

- `x` = a list of values.
- `bins` = the number of bins you want to separate the values into.

To create a histogram using this information, you can use the code:

- `plt.hist(x, bins=)` - where `x` is the list created earlier, and `bins` will default to 10 if not specified.

To clear the created histogram:

- `plt.clf()` - Use this command to clear the histogram.

**Exercises:**

**Build a histogram (1)**

life_exp, the list containing data on the life expectancy for different countries in 2007, is available in your Python shell.

To see how life expectancy in different countries is distributed, let's create a histogram of life_exp.

matplotlib.pyplot is already available as plt.

Instructions:

-Use plt.hist() to create a histogram of the values in life_exp. Do not specify the number of bins; Python will set the number of bins to 10 by default for you.

-Add plt.show() to actually display the histogram. Can you tell which bin contains the most observations?

    # Create histogram of life_exp data
    plt.hist(life_exp)

    # Display histogram
    plt.show()

![Image6](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/25039e6f-dd1b-4553-8258-3685cc35abe6)

**Build a histogram (2): bins**

In the previous exercise, you didn't specify the number of bins. By default, Python sets the number of bins to 10 in that case. The number of bins is pretty important. Too few bins will oversimplify reality and won't show you the details. Too many bins will overcomplicate reality and won't show the bigger picture.

To control the number of bins to divide your data in, you can set the bins argument.

That's exactly what you'll do in this exercise. You'll be making two plots here. The code in the script already includes plt.show() and plt.clf() calls; plt.show() displays a plot; plt.clf() cleans it up again so you can start afresh.

As before, life_exp is available and matplotlib.pyplot is imported as plt.

Instructions:

-Build a histogram of life_exp, with 5 bins. Can you tell which bin contains the most observations?

-Build another histogram of life_exp, this time with 20 bins. Is this better?

    # Build histogram with 5 bins
    plt.hist(life_exp, bins = 5)

    # Show and clean up plot
    plt.show()
    plt.clf()

    # Build histogram with 20 bins
    plt.hist(life_exp, bins = 20)

    # Show and clean up again
    plt.show()
    plt.clf()

![Image7](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/425dd4ad-b9db-46b0-ba16-e0906e35720b)

![Image8](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e8f6bddb-7554-4cbd-9fe1-d80b569c77c4)

**Build a histogram (3): compare**

In the video, you saw population pyramids for the present day and for the future. Because we were using a histogram, it was very easy to make a comparison.

Let's do a similar comparison. life_exp contains life expectancy data for different countries in 2007. You also have access to a second list now, life_exp1950, containing similar data for 1950. Can you make a histogram for both datasets?

You'll again be making two plots. The plt.show() and plt.clf() commands to render everything nicely are already included. Also matplotlib.pyplot is imported for you, as plt.

Instructions:

-Build a histogram of life_exp with 15 bins.

-Build a histogram of life_exp1950, also with 15 bins. Is there a big difference with the histogram for the 2007 data?

    # Histogram of life_exp, 15 bins
    plt.hist(life_exp, bins = 15)

    # Show and clear plot
    plt.show()
    plt.clf()

    # Histogram of life_exp1950, 15 bins
    plt.hist(life_exp1950, bins = 15)

    # Show and clear plot again
    plt.show()
    plt.clf()

![Image9](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/be8d997d-fdb2-4b8a-b413-c8c24eecb4c4)

![Image10](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/bce7b673-1d44-49aa-943f-3aad01f80dd1)


**Choose the right plot (1)**

You're a professor teaching Data Science with Python, and you want to visually assess if the grades on your exam follow a particular distribution. Which plot do you use?

    Histogram

**Choose the right plot (2)**

You're a professor in Data Analytics with Python, and you want to visually assess if longer answers on exam questions lead to higher grades. Which plot do you use?

    Scatter plot

# Customization

**Personal notes:**

To label the x and y axes and add a title to your plot, you can use the following commands:

- `plt.xlabel('')` - Use this to add a title to the x-axis. Make sure to enclose the title in a string.
- `plt.ylabel('')` - Use this to add a title to the y-axis.
- `plt.title('')` - To add an overall title to the graph.

To customize the y-axis scale, you can use:

- `plt.yticks([])` - This allows you to change the scale being used on the y-axis. For example, you can provide a list with the same number of elements, but this time, they can be strings to label the elements in a more meaningful way. For instance, `[2B, 4B, 6B, 8B, 10B]` to indicate values in billions.

To add more elements to the plot:

- `year = [] + year` - You can use this to add more elements to the plot.

**Exercises:**

**Labels**

It's time to customize your own plot. This is the fun part, you will see your plot come to life!

You're going to work on the scatter plot with world development data: GDP per capita on the x-axis (logarithmic scale), life expectancy on the y-axis. The code for this plot is available in the script.

As a first step, let's add axis labels and a title to the plot. You can do this with the xlabel(), ylabel() and title() functions, available in matplotlib.pyplot. This sub-package is already imported as plt.

Instructions:

-The strings xlab and ylab are already set for you. Use these variables to set the label of the x- and y-axis.

-The string title is also coded for you. Use it to add a title to the plot.

-After these customizations, finish the script with plt.show() to actually display the plot.

    # Basic scatter plot, log scale
    plt.scatter(gdp_cap, life_exp)
    plt.xscale('log') 

    # Strings
    xlab = 'GDP per Capita [in USD]'
    ylab = 'Life Expectancy [in years]'
    title = 'World Development in 2007'

    # Add axis labels
    plt.xlabel(xlab)
    plt.ylabel(ylab)

    # Add title
    plt.title(title)

    # After customizing, display the plot
    plt.show()

![Image11](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e2ea2cb5-811d-49e0-96a2-6bb00fda7034)

**Ticks**

The customizations you've coded up to now are available in the script, in a more concise form.

In the video, Hugo has demonstrated how you could control the y-ticks by specifying two arguments:

plt.yticks([0,1,2], ["one","two","three"])

In this example, the ticks corresponding to the numbers 0, 1 and 2 will be replaced by one, two and three, respectively.

Let's do a similar thing for the x-axis of your world development chart, with the xticks() function. The tick values 1000, 10000 and 100000 should be replaced by 1k, 10k and 100k. To this end, two lists have already been created for you: tick_val and tick_lab.

Instructions:

-Use tick_val and tick_lab as inputs to the xticks() function to make the the plot more readable.

-As usual, display the plot with plt.show() after you've added the customizations.

    # Scatter plot
    plt.scatter(gdp_cap, life_exp)

    # Previous customizations
    plt.xscale('log') 
    plt.xlabel('GDP per Capita [in USD]')
    plt.ylabel('Life Expectancy [in years]')
    plt.title('World Development in 2007')

    # Definition of tick_val and tick_lab
    tick_val = [1000, 10000, 100000]
    tick_lab = ['1k', '10k', '100k']

    # Adapt the ticks on the x-axis
    plt.xticks(tick_val, tick_lab)

    # After customizing, display the plot
    plt.show()  

![Image12](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/825c3b86-d8ae-4368-88f3-7596fb61cf62)

**Sizes**

Right now, the scatter plot is just a cloud of blue dots, indistinguishable from each other. Let's change this. Wouldn't it be nice if the size of the dots corresponds to the population?

To accomplish this, there is a list pop loaded in your workspace. It contains population numbers for each country expressed in millions. You can see that this list is added to the scatter method, as the argument s, for size.

Instructions:

-Run the script to see how the plot changes.

-Looks good, but increasing the size of the bubbles will make things stand out more.

-Import the numpy package as np.

-Use np.array() to create a numpy array from the list pop. Call this NumPy array np_pop.

-Double the values in np_pop setting the value of np_pop equal to np_pop * 2. Because np_pop is a NumPy array, each array element will be doubled.

-Change the s argument inside plt.scatter() to be np_pop instead of pop.

    # Import numpy as np
    import numpy as np

    # Store pop as a numpy array: np_pop
    np_pop = np.array(pop)

    # Double np_pop
    np_pop = np_pop * 2

    # Update: set s argument to np_pop
    plt.scatter(gdp_cap, life_exp, s = np_pop)

    # Previous customizations
    plt.xscale('log') 
    plt.xlabel('GDP per Capita [in USD]')
    plt.ylabel('Life Expectancy [in years]')
    plt.title('World Development in 2007')
    plt.xticks([1000, 10000, 100000],['1k', '10k', '100k'])

    # Display the plot
    plt.show()

![Image13](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e6f59b58-0f71-415d-8a78-7b311cdb45b1)

**Colors**

The code you've written up to now is available in the script.

The next step is making the plot more colorful! To do this, a list col has been created for you. It's a list with a color for each corresponding country, depending on the continent the country is part of.

How did we make the list col you ask? The Gapminder data contains a list continent with the continent each country belongs to. A dictionary is constructed that maps continents onto colors:

dict = {

'Asia':'red',

'Europe':'green',

'Africa':'blue',

'Americas':'yellow',

'Oceania':'black'
}

Nothing to worry about now; you will learn about dictionaries in the next chapter.

Instructions:

-Add c = col to the arguments of the plt.scatter() function.

-Change the opacity of the bubbles by setting the alpha argument to 0.8 inside plt.scatter(). Alpha can be set from zero to one, where zero is totally transparent, and one is not at all transparent.

    # Specify c and alpha inside plt.scatter()
    plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c = col, alpha =0.8)

    # Previous customizations
    plt.xscale('log') 
    plt.xlabel('GDP per Capita [in USD]')
    plt.ylabel('Life Expectancy [in years]')
    plt.title('World Development in 2007')
    plt.xticks([1000,10000,100000], ['1k','10k','100k'])

    # Show the plot
    plt.show()

![Image14](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d2d31bea-37fe-49c4-94bb-ef0e7f92d191)

**Additional Customizations**

If you have another look at the script, under # Additional Customizations, you'll see that there are two plt.text() functions now. They add the words "India" and "China" in the plot.

Instructions:

-Add plt.grid(True) after the plt.text() calls so that gridlines are drawn on the plot.

    # Scatter plot
    plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c = col, alpha = 0.8)

    # Previous customizations
    plt.xscale('log') 
    plt.xlabel('GDP per Capita [in USD]')
    plt.ylabel('Life Expectancy [in years]')
    plt.title('World Development in 2007')
    plt.xticks([1000,10000,100000], ['1k','10k','100k'])

    # Additional customizations
    plt.text(1550, 71, 'India')
    plt.text(5700, 80, 'China')

    # Add grid() call
    plt.grid(True)

    # Show the plot
    plt.show()

![Image15](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/e6e0659a-8873-46bf-8492-af0bb8cc5ee9)

**Interpretation**

If you have a look at your colorful plot, it's clear that people live longer in countries with a higher GDP per capita. No high income countries have really short life expectancy, and no low income countries have very long life expectancy. Still, there is a huge difference in life expectancy between countries on the same income level. Most people live in middle income countries where difference in lifespan is huge between countries; depending on how income is distributed and how it is used.

What can you say about the plot?

![Image16](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/12b0ea5d-82e6-4de3-a493-3a4caf8ff880)

    The countries in blue, corresponding to Africa, have both low life expectancy and a low GDP per capita.
