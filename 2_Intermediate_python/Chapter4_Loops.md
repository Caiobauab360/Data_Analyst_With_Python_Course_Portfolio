# Loops

Description:

There are several techniques you can use to repeatedly execute Python code. While loops are like repeated if statements, the for loop iterates over all kinds of data structures. Learn all about them in this chapter.

# While loop

**Personal notes:**

The `while` loop in Python works similarly to an `if` statement, but it is designed as a loop. It will continue to repeat the code block as long as the condition specified in the `while` statement remains true. Once the condition becomes false, the loop terminates, and the program continues with the next line of code after the `while` loop. It's a way to create a repetitive structure in your program based on a condition.

**Exercises:**

**while: warming up**

The while loop is like a repeated if statement. The code is executed over and over again, as long as the condition is True. Have another look at its recipe.

while condition :

expression

Can you tell how many printouts the following while loop will do?

x = 1

while x < 4 :

print(x)

x = x + 1

    Awnser = 3

**Basic while loop**

Below you can find the example from the video where the error variable, initially equal to 50.0, is divided by 4 and printed out on every run:

error = 50.0

while error > 1 :

error = error / 4

print(error)

This example will come in handy, because it's time to build a while loop yourself! We're going to code a while loop that implements a very basic control system for an inverted pendulum. If there's an offset from standing perfectly straight, the while loop will incrementally fix this offset.

Note that if your while loop takes too long to run, you might have made a mistake. In particular, remember to indent the contents of the loop using four spaces or auto-indentation!

Instructions:

-Create the variable offset with an initial value of 8.

-Code a while loop that keeps running as long as offset is not equal to 0. Inside the while loop:

-Print out the sentence "correcting...".

-Next, decrease the value of offset by 1. You can do this with offset = offset - 1.

-Finally, still within your loop, print out offset so you can see how it changes.

    # Initialize offset
    offset = 8

    # Code the while loop
    while offset != 0 :
        print("correcting...")
        offset = offset - 1
        print(offset)

**Add conditionals**

The while loop that corrects the offset is a good start, but what if offset is negative? You can try to run the following code where offset is initialized to -6:

#Initialize offset
offset = -6

#Code the while loop

while offset != 0 :

print("correcting...")

offset = offset - 1

print(offset)

but your session will be disconnected. The while loop will never stop running, because offset will be further decreased on every run. offset != 0 will never become False and the while loop continues forever.

Fix things by putting an if-else statement inside the while loop. If your code is still taking too long to run, you probably made a mistake!

Instructions:

-Inside the while loop, complete the if-else statement:

-If offset is greater than zero, you should decrease offset by 1.

-Else, you should increase offset by 1.

-If you've coded things correctly, hitting Submit Answer should work this time.

    # Initialize offset
    offset = -6

    # Code the while loop
    while offset != 0 :
        print("correcting...")
    if offset > 0 :
        offset = offset - 1
    else : 
        offset = offset + 1   
        print(offset)

# For loop

**Exercises:**

**Loop over a list**

Have another look at the for loop that Hugo showed in the video:

fam = [1.73, 1.68, 1.71, 1.89]

for height in fam : 

print(height)

As usual, you simply have to indent the code with 4 spaces to tell Python which code should be executed in the for loop.

The areas variable, containing the area of different rooms in your house, is already defined.

Instructions:

-Write a for loop that iterates over all elements of the areas list and prints out every element separately.

    # areas list
    areas = [11.25, 18.0, 20.0, 10.75, 9.50]

    # Code the for loop
    for elements in areas :
        print(elements)

**Indexes and values (1)**

Using a for loop to iterate over a list only gives you access to every list element in each run, one after the other. If you also want to access the index information, so where the list element you're iterating over is located, you can use enumerate().

As an example, have a look at how the for loop from the video was converted:

fam = [1.73, 1.68, 1.71, 1.89]

for index, height in enumerate(fam) :

print("person " + str(index) + ": " + str(height))

Instructions:

-Adapt the for loop in the sample code to use enumerate() and use two iterator variables.

-Update the print() statement so that on each run, a line of the form "room x: y" should be printed, where x is the index of the list element and y is the actual list element, i.e. the area. Make sure to print out this exact string, with the correct spacing.

    # areas list
    areas = [11.25, 18.0, 20.0, 10.75, 9.50]

    # Change for loop to use enumerate() and update print()
    for index, a in enumerate(areas) :
        print("room" + str(index) + ":" + str(a))

**Indexes and values (2)**

For non-programmer folks, room 0: 11.25 is strange. Wouldn't it be better if the count started at 1?

Instructions:

-Adapt the print() function in the for loop so that the first printout becomes "room 1: 11.25", the second one "room 2: 18.0" and so on.

    # areas list
    areas = [11.25, 18.0, 20.0, 10.75, 9.50]

    # Code the for loop
    for index, area in enumerate(areas) :
        index = index + 1
        print("room " + str(index) + ": " + str(area))

**Loop over list of lists**

Remember the house variable from the Intro to Python course? Have a look at its definition in the script. It's basically a list of lists, where each sublist contains the name and area of a room in your house.

It's up to you to build a for loop from scratch this time!

Instructions:

-Write a for loop that goes through each sublist of house and prints out the x is y sqm, where x is the name of the room and y is the area of the room.

    # house list of lists
    house = [["hallway", 11.25], 
             ["kitchen", 18.0], 
             ["living room", 20.0], 
             ["bedroom", 10.75], 
             ["bathroom", 9.50]]
         
    # Build a for loop from scratch
    for x in house :
        print("the " + x[0] + " is " + str(x[1]) + " sqm")
    
# Loop Data Structures, Part 1

**Exercises:**

**Loop over dictionary**

In Python 3, you need the items() method to loop over a dictionary:

world = { "afghanistan":30.55, 

"albania":2.77,

"algeria":39.21 }

for key, value in world.items() :

print(key + " -- " + str(value))

Remember the europe dictionary that contained the names of some European countries as key and their capitals as corresponding value? Go ahead and write a loop to iterate over it!

Instructions:

-Write a for loop that goes through each key:value pair of europe. On each iteration, "the capital of x is y" should be printed out, where x is the key and y is the value of the pair.

    # Definition of dictionary
    europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin',
              'norway':'oslo', 'italy':'rome', 'poland':'warsaw', 'austria':'vienna' }
          
    # Iterate over europe
    for key, value in europe.items() :
        print("the capital of " + key + " is " + str(value) )

**Loop over NumPy array**

If you're dealing with a 1D NumPy array, looping over all elements can be as simple as:

for x in my_array :

...

If you're dealing with a 2D NumPy array, it's more complicated. A 2D array is built up of multiple 1D arrays. To explicitly iterate over all separate elements of a multi-dimensional array, you'll need this syntax:

for x in np.nditer(my_array) :

...

Two NumPy arrays that you might recognize from the intro course are available in your Python session: np_height, a NumPy array containing the heights of Major League Baseball players, and np_baseball, a 2D NumPy array that contains both the heights (first column) and weights (second column) of those players.

Instructions:
-Import the numpy package under the local alias np.

-Write a for loop that iterates over all elements in np_height and prints out "x inches" for each element, where x is the value in the array.

-Write a for loop that visits every element of the np_baseball array and prints it out.

    # Import numpy as np
    import numpy as np

    # For loop over np_height
    for x in np_height :
        print(str(x) + " inches") 

    # For loop over np_baseball
    for x in np.nditer(np_baseball) :
        print(x)

# Loop Data Structures, Part 2

**Exercises:**

**Loop over DataFrame (1)**

Iterating over a Pandas DataFrame is typically done with the iterrows() method. Used in a for loop, every observation is iterated over and on every iteration the row label and actual row contents are available:

for lab, row in brics.iterrows() :

...

In this and the following exercises you will be working on the cars DataFrame. It contains information on the cars per capita and whether people drive right or left for seven countries in the world.

Instructions:

-Write a for loop that iterates over the rows of cars and on each iteration perform two print() calls: one to print out the row label and one to print out all of the rows contents.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Iterate over rows of cars
    for lab, row in cars.iterrows() :
        print(lab)
        print(row)

**Loop over DataFrame (2)**

The row data that's generated by iterrows() on every run is a Pandas Series. This format is not very convenient to print out. Luckily, you can easily select variables from the Pandas Series using square brackets:

for lab, row in brics.iterrows() :

print(row['country'])

Instructions:

-Using the iterators lab and row, adapt the code in the for loop such that the first iteration prints out "US: 809", the second iteration "AUS: 731", and so on.

-The output should be in the form "country: cars_per_cap". Make sure to print out this exact string (with the correct spacing).
You can use str() to convert your integer data to a string so that you can print it in conjunction with the country label.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Adapt for loop
    for lab, row in cars.iterrows() :
        print(lab)
        print(row)

**Add column (1)**

In the video, Hugo showed you how to add the length of the country names of the brics DataFrame in a new column:

for lab, row in brics.iterrows() :

brics.loc[lab, "name_length"] = len(row["country"])

You can do similar things on the cars DataFrame.

Instructions:

-Use a for loop to add a new column, named COUNTRY, that contains a uppercase version of the country names in the "country" column. You can use the string method upper() for this.

-To see if your code worked, print out cars. Don't indent this code, so that it's not part of the for loop.

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Code for loop that adds COUNTRY column
    for lab, row in cars.iterrows() :
        cars.loc[lab, 'COUNTRY'] = row['country'].upper()


    # Print cars
    print(cars)

**Add column (2)**

Using iterrows() to iterate over every observation of a Pandas DataFrame is easy to understand, but not very efficient. On every iteration, you're creating a new Pandas Series.

If you want to add a column to a DataFrame by calling a function on another column, the iterrows() method in combination with a for loop is not the preferred way to go. Instead, you'll want to use apply().

Compare the iterrows() version with the apply() version to get the same result in the brics DataFrame:

for lab, row in brics.iterrows() :

brics.loc[lab, "name_length"] = len(row["country"])

brics["name_length"] = brics["country"].apply(len)

We can do a similar thing to call the upper() method on every name in the country column. However, upper() is a method, so we'll need a slightly different approach:

Instructions:

-Replace the for loop with a one-liner that uses .apply(str.upper). The call should give the same result: a column COUNTRY should be added to cars, containing an uppercase version of the country names.

-As usual, print out cars to see the fruits of your hard labor

    # Import cars data
    import pandas as pd
    cars = pd.read_csv('cars.csv', index_col = 0)

    # Use .apply(str.upper)
    cars["COUNTRY"] = cars["country"].apply(str.upper)

    print(cars)