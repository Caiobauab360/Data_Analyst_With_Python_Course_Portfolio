# Logic, Control Flow and Filtering

Description:

Boolean logic is the foundation of decision-making in Python programs. Learn about different comparison operators, how to combine them with Boolean operators, and how to use the Boolean outcomes in control structures. You'll also learn to filter data in pandas DataFrames using logic.

# Comparison Operators

**Exercises:**

**Equality**

To check if two Python values, or variables, are equal you can use ==. To check for inequality, you need !=. As a refresher, have a look at the following examples that all result in True. Feel free to try them out in the IPython Shell.

2 == (1 + 1)

"intermediate" != "python"

True != False

"Python" != "python"

When you write these comparisons in a script, you will need to wrap a print() function around them to see the output.

Instructions:

-In the editor on the right, write code to see if True equals False.

-Write Python code to check if -5 * 15 is not equal to 75.

-Ask Python whether the strings "pyscript" and "PyScript" are equal.

-What happens if you compare booleans and integers? Write code to see if True and 1 are equal.

    # Comparison of booleans
    print(True == False)

    # Comparison of integers
    print((-5 * 15) != 75)

    # Comparison of strings
    print("pyscript" == "PyScript")

    # Compare a boolean with an integer
    print(True == 1)

**Greater and less than**

In the video, Hugo also talked about the less than and greater than signs, < and > in Python. You can combine them with an equals sign: <= and >=. Pay attention: <= is valid syntax, but =< is not.

All Python expressions in the following code chunk evaluate to True:

3 < 4

3 <= 4

"alpha" <= "beta"

Remember that for string comparison, Python determines the relationship based on alphabetical order.

Instructions:

-Write Python expressions, wrapped in a print() function, to check whether:

-x is greater than or equal to -10. x has already been defined for you.

-"test" is less than or equal to y. y has already been defined for you.

-True is greater than False.

    # Comparison of integers
    x = -3 * 6
    print(x >= -10)


    # Comparison of strings
    y = "test"
    print('test' <= y)

    # Comparison of booleans
    print(True > False)

**Compare arrays**

Out of the box, you can also use comparison operators with NumPy arrays.

Remember areas, the list of area measurements for different rooms in your house from Introduction to Python? This time there's two NumPy arrays: my_house and your_house. They both contain the areas for the kitchen, living room, bedroom and bathroom in the same order, so you can compare them.

Instructions:

-Using comparison operators, generate boolean arrays that answer the following questions:

-Which areas in my_house are greater than or equal to 18?

-You can also compare two NumPy arrays element-wise. Which areas in my_house are smaller than the ones in your_house?

-Make sure to wrap both commands in a print() statement so that you can inspect the output!

    # Create arrays
    import numpy as np
    my_house = np.array([18.0, 20.0, 10.75, 9.50])
    your_house = np.array([14.0, 24.0, 14.25, 9.0])

    # my_house greater than or equal to 18
    print(my_house >= 18)

    # my_house less than your_house
    print(my_house < your_house)

# Boolean Operators

**Personal notes:**

"And," "Or," "Not" are logical operators used in Python:

- *And*: Takes two Booleans and returns true if both are true.

- *Or:* Similar to "And," it returns true if any of the compared Booleans is true.

- *Not:* Used to negate a result. `Not True` equals false, and `Not False` equals true.

In NumPy, you can't use these functions directly; you need to use their NumPy equivalents:

- `np.logical_and()`
- `np.logical_or()`
- `np.logical_not()`

For example, to find the BMI for two distinct comparisons, you would use:

- `bmi[np.logical_and(bmi > 21, bmi < 22)]`

**Exercises:**

**and, or, not (1)**

A boolean is either 1 or 0, True or False. With boolean operators such as and, or and not, you can combine these booleans to perform more advanced queries on your data.

In the sample code, two variables are defined: my_kitchen and your_kitchen, representing areas.

Instructions:

-Write Python expressions, wrapped in a print() function, to check whether:

-my_kitchen is bigger than 10 and smaller than 18.

-my_kitchen is smaller than 14 or bigger than 17.

-double the area of my_kitchen is smaller than triple the area of your_kitchen.

    # Define variables
    my_kitchen = 18.0
    your_kitchen = 14.0

    # my_kitchen bigger than 10 and smaller than 18?
    print(my_kitchen > 10 and my_kitchen < 18)

    # my_kitchen smaller than 14 or bigger than 17?
    print(my_kitchen < 14 or my_kitchen > 17)

    # Double my_kitchen smaller than triple your_kitchen?
    print(my_kitchen*2 < your_kitchen*3)

**and, or, not (2)**

To see if you completely understood the boolean operators, have a look at the following piece of Python code:

x = 8
y = 9
not(not(x < 3) and not(y > 14 or y > 10))
What will the result be if you execute these three commands in the IPython Shell?

NB: Notice that not has a higher priority than and and or, it is executed first.

    False

**Boolean operators with NumPy**

Before, the operational operators like < and >= worked with NumPy arrays out of the box. Unfortunately, this is not true for the boolean operators and, or, and not.

To use these operators with NumPy, you will need np.logical_and(), np.logical_or() and np.logical_not(). Here's an example on the my_house and your_house arrays from before to give you an idea:

np.logical_and(my_house > 13, 

               your_house < 15)

Instructions:

-Generate boolean arrays that answer the following questions:

-Which areas in my_house are greater than 18.5 or smaller than 10?

-Which areas are smaller than 11 in both my_house and your_house? Make sure to wrap both commands in print() statement, so that you can inspect the output.

    # Create arrays
    import numpy as np
    my_house = np.array([18.0, 20.0, 10.75, 9.50])
    your_house = np.array([14.0, 24.0, 14.25, 9.0])

    # my_house greater than 18.5 or smaller than 10
    print(np.logical_or(my_house > 18.5, my_house < 10))

    # Both my_house and your_house smaller than 11
    print(np.logical_and(my_house < 11, your_house < 11))

# If, Elif, Else

**Personal notes:**

These are conditional statements in Python:

- *Else:* You don't need to specify a condition for "Else." It serves as a fallback when none of the preceding conditions are met. If none of the previous `if` or `elif` conditions are true, the code block under `else` will execute.

- *Elif:* It works like an additional `if` when you need to add another condition in the logic. However, the program will execute the code block associated with the first true condition it encounters and then stop. If none of the conditions are true, it may execute the code block under `else` if it exists.

**Exercises:**

**Warmup**

To experiment with if and else a bit, have a look at this code sample:

area = 10.0

if(area < 9) :

print("small")

elif(area < 12) :

print("medium")

else :

print("large")

What will the output be if you run this piece of code in the IPython Shell?

    Medium

**if**

It's time to take a closer look around in your house.

Two variables are defined in the sample code: room, a string that tells you which room of the house we're looking at, and area, the area of that room.

Instructions:

-Examine the if statement that prints out "looking around in the kitchen." if room equals "kit".

-Write another if statement that prints out "big place!" if area is greater than 15.
    
    # Define variables
    room = "kit"
    area = 14.0

    # if statement for room
    if room == "kit" :
        print("looking around in the kitchen.")

    # if statement for area
    if area > 15 :
        print("big place!")

**Add else**

In the script, the if construct for room has been extended with an else statement so that "looking around elsewhere." is printed if the condition room == "kit" evaluates to False.

Can you do a similar thing to add more functionality to the if construct for area?

Instructions:

-Add an else statement to the second control structure so that "pretty small." is printed out if area > 15 evaluates to False.

    # Define variables
    room = "kit"
    area = 14.0

    # if-else construct for room
    if room == "kit" :
        print("looking around in the kitchen.")
    else :
        print("looking around elsewhere.")

    # if-else construct for area
    if area > 15 :
        print("big place!")
    else :
        print("pretty small.")

**Customize further: elif**

It's also possible to have a look around in the bedroom. The sample code contains an elif part that checks if room equals "bed". In that case, "looking around in the bedroom." is printed out.

It's up to you now! Make a similar addition to the second control structure to further customize the messages for different values of area.

Instructions:

-Add an elif to the second control structure such that "medium size, nice!" is printed out if area is greater than 10.

    # Define variables
    room = "bed"
    area = 14.0

    # if-elif-else construct for room
    if room == "kit" :
        print("looking around in the kitchen.")
    elif room == "bed":
        print("looking around in the bedroom.")
    else :
        print("looking around elsewhere.")

    # if-elif-else construct for area
    if area > 15 :
        print("big place!")
    elif area > 10:
        print("medium size, nice!")
    else :
        print("pretty small.")


# Filtering pandas DataFrame

**Personal notes:**

Filtering pandas DataFrames can be achieved in three steps:

Select the desired column(s).

Perform the desired comparison(s).

Use the result to select specific items or rows from the DataFrame.

To use and, or, and not in filtering operations with pandas DataFrames, you can follow a similar approach to how it's done with NumPy arrays. These logical operators help you create complex conditions and filter data based on multiple criteria.

**Exercises:**

**Driving right (1)**

Remember that cars dataset, containing the cars per 1000 people (cars_per_cap) and whether people drive right (drives_right) for different countries (country)? The code that imports this data in CSV format into Python as a DataFrame is included in the script.

In the video, you saw a step-by-step approach to filter observations from a DataFrame based on boolean arrays. Let's start simple and try to find all observations in cars where drives_right is True.

drives_right is a boolean column, so you'll have to extract it as a Series and then use this boolean Series to select observations from cars

Instructions:

-Extract the drives_right column as a Pandas Series and store it as dr.

-Use dr, a boolean Series, to subset the cars DataFrame. Store the resulting selection in sel.

-Print sel, and assert that drives_right is True for all observations.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Extract drives_right column as Series: dr
    dr = cars['drives_right']

    # Use dr to subset cars: sel
    sel = cars[dr]

    # Print sel
    print(sel)

**Driving right (2)**

The code in the previous example worked fine, but you actually unnecessarily created a new variable dr. You can achieve the same result without this intermediate variable. Put the code that computes dr straight into the square brackets that select observations from cars.

Instructions:

-Convert the code to a one-liner that calculates the variable sel as before.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Convert code to a one-liner
    sel = cars[cars['drives_right']]
    
    # Print sel
    print(sel)

**Cars per capita (1)**

Let's stick to the cars data some more. This time you want to find out which countries have a high cars per capita figure. In other words, in which countries do many people have a car, or maybe multiple cars.

Similar to the previous example, you'll want to build up a boolean Series, that you can then use to subset the cars DataFrame to select certain observations. If you want to do this in a one-liner, that's perfectly fine!

Instructions:

-Select the cars_per_cap column from cars as a Pandas Series and store it as cpc.

-Use cpc in combination with a comparison operator and 500. You want to end up with a boolean Series that's True if the corresponding country has a cars_per_cap of more than 500 and False otherwise. Store this boolean Series as many_cars.

-Use many_cars to subset cars, similar to what you did before. Store the result as car_maniac.

-Print out car_maniac to see if you got it right.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Create car_maniac: observations that have a cars_per_cap over 500
    cpc = cars['cars_per_cap']
    many_cars = cpc > 500
    car_maniac = cars[many_cars]

    # Print car_maniac
    print(car_maniac)

**Cars per capita (2)**

Remember about np.logical_and(), np.logical_or() and np.logical_not(), the NumPy variants of the and, or and not operators? You can also use them on Pandas Series to do more advanced filtering operations.

Take this example that selects the observations that have a cars_per_cap between 10 and 80. Try out these lines of code step by step to see what's happening.

cpc = cars['cars_per_cap']

between = np.logical_and(cpc > 10, cpc < 80)

medium = cars[between]

Instructions:

-Use the code sample provided to create a DataFrame medium, that includes all the observations of cars that have a cars_per_cap between 100 and 500.

-Print out medium.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Import numpy, you'll need this
    import numpy as np

    # Create medium: observations with cars_per_cap between 100 and 500
    cpc = cars['cars_per_cap']
    between = np.logical_and(cpc > 100, cpc < 500)
    medium = cars[between]

    # Print medium
    print(medium)

