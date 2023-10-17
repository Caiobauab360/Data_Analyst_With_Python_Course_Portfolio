# Sampling Methods

**Description:**

It’s time to get hands-on and perform the four random sampling methods in Python: simple, systematic, stratified, and cluster.

# Simple random and systematic sampling

**Personal notes:**

*Simple random sampling* works like a raffle or a lottery. You start with your population of raffle tickets or lottery balls and select them randomly, one at a time.

- *.sample(n=, random_state=)* - You set n as the sample size. You can set the seed using the random_state argument to produce reproducible results.

*Systematic sampling* performs the sampling with the population at regular intervals. To perform systematic sampling, you need to start by determining the interval size between each row for a given sample size:

-*sample_size = 5* - The desired sample size.

-*pop_size = len(coffee_ratings)* - The population size is the number of rows in the entire dataset.

-*interval = pop_size // sample_size* - The interval is the population size divided by the sample size. However, as an integer is expected as a result, you need to perform the division using double 
slashes, which acts as the standard division but discards any fractional part of the result.

The result of the division is the interval size that needs to be selected to collect the sample from the dataset. To select every x rows, you use *.iloc[]*:

-*coffee_ratings.iloc[::interval]* - By passing double colons to iloc and the previously calculated interval, this instructs pandas to select every 267th row from zero to the end of the dataframe.

In general, systematic sampling should only be used if the plot studied doesn't have a pattern. To ensure that systematic sampling is safe, you can randomize the order of the rows before sampling.

-*shuffled = coffee_ratings.sample(frac=1)* - The frac argument allows you to specify the proportion of the dataset to be returned in the sample, rather than the absolute number of rows n specifies. Setting it to 1 results in randomly sampling the entire dataset, shuffling the rows randomly.

-*shuffled = shuffled.reset_index(drop=True).reset_index()* - Then, you need to reset the row indices to start from zero again. Specifying drop as True clears the previous row index, and chaining it to another reset_index call creates a column containing these new indices.

After shuffling the rows, systematic sampling is essentially the same as simple random sampling.

**Exercises:**

**Simple random sampling**

The simplest method of sampling a population is the one you've seen already. It is known as simple random sampling (sometimes abbreviated to "SRS"), and involves picking rows at random, one at a time, where each row has the same chance of being picked as any other.

In this chapter, you'll apply sampling methods to a synthetic (fictional) employee attrition dataset from IBM, where "attrition" in this context means leaving the company.

attrition_pop is available; pandas as pd is loaded.

Instructions:

-Sample 70 rows from attrition_pop using simple random sampling, setting the random seed to 18900217.

-Print the sample dataset, attrition_samp. What do you notice about the indices?

      # Sample 70 rows using simple random sampling and set the seed
      attrition_samp = attrition_pop.sample(n=70, random_state=18900217)

      # Print the sample
      print(attrition_samp)

**Systematic sampling**

One sampling method that avoids randomness is called systematic sampling. Here, you pick rows from the population at regular intervals.

For example, if the population dataset had one thousand rows, and you wanted a sample size of five, you could pick rows 0, 200, 400, 600, and 800.

attrition_pop is available; pandas has been pre-loaded as pd

Instructions:

-Set the sample size to 70.

-Calculate the population size from attrition_pop.

-Calculate the interval between the rows to be sampled.

-Systematically sample attrition_pop to get the rows of the population at each interval, starting at 0; assign the rows to attrition_sys_samp.

      # Set the sample size to 70
      sample_size = 70

      # Calculate the population size from attrition_pop
      pop_size = len(attrition_pop)

      # Calculate the interval
      interval = pop_size // sample_size

      # Systematically sample 70 rows
      attrition_sys_samp = attrition_pop.iloc[::interval]

      # Print the sample
      print(attrition_sys_samp)

**Is systematic sampling OK?**

Systematic sampling has a problem: if the data has been sorted, or there is some sort of pattern or meaning behind the row order, then the resulting sample may not be representative of the whole population. The problem can be solved by shuffling the rows, but then systematic sampling is equivalent to simple random sampling.

Here you'll look at how to determine whether or not there is a problem.

attrition_pop is available; pandas is loaded as pd, and matplotlib.pyplot as plt.

Instructions:

-Add an index column to attrition_pop, assigning the result to attrition_pop_id.

-Create a scatter plot of YearsAtCompany versus index for attrition_pop_id using pandas .plot().

      # Add an index column to attrition_pop
      attrition_pop_id = attrition_pop.reset_index()

      # Plot YearsAtCompany vs. index for attrition_pop_id
      attrition_pop_id.plot(x="index", y="YearsAtCompany", kind="scatter")
      plt.show()

![Image122](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/6a5b2984-4af3-4b08-b5bb-bb4ec8d7de75)

-Randomly shuffle the rows of attrition_pop.

-Reset the row indexes, and add an index column to attrition_pop.

-Repeat the scatter plot of YearsAtCompany versus index, this time using attrition_shuffled.

      # Shuffle the rows of attrition_pop
      attrition_shuffled = attrition_pop.sample(frac=1)

      # Reset the row indexes and create an index column
      attrition_shuffled = attrition_shuffled.reset_index(drop=True).reset_index()

      # Plot YearsAtCompany vs. index for attrition_shuffled
      attrition_shuffled.plot(x="index", y="YearsAtCompany", kind="scatter")
      plt.show()

![Image123](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/df95c301-9c3f-4877-ae2f-9e175b5b6283)

# Stratified and weighted random sampling

**Personal notes:**

*Stratified sampling* is a technique that allows us to sample a population containing subgroups. One way to perform sampling on a population with subgroups is to narrow down the analysis by creating a list of variables of interest.

-*.isin()* - You can use the isin method to filter the population. Store the filtered data in a new variable.

*Stratified random sampling* can be achieved by using the *groupby()* and *sample()* methods together. Calling sample after grouping takes a simple random sample within each group.

In *weighted random sampling*, you create a weight column that adjusts the relative sampling probability of each row.

-*condition = coffee_ratings_weight["country_of_origin"] == "Taiwan"* - You create a condition, where, in the example, it's rows where the country of origin is Taiwan.

-*coffee_ratings_weight["weight"] = np.where(condition, 1, 2)* - Using the np.where function from NumPy, you can set a weight of two for the rows that match the condition and a weight of one for rows that don't match the condition.

-*coffee_ratings_weight = coffee_ratings_weight.sample(frac=0.1, weights="weight")* - When you call .sample, you pass the weight column to the weights argument.

This type of weighted sampling is common in political surveys, where you need to correct insufficient or excessive representation of demographic groups.

**Exercises:**

**Proportional stratified sampling**

If you are interested in subgroups within the population, then you may need to carefully control the counts of each subgroup within the population. Proportional stratified sampling results in subgroup sizes within the sample that are representative of the subgroup sizes within the population. It is equivalent to performing a simple random sample on each subgroup.

attrition_pop is available; pandas is loaded with its usual alias.

Instructions:

-Get the proportion of employees by Education level from attrition_pop.

-Use proportional stratified sampling on attrition_pop to sample 40% of each Education group, setting the seed to 2022.

-Get the proportion of employees by Education level from attrition_strat.

      # Proportion of employees by Education level
      education_counts_pop = attrition_pop['Education'].value_counts(normalize=True)

      # Print education_counts_pop
      print(education_counts_pop)

      # Proportional stratified sampling for 40% of each Education group
      attrition_strat = attrition_pop.groupby('Education')\
	      .sample(frac=0.4, random_state=2022)

      # Calculate the Education level proportions from attrition_strat
      education_counts_strat = attrition_strat['Education'].value_counts(normalize=True)

      # Print education_counts_strat
      print(education_counts_strat)

**Equal counts stratified sampling**

If one subgroup is larger than another subgroup in the population, but you don't want to reflect that difference in your analysis, then you can use equal counts stratified sampling to generate samples where each subgroup has the same amount of data. For example, if you are analyzing blood types, O is the most common blood type worldwide, but you may wish to have equal amounts of O, A, B, and AB in your sample.

attrition_pop is available; pandas is loaded with its usual alias.

Instructions:

-Use equal counts stratified sampling on attrition_pop to get 30 employees from each Education group, setting the seed to 2022.

-Get the proportion of employees by Education level from attrition_eq.

      # Get 30 employees from each Education group
      attrition_eq = attrition_pop.groupby('Education')\
	      .sample(n=30, random_state=2022)      

      # Get the proportions from attrition_eq
      education_counts_eq = attrition_eq["Education"].value_counts(normalize=True)

      # Print the results
      print(education_counts_eq)

**Weighted sampling**

Stratified sampling provides rules about the probability of picking rows from your dataset at the subgroup level. A generalization of this is weighted sampling, which lets you specify rules about the probability of picking rows at the row level. The probability of picking any given row is proportional to the weight value for that row.

attrition_pop is available; pandas, matplotlib.pyplot, and numpy are loaded with their usual aliases.

Instructions:

-Plot YearsAtCompany from attrition_pop as a histogram with bins of width 1 from 0 to 40.

      # Plot YearsAtCompany from attrition_pop as a histogram
      attrition_pop['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))
      plt.show()

![Image124](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/c150aa62-0ce6-401b-8ab4-d0f30dc6d79d)

-Sample 400 employees from attrition_pop weighted by YearsAtCompany.

      # Plot YearsAtCompany from attrition_pop as a histogram
      attrition_pop['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))
      plt.show()

      # Sample 400 employees weighted by YearsAtCompany
      attrition_weight = attrition_pop.sample(n=400, replace=False, weights = attrition_pop['YearsAtCompany'])

      # Print the sample
      print(attrition_weight)

-Plot YearsAtCompany from attrition_weight as a histogram with bins of width 1 from 0 to 40

      # Plot YearsAtCompany from attrition_pop as a histogram
      attrition_pop['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))
      plt.show()

      # Sample 400 employees weighted by YearsAtCompany
      attrition_weight = attrition_pop.sample(n=400, weights="YearsAtCompany")

      # Plot YearsAtCompany from attrition_weight as a histogram
      attrition_weight['YearsAtCompany'].hist(bins=np.arange(0, 41, 1))

      plt.show()

![Image125](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b8a53756-ea46-4a30-8863-1a0d5643de4e)

# Cluster sampling

**Personal notes:**

In stratified sampling, you need to collect data from each subgroup, dividing the population into subgroups and then using simple random sampling in each of them. In cluster sampling, you limit the number of subgroups in the analysis by selecting some of them with simple random sampling and then perform simple random sampling within each subgroup as before.

To extract unique varieties using *.unique()*:

-*varieties_pop = list(coffee_ratings["variety"].unique())* - This returns an array, so wrapping it in the list function creates a list of unique varieties.

First stage of cluster sampling:

-*import random

  -*varieties_samp = random.sample(varieties_pop, k=3)* - The first stage of cluster sampling is to randomly cut down the number of varieties, and you do that by randomly selecting them. Use the random.sample() function from the random package to get three varieties, specifying the argument k=3.

Second stage:

-*variety_condition = coffee_ratings["variety"].isin(varieties_samp)*
  -*coffee_ratings_cluster = coffee_ratings[variety_condition]* - The second stage is to perform simple random sampling within each of the three varieties that you randomly selected. First, filter the dataset for the rows where the variety is one of the three selected using the .isin method.

  -*coffee_ratings_cluster["variety"] = coffee_ratings_cluster['variety'].cat.remove_unused_categories()* - To ensure that the isin filtering removes levels with zero rows, apply cat.remove_unused_categories to the focus series, which is the variety here. If you omit this method, you might get an error when sampling by variety level.

  -*coffee_ratings_cluster.groupby("variety").sample(n=5, random_state=2021)* - Then, use the pandas code like stratified sampling. n=5 results in an equal count sample of five rows from each remaining variety.

These are the two stages of cluster sampling. You randomly sample the subgroups to include, and then randomly sample rows within those subgroups. Cluster sampling is a special case of multistage sampling. You can use more than two stages if needed.

**Exercises:**

**Performing cluster sampling**

Now that you know when to use cluster sampling, it's time to put it into action. In this exercise, you'll explore the JobRole column of the attrition dataset. You can think of each job role as a subgroup of the whole population of employees.

attrition_pop is available; pandas is loaded with its usual alias, and the random package is available. A seed of 19790801 has also been set with random.seed().

Instructions:

-Create a list of unique JobRole values from attrition_pop, and assign to job_roles_pop.

-Randomly sample four JobRole values from job_roles_pop.

-Subset attrition_pop for the sampled job roles by filtering for rows where JobRole is in job_roles_samp.

-Remove any unused categories from JobRole.

-For each job role in the filtered dataset, take a random sample of ten rows, setting the seed to 2022.

      # Create a list of unique JobRole values
      job_roles_pop = list(attrition_pop['JobRole'].unique())

      # Randomly sample four JobRole values
      job_roles_samp = random.sample(job_roles_pop, k=4)

      # Filter for rows where JobRole is in job_roles_samp
      jobrole_condition = attrition_pop['JobRole'].isin(job_roles_samp)
      attrition_filtered = attrition_pop[jobrole_condition]

      # Remove categories with no rows
      attrition_filtered['JobRole'] = attrition_filtered['JobRole'].cat.remove_unused_categories()

      # Randomly sample 10 employees from each sampled job role
      attrition_clust = attrition_filtered.groupby("JobRole").sample(n=10, random_state=2022)


      # Print the sample
      print(attrition_clust)

# Comparing sampling methods

**Personal notes:**

It's important to understand and compare different sampling methods because the method you choose can significantly impact the quality of your analysis and the accuracy of your results. Here's a summary of the methods discussed and their comparisons:

1.*Simple Random Sampling (SRS):*

   - Selects a random subset of the population with equal probability.

   - Generally provides unbiased estimates of population parameters.

   - Can be inefficient if the population is highly stratified or clustered.

2.*Stratified Sampling:*

   - Divides the population into strata or subgroups based on some characteristic (e.g., age, location).

   - Samples randomly within each stratum, ensuring representation of each group.

   - Typically provides more precise estimates than SRS when the population is diverse.

3.*Cluster Sampling:*

   - Divides the population into clusters or groups (e.g., schools, neighborhoods).

   - Randomly selects clusters and samples all units within the selected clusters.

   - Can be more efficient when the clusters themselves are fairly homogeneous but may lead to less accurate estimates if the clusters are diverse.
   
4.*Comparing Estimates:*

   - Population parameters are usually unknown in real-life scenarios, so we use them as benchmarks to measure the performance of our sampling methods.

   - In the examples discussed, both SRS and stratified sampling produced estimates of population means that were very close to the true population mean, which is a favorable outcome.

   - Cluster sampling, while less precise, can still provide acceptable estimates if the inherent clusters within the data are considered in the analysis.

The choice of sampling method should depend on the research question, available resources, and the nature of the data. Researchers must carefully consider which method is most suitable for their specific study to ensure that their estimates are reliable and representative of the population they are studying.

**Exercises:**

**3 kinds of sampling**

You're going to compare the performance of point estimates using simple, stratified, and cluster sampling. Before doing that, you'll have to set up the samples.

You'll use the RelationshipSatisfaction column of the attrition_pop dataset, which categorizes the employee's relationship with the company. It has four levels: Low, Medium, High, and Very_High. pandas has been loaded with its usual alias, and the random package has been loaded.

Instructions:

-Perform simple random sampling on attrition_pop to get one-quarter of the population, setting the seed to 2022.

      # Perform simple random sampling to get 0.25 of the population
      attrition_srs = attrition_pop.sample(frac=0.25, random_state=2022)

-Perform stratified sampling on attrition_pop to sample one-quarter of each RelationshipSatisfaction group, setting the seed to 2022.

      # Perform stratified sampling to get 0.25 of each relationship group
      attrition_strat = attrition_pop.groupby("RelationshipSatisfaction").sample(frac=0.25, random_state=2022)

-Create a list of unique values from attrition_pop's RelationshipSatisfaction column.
Randomly sample satisfaction_unique to get two values.
Subset the population for rows where RelationshipSatisfaction is in satisfaction_samp and clear any unused categories from RelationshipSatisfaction; assign to attrition_clust_prep.
Perform cluster sampling on the selected satisfaction groups, sampling one quarter of the population and setting the seed to 2022.

      # Create a list of unique RelationshipSatisfaction values
      satisfaction_unique = list(attrition_pop['RelationshipSatisfaction'].unique())

      # Randomly sample 2 unique satisfaction values
      satisfaction_samp = random.sample(satisfaction_unique, k=2)

      # Filter for satisfaction_samp and clear unused categories from RelationshipSatisfaction
      satis_condition = attrition_pop['RelationshipSatisfaction'].isin(satisfaction_samp)
      attrition_clust_prep = attrition_pop[satis_condition]
      attrition_clust_prep['RelationshipSatisfaction'] = attrition_clust_prep['RelationshipSatisfaction'].cat.remove_unused_categories()

      # Perform cluster sampling on the selected group, getting 0.25 of attrition_pop
      attrition_clust = attrition_clust_prep.groupby("RelationshipSatisfaction")\
         .sample(n=len(attrition_pop) // 4, random_state=2022)

**Comparing point estimates**

Now that you have three types of sample (simple, stratified, and cluster), you can compare point estimates from each sample to the population parameter. That is, you can calculate the same summary statistic on each sample and see how it compares to the summary statistic for the population.

Here, we'll look at how satisfaction with the company affects whether or not the employee leaves the company. That is, you'll calculate the proportion of employees who left the company (they have an Attrition value of 1) for each value of RelationshipSatisfaction.

attrition_pop, attrition_srs, attrition_strat, and attrition_clust are available; pandas is loaded with its usual alias.

Instructions:

-Group attrition_pop by RelationshipSatisfaction levels and calculate the mean of Attrition for each level.

      # Mean Attrition by RelationshipSatisfaction group
      mean_attrition_pop = attrition_pop.groupby("RelationshipSatisfaction")["Attrition"].mean()

      # Print the result
      print(mean_attrition_pop)

-Calculate the proportion of employee attrition for each relationship satisfaction group, this time on the simple random sample, attrition_srs.

      # Calculate the same thing for the simple random sample 
      mean_attrition_srs = attrition_srs.groupby("RelationshipSatisfaction")["Attrition"].mean()

      # Print the result
      print(mean_attrition_srs)

-Calculate the proportion of employee attrition for each relationship satisfaction group, this time on the stratified sample, attrition_strat.

      # Calculate the same thing for the stratified sample 
      mean_attrition_strat = attrition_strat.groupby("RelationshipSatisfaction")["Attrition"].mean()

      # Print the result
      print(mean_attrition_strat)

-Calculate the proportion of employee attrition for each relationship satisfaction group, this time on the cluster sample, attrition_clust.

      # Calculate the same thing for the cluster sample 
      mean_attrition_clust = attrition_clust.groupby("RelationshipSatisfaction")["Attrition"].mean()

      # Print the result
      print(mean_attrition_clust)

