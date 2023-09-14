# Joining data with pandas course

**Course Description:**

Being able to combine and work with multiple datasets is an essential skill for any aspiring Data Scientist. pandas is a crucial cornerstone of the Python data science ecosystem, with Stack Overflow recording 5 million views for pandas questions. Learn to handle multiple DataFrames by combining, organizing, joining, and reshaping them using pandas. You'll work with datasets from the World Bank and the City Of Chicago. You will finish the course with a solid skillset for data-joining in pandas.

# Data Merging Basics

**Description:**

Learn how you can merge disparate data using inner joins. By combining information from multiple sources you’ll uncover compelling insights that may have previously been hidden. You’ll also learn how the relationship between those sources, such as one-to-one or one-to-many, can affect your result.

# Inner join

**Personal notes:**

Tables = DataFrame; merging = joining;

To merge DataFrames:

- DataFrame.merge(census, on="ward") - 

In this case, the first DataFrame declared before the .merge method is merged with the second DataFrame referred to as "census." The "on" parameter specifies the column from the first DataFrame for merging, which must exist in both DataFrames with the same name. The result is a new DataFrame with the first column being the selected column in "on," followed by the columns from the DataFrame in square brackets, and then the remaining columns from the DataFrame.merge.

An inner join returns only the rows with matching values in both merged tables. Columns with the same name are automatically modified with suffixes _x and _y for differentiation. The _x suffix belongs to the DataFrame from .merge, and the _y suffix belongs to the "census" DataFrame in the previous example.

- DataFrame.merge(census, on="ward", suffixes = ("_ward", "_cen")) - 

In this case, the tables are differentiated by the selected suffixes, making it easier to read the resulting table. The suffixes are added to all columns from both merged DataFrames with the same names;

*Remember that .merge returns only the rows where values match in both DataFrames.

**Exercises:**

**What column to merge on?**

Chicago provides a list of taxicab owners and vehicles licensed to operate within the city, for public safety. Your goal is to merge two tables together. One table is called taxi_owners, with info about the taxi cab company owners, and one is called taxi_veh, with info about each taxi cab vehicle. Both the taxi_owners and taxi_veh tables have been loaded for you and you can explore them in the IPython shell.

Choose the column you would use to merge the two tables on using the .merge() method.

    on='vid'

**Your first inner join**

You have been tasked with figuring out what the most popular types of fuel used in Chicago taxis are. To complete the analysis, you need to merge the taxi_owners and taxi_veh tables together on the vid column. You can then use the merged table along with the .value_counts() method to find the most common fuel_type.

Since you'll be working with pandas throughout the course, the package will be preloaded for you as pd in each exercise in this course. Also the taxi_owners and taxi_veh DataFrames are loaded for you.

Instructions: 

-Merge taxi_owners with taxi_veh on the column vid, and save the result to taxi_own_veh.

    # Merge the taxi_owners and taxi_veh tables
    taxi_own_veh = taxi_owners.merge(taxi_veh,on="vid")

    # Print the column names of the taxi_own_veh
    print(taxi_own_veh.columns)

-Set the left and right table suffixes for overlapping columns of the merge to _own and _veh, respectively.

    # Merge the taxi_owners and taxi_veh tables setting a suffix
    taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=("_own", "_veh"))

    # Print the column names of taxi_own_veh
    print(taxi_own_veh.columns)

-Select the fuel_type column from taxi_own_veh and print the value_counts() to find the most popular fuel_types used.

    # Merge the taxi_owners and taxi_veh tables setting a suffix
    taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=('_own','_veh'))

    # Print the value_counts to find the most popular fuel_type
    print(taxi_own_veh['fuel_type'].value_counts())

**Inner joins and number of rows returned**

All of the merges you have studied to this point are called inner joins. It is necessary to understand that inner joins only return the rows with matching values in both tables. You will explore this further by reviewing the merge between the wards and census tables, then comparing it to merges of copies of these tables that are slightly altered, named wards_altered, and census_altered. The first row of the wards column has been changed in the altered tables. You will examine how this affects the merge between them. The tables have been loaded for you.

For this exercise, it is important to know that the wards and census tables start with 50 rows.

Instructions:

-Merge wards and census on the ward column and save the result to wards_census.

    # Merge the wards and census tables on the ward column
    wards_census = wards.merge(census, on="ward")

    # Print the shape of wards_census
    print('wards_census table shape:', wards_census.shape)

-Merge the wards_altered and census tables on the ward column, and notice the difference in returned rows.

    # Print the first few rows of the wards_altered table to view the change 
    print(wards_altered[['ward']].head())

    # Merge the wards_altered and census tables on the ward column
    wards_altered_census = wards_altered.merge(census, on="ward")

    # Print the shape of wards_altered_census
    print('wards_altered_census table shape:', wards_altered_census.shape)

-Merge the wards and census_altered tables on the ward column, and notice the difference in returned rows.

    # Print the first few rows of the census_altered table to view the change 
    print(census_altered[['ward']].head())

    # Merge the wards and census_altered tables on the ward column
    wards_census_altered = wards.merge(census_altered, on="ward")

    # Print the shape of wards_census_altered
    print('wards_census_altered table shape:', wards_census_altered.shape)

# One-to-many relationships

**Personal notes:**

In a one-to-one relationship, each row in the left table is related to one and only one row in the right table. In a one-to-many relationship, each row in the left table is related to one or more rows in the right table.

When merging DataFrames in a one-to-many relationship, the result is a DataFrame with more rows and columns than the left table before the merge.

**Exercises:**

**One-to-many merge**

A business may have one or multiple owners. In this exercise, you will continue to gain experience with one-to-many merges by merging a table of business owners, called biz_owners, to the licenses table. Recall from the video lesson, with a one-to-many relationship, a row in the left table may be repeated if it is related to multiple rows in the right table. In this lesson, you will explore this further by finding out what is the most common business owner title. (i.e., secretary, CEO, or vice president)

The licenses and biz_owners DataFrames are loaded for you.

Instructions:

-Starting with the licenses table on the left, merge it to the biz_owners table on the column account, and save the results to a variable named licenses_owners.

-Group licenses_owners by title and count the number of accounts for each title. Save the result as counted_df

-Sort counted_df by the number of accounts in descending order, and save this as a variable named sorted_df.

-Use the .head() method to print the first few rows of the sorted_df

    # Merge the licenses and biz_owners table on account
    licenses_owners = licenses.merge(biz_owners, on="account")

    # Group the results by title then count the number of accounts
    counted_df = licenses_owners.groupby("title").agg({'account':'count'})

    # Sort the counted_df in desending order
    sorted_df = counted_df.sort_values(by="account", ascending=False)

    # Use .head() method to print the first few rows of sorted_df
    print(sorted_df.head())

# Merging multiple DataFrames

**Personal notes:**

Merging multiple named DataFrames like licenses, ward, and grants:

```python
grants.merge(licenses, on=["address", "zip"]).merge(wards, on="ward", suffixes=("_bus", "_ward"))
```


The backslash (`\`) is used to break a long line of code into multiple lines for better readability, but Python will treat it as a single line of code when executed.

**Exercises:**

**Total riders in a month**

Your goal is to find the total number of rides provided to passengers passing through the Wilson station (station_name == 'Wilson') when riding Chicago's public transportation system on weekdays (day_type == 'Weekday') in July (month == 7). Luckily, Chicago provides this detailed data, but it is in three different tables. You will work on merging these tables together to answer the question. This data is different from the business related data you have seen so far, but all the information you need to answer the question is provided.

The cal, ridership, and stations DataFrames have been loaded for you. The relationship between the tables can be seen in the diagram below.

![Image31](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/ba116891-be05-40a1-a851-742cfb363f8b)

Instructions:

-Merge the ridership and cal tables together, starting with the ridership table on the left and save the result to the variable ridership_cal. If you code takes too long to run, your merge conditions might be incorrect.

    # Merge the ridership and cal tables
    ridership_cal = ridership.merge(cal, on=["year", "month", "day"])

-Extend the previous merge to three tables by also merging the stations table.

-Create a variable called filter_criteria to select the appropriate rows from the merged table so that you can sum the rides column.

    # Merge the ridership, cal, and stations tables
    ridership_cal_stations = ridership.merge(cal, on=['year','month','day']) \
							    .merge(stations, on='station_id')

    # Create a filter to filter ridership_cal_stations
    filter_criteria = ((ridership_cal_stations['month'] == 7) 
                    & (ridership_cal_stations['day_type'] == "Weekday") 
                    & (ridership_cal_stations['station_name'] == "Wilson"))

    # Use .loc and the filter to select for rides
    print(ridership_cal_stations.loc[filter_criteria, 'rides'].sum())

**Three table merge**

To solidify the concept of a three DataFrame merge, practice another exercise. A reasonable extension of our review of Chicago business data would include looking at demographics information about the neighborhoods where the businesses are. A table with the median income by zip code has been provided to you. You will merge the licenses and wards tables with this new income-by-zip-code table called zip_demo.

The licenses, wards, and zip_demo DataFrames have been loaded for you.

Instructions:

-Starting with the licenses table, merge to it the zip_demo table on the zip column. Then merge the resulting table to the wards table on the ward column. Save result of the three merged tables to a variable named licenses_zip_ward.

-Group the results of the three merged tables by the column alderman and find the median income.

    # Merge licenses and zip_demo, on zip; and merge the wards on ward
    licenses_zip_ward = licenses.merge(zip_demo, on="zip") \
            			    .merge(wards, on="ward")

    # Print the results by alderman and show median income
    print(licenses_zip_ward.groupby(by="alderman").agg({'income':'median'}))

**One-to-many merge with multiple tables**

In this exercise, assume that you are looking to start a business in the city of Chicago. Your perfect idea is to start a company that uses goats to mow the lawn for other businesses. However, you have to choose a location in the city to put your goat farm. You need a location with a great deal of space and relatively few businesses and people around to avoid complaints about the smell. You will need to merge three tables to help you choose your location. The land_use table has info on the percentage of vacant land by city ward. The census table has population by ward, and the licenses table lists businesses by ward.

The land_use, census, and licenses tables have been loaded for you.

Instructions:

-Merge land_use and census on the ward column. Merge the result of this with licenses on the ward column, using the suffix _cen for the left table and _lic for the right table. Save this to the variable land_cen_lic.

-Group land_cen_lic by ward, pop_2010 (the population in 2010), and vacant, then count the number of accounts. Save the results to pop_vac_lic.

-Sort pop_vac_lic by vacant, account, andpop_2010 in descending, ascending, and ascending order respectively. Save it as sorted_pop_vac_lic.

    # Merge land_use and census and merge result with licenses including suffixes
    land_cen_lic = land_use.merge(census, on='ward') \
                        .merge(licenses, on='ward', suffixes=('_cen','_lic'))

    # Group by ward, pop_2010, and vacant, then count the # of accounts
    pop_vac_lic = land_cen_lic.groupby(['ward','pop_2010','vacant'], 
                                    as_index=False).agg({'account':'count'})

    # Sort pop_vac_lic and print the results
    sorted_pop_vac_lic = pop_vac_lic.sort_values(["vacant", "account", "pop_2010"], 
                                                ascending=[False, True, True])

    # Print the top few rows of sorted_pop_vac_lic
    print(sorted_pop_vac_lic.head())

