# Advanced Merging and Concatenating

**Description:**

In this chapter, you’ll leverage powerful filtering techniques, including semi-joins and anti-joins. You’ll also learn how to glue DataFrames by vertically combining and using the pandas.concat function to create new datasets. Finally, because data is rarely clean, you’ll also learn how to validate your newly combined data structures.

# Filtering joins

**Personal notes:**

Filtering joins allow you to filter observations from one table based on whether they match or do not match observations in another table.

**Semi Join:*

1. Start by performing an inner join between the two tables using `merge()`.

   ```python
   merged_df = DataFrame1.merge(DataFrame2, on="common_column")
   ```

2. Use the `isin()` method to compare each element in a column to the elements in another column.

   ```python
   filter_condition = DataFrame1["column_to_filter"].isin(DataFrame2["matching_column"])
   ```

3. Finally, use the filtered condition to create a subset of the table.

   ```python
   filtered_subset = merged_df[filter_condition]
   ```

**Anti Join:*

1. Begin with a left join, returning all rows from the left table, and add an indicator column using `indicator=True`.

   ```python
   merged_df = DataFrame1.merge(DataFrame2, on="common_column", how="left", indicator=True)
   ```

2. Use `.loc` and the indicator column to select rows that only appear in the left table.

   ```python
   anti_join_condition = merged_df["_merge"] == "left_only"
   anti_join_result = merged_df.loc[anti_join_condition, ["left_table_column"]]
   ```

3. You can use the `isin()` method to filter rows with values matching a specific column.

   ```python
   anti_join_result = anti_join_result[anti_join_result["left_table_column"].isin(DataFrame2["matching_column"])]
   ```

This process will give you a DataFrame containing rows from the left table that do not have corresponding matches in the right table.

**Exercises:**

**Performing an anti join**

In our music streaming company dataset, each customer is assigned an employee representative to assist them. In this exercise, filter the employee table by a table of top customers, returning only those employees who are not assigned to a customer. The results should resemble the results of an anti join. The company's leadership will assign these employees additional training so that they can work with high valued customers.

The top_cust and employees tables have been provided for you.

Instructions:

-Merge employees and top_cust with a left join, setting indicator argument to True. Save the result to empl_cust.

-Select the srid column of empl_cust and the rows where _merge is 'left_only'. Save the result to srid_list.

-Subset the employees table and select those rows where the srid is in the variable srid_list and print the results.

      # Merge employees and top_cust
      empl_cust = employees.merge(top_cust, on='srid', 
                                    how='left', indicator=True)

      # Select the srid column where _merge is left_only
      srid_list = empl_cust.loc[empl_cust['_merge'] == 'left_only', 'srid']

      # Get employees not working with top customers
      print(employees[employees["srid"].isin(srid_list)])

**Performing a semi join**

Some of the tracks that have generated the most significant amount of revenue are from TV-shows or are other non-musical audio. You have been given a table of invoices that include top revenue-generating items. Additionally, you have a table of non-musical tracks from the streaming service. In this exercise, you'll use a semi join to find the top revenue-generating non-musical tracks..

The tables non_mus_tcks, top_invoices, and genres have been loaded for you.

Instructions:

-Merge non_mus_tcks and top_invoices on tid using an inner join. Save the result as tracks_invoices.

-Use .isin() to subset the rows of non_mus_tck where tid is in the tid column of tracks_invoices. Save the result as top_tracks.

-Group top_tracks by gid and count the tid rows. Save the result to cnt_by_gid.

-Merge cnt_by_gid with the genres table on gid and print the result.

      # Merge the non_mus_tck and top_invoices tables on tid
      tracks_invoices = non_mus_tcks.merge(top_invoices, on="tid")

      # Use .isin() to subset non_mus_tcks to rows with tid in tracks_invoices
      top_tracks = non_mus_tcks[non_mus_tcks['tid'].isin(tracks_invoices["tid"])]

      # Group the top_tracks by gid and count the tid rows
      cnt_by_gid = top_tracks.groupby(['gid'], as_index=False).agg({'tid':"count"})

      # Merge the genres table to cnt_by_gid on gid and print
      print(cnt_by_gid.merge(genres, on='gid'))

# Concatenate DataFrames together vertically

**Personal notes:**

You can concatenate DataFrames vertically using the `pd.concat()` function. Here are some common scenarios:

**Basic Concatenation:*

```python
result = pd.concat([table_1, table_2, table_3])
```

In this basic concatenation, the resulting DataFrame will retain the original indices.

**Concatenation with Ignored Indices:*

```python
result = pd.concat([table_1, table_2, table_3], ignore_index=True)
```

Using `ignore_index=True`, you can concatenate the tables while ignoring the original indices and creating new indices from 0 to n-1.

**Concatenation with Multi-Level Indices:*

```python
result = pd.concat([table_1, table_2, table_3], keys=["jan", "feb", "mar"])
```

If you want to add a label to the original tables, you can use the `keys` parameter. This will result in a new DataFrame with multi-level indices, where the labels "jan," "feb," and "mar" represent the first level of the index.

**Concatenation with Different Column Names:*

By default, `pd.concat()` includes all columns from the different tables. You can use the `sort=True` argument to alphabetically sort the column names in the result.

```python
result = pd.concat([table_1, table_2, table_3], sort=True)
```

If you want to include only columns that are common to all tables, you can specify the `join` parameter as "inner." This will include only the intersecting columns from the original tables, and the `sort` argument will have no effect.

```python
result = pd.concat([table_1, table_2, table_3], join="inner")
```

These are different ways to concatenate DataFrames vertically while considering indices, labels, and column names as needed.

**Exercises:**

**Concatenation basics**

You have been given a few tables of data with musical track info for different albums from the metal band, Metallica. The track info comes from their Ride The Lightning, Master Of Puppets, and St. Anger albums. Try various features of the .concat() method by concatenating the tables vertically together in different ways.

The tables tracks_master, tracks_ride, and tracks_st have loaded for you.

Instructions:

-Concatenate tracks_master, tracks_ride, and tracks_st, in that order, setting sort to True.

      # Concatenate the tracks
      tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                                    sort=True)
      print(tracks_from_albums)
   
-Concatenate tracks_master, tracks_ride, and tracks_st, where the index goes from 0 to n-1.

      # Concatenate the tracks so the index goes from 0 to n-1
      tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                                    ignore_index=True,
                                    sort=True)
      print(tracks_from_albums)

-Concatenate tracks_master, tracks_ride, and tracks_st, showing only columns that are in all tables.

      # Concatenate the tracks, show only columns names that are in all tables
      tracks_from_albums = pd.concat([tracks_master, tracks_ride, tracks_st],
                                    join="inner",
                                    sort=True)
      print(tracks_from_albums)

**Concatenating with keys**

The leadership of the music streaming company has come to you and asked you for assistance in analyzing sales for a recent business quarter. They would like to know which month in the quarter saw the highest average invoice total. You have been given three tables with invoice data named inv_jul, inv_aug, and inv_sep. Concatenate these tables into one to create a graph of the average monthly invoice total.

Instructions:

-Concatenate the three tables together vertically in order with the oldest month first, adding '7Jul', '8Aug', and '9Sep' as keys for their respective months, and save to variable avg_inv_by_month.

-Use the .agg() method to find the average of the total column from the grouped invoices.

-Create a bar chart of avg_inv_by_month.

      # Concatenate the tables and add keys
      inv_jul_thr_sep = pd.concat([inv_jul, inv_aug, inv_sep], 
                                 keys=["7Jul", "8Aug", "9Sep"])

      # Group the invoices by the index keys and find avg of the total column
      avg_inv_by_month = inv_jul_thr_sep.groupby(level=0).agg({"total":"mean"})

      # Bar plot of avg_inv_by_month
      avg_inv_by_month.plot(kind="bar")
      plt.show()

![Image33](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/a1799855-8cad-4516-a0e2-472861a90f61)

# Verifying integrity

**Personal notes:**

Data integrity is crucial when working with DataFrames, and it ensures that your data is structured correctly. Here are ways to verify data integrity in pandas:

**Verifying Integrity with `merge`*:

When using the `merge` method to combine DataFrames, you can specify the type of relationship expected between the tables using the `validate` parameter. This helps to ensure that the relationship matches the tables involved.

```python
result = DataFrame1.merge(DataFrame2, on="key_column", validate="one_to_one")
```

The `validate` parameter can take various values like "one_to_one," "one_to_many," or "many_to_many." If the relationship doesn't match what you specify, a MergeError will be raised.

**Verifying Integrity with `concat`*:

The `concat` function has a `verify_integrity` parameter. When set to `True`, it checks for duplicate indices during concatenation and raises a ValueError if duplicates are found. This is useful for ensuring that you don't accidentally introduce duplicates in your DataFrame indices.

```python
result = pd.concat([table_1, table_2, table_3], verify_integrity=True)
```

If you set `verify_integrity` to `False`, it won't check for duplicate indices and will concatenate the tables even if there are duplicates.

```python
result = pd.concat([table_1, table_2, table_3], verify_integrity=False)
```

Checking data integrity is important for data analysis to avoid inaccurate results and ensure that your data is clean and structured correctly. If you encounter MergeError or ValueError, it's an indication that you need to review and clean your data to maintain its integrity.

**Exercises:**

**Validating a merge**

You have been given 2 tables, artists, and albums. Use the IPython shell to merge them using artists.merge(albums, on='artid').head(). Adjust the validate argument to answer which statement is False.

   You can use many-to-one without an error, since there is a duplicate key in the left table.

**Concatenate and merge to find common songs**

The senior leadership of the streaming service is requesting your help again. You are given the historical files for a popular playlist in the classical music genre in 2018 and 2019. Additionally, you are given a similar set of files for the most popular pop music genre playlist on the streaming service in 2018 and 2019. Your goal is to concatenate the respective files to make a large classical playlist table and overall popular music table. Then filter the classical music table using a semi join to return only the most popular classical music tracks.

The tables classic_18, classic_19, and pop_18, pop_19 have been loaded for you. Additionally, pandas has been loaded as pd.

Instructions:

-Concatenate the classic_18 and classic_19 tables vertically where the index goes from 0 to n-1, and save to classic_18_19.

-Concatenate the pop_18 and pop_19 tables vertically where the index goes from 0 to n-1, and save to pop_18_19

-With classic_18_19 on the left, merge it with pop_18_19 on tid using an inner join.

-Use .isin() to filter classic_18_19 where tid is in classic_pop

      # Concatenate the classic tables vertically
      classic_18_19 = pd.concat([classic_18, classic_19], ignore_index=True)

      # Concatenate the pop tables vertically
      pop_18_19 = pd.concat([pop_18, pop_19], ignore_index=True)

      # Merge classic_18_19 with pop_18_19
      classic_pop = classic_18_19.merge(pop_18_19, on="tid")

      # Using .isin(), filter classic_18_19 rows where tid is in classic_pop
      popular_classic = classic_18_19[classic_18_19["tid"].isin(classic_pop["tid"])]

      # Print popular chart
      print(popular_classic)

