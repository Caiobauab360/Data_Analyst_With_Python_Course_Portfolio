# Sampling Distributions

**Description:**

Let’s test your sampling. In this chapter, you’ll discover how to quantify the accuracy of sample statistics using relative errors, and measure variation in your estimates by generating sampling distributions.

# Relative error of point estimate

**Personal notes:**

The relative error of a point estimate is a critical concept when evaluating the precision and accuracy of your sample-based estimates compared to population parameters. Here are some key takeaways:

1. *Relative Error Formula:*

   - The relative error (RE) of a point estimate is calculated as follows:

     - `relative_error = 100 * abs(population_mean - sample_mean) / population_mean`

   - This formula measures the percentage difference between the population parameter (in this case, the population mean) and the sample estimate (sample mean).

2. *Interpreting Relative Error:*

   - A low relative error indicates that the sample estimate is very close to the population parameter.

   - A higher relative error means that the sample estimate is less accurate and less representative of the population.

3. *Sample Size and Relative Error:*

   - Increasing the sample size generally results in a reduction in relative error. Larger samples tend to provide more accurate and precise estimates.

   - As you observed in the example, the relative error decreased as the sample size increased. A larger sample size led to a point estimate that was closer to the population mean.

4. *Practical Implications:*

   - When designing surveys or experiments, it's essential to consider the trade-off between precision and cost. Larger sample sizes can yield more accurate estimates but may be more resource-intensive.

5. *Graphical Representation:*

   - Plotting the relative error against the sample size can help visualize how the precision of the estimate improves as the sample size increases.

In practice, researchers often choose a sample size that strikes a balance between achieving a sufficient level of precision while considering resource constraints. The relative error provides a quantifiable measure of how closely the sample estimate aligns with the population parameter, helping researchers make informed decisions about their sampling strategies.

**Exercises:**

**Calculating relative errors**

The size of the sample you take affects how accurately the point estimates reflect the corresponding population parameter. For example, when you calculate a sample mean, you want it to be close to the population mean. However, if your sample is too small, this might not be the case.

The most common metric for assessing accuracy is relative error. This is the absolute difference between the population parameter and the point estimate, all divided by the population parameter. It is sometimes expressed as a percentage.

attrition_pop and mean_attrition_pop (the mean of the Attrition column of attrition_pop) are available; pandas is loaded as pd.

Instructions:

-Generate a simple random sample from attrition_pop of fifty rows, setting the seed to 2022.

-Calculate the mean employee Attrition in the sample.

-Calculate the relative error between mean_attrition_srs50 and mean_attrition_pop as a percentage.

      # Generate a simple random sample of 50 rows, with seed 2022
      attrition_srs50 = attrition_pop.sample(n=50, random_state=2022)

      # Calculate the mean employee attrition in the sample
      mean_attrition_srs50 = attrition_srs50["Attrition"].mean()

      # Calculate the relative error percentage
      rel_error_pct50 = 100*abs(mean_attrition_pop-mean_attrition_srs50) /mean_attrition_pop

      # Print rel_error_pct50
      print(rel_error_pct50)

-Calculate the relative error percentage again. This time, use a simple random sample of one hundred rows of attrition_pop.

      # Generate a simple random sample of 100 rows, with seed 2022
      attrition_srs100 = attrition_pop.sample(n=100, random_state=2022)

      # Calculate the mean employee attrition in the sample
      mean_attrition_srs100 = attrition_srs100["Attrition"].mean()

      # Calculate the relative error percentage
      rel_error_pct100 = 100*abs(mean_attrition_pop-mean_attrition_srs100) /mean_attrition_pop

      # Print rel_error_pct100
      print(rel_error_pct100)

# Creating a sampling distribution

**Personal notes:**

We've observed that the average cup points from a simple random sample with n=30 can vary each time it's tested. Let's try to visualize and quantify this variation.

- `mean_cup_points_1000 = []` - We start by creating a list to store these variations.

Next, we set up a for loop to repeatedly sample 30 coffees from the coffee_ratings a total of 1000 times, calculating the mean cup points each time. After each calculation, we append the result, also known as a replication, to the list we created earlier.

- `for i in range(1000):
    - mean_cup_points_1000.append(
        - coffee_ratings.sample(n=30)["total_cup_points"].mean()
    - )` - This results in a list of one thousand sample means added to the `mean_cup_points_1000` list.

These one thousand sample means constitute a distribution of sample means. To visualize such a distribution, the most common and effective way is to use a histogram:

- `plt.hist(mean_cup_points_1000, bins=30)` - A distribution of replications of sample means, or other point estimates, is known as a sampling distribution.

**Exercises:**

**Replicating samples**

When you calculate a point estimate such as a sample mean, the value you calculate depends on the rows that were included in the sample. That means that there is some randomness in the answer. In order to quantify the variation caused by this randomness, you can create many samples and calculate the sample mean (or another statistic) for each sample.

attrition_pop is available; pandas and matplotlib.pyplot are loaded with their usual aliases.

Instructions:

-Replicate the provided code so that it runs 500 times. Assign the resulting list of sample means to mean_attritions.

-Draw a histogram of the mean_attritions list with 16 bins.

      # Create an empty list
      mean_attritions = []
      # Loop 500 times to create 500 sample means
      for i in range(500):
	      mean_attritions.append(
    	      attrition_pop.sample(n=60)['Attrition'].mean()
	)

      # Create a histogram of the 500 sample means
      plt.hist(mean_attritions, bins=16)
      plt.show()

![Image126](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/1daf0240-6214-4a82-985d-ffaa4e329796)

# Approximate sampling distributions

**Personal notes:**

Let's consider the case of four rolls of a six-sided die. We can generate all possible combinations using the `expand_grid` function, defined within pandas, which leverages the itertools package.

- `dice = expand_grid(
    - {"die1": [1,2,3,4,5,6],
    - "die2": [1,2,3,4,5,6],
    - "die3": [1,2,3,4,5,6],
    - "die4": [1,2,3,4,5,6]
    - })` - There are 1296 possible combinations of dice rolls.

Let's consider the mean of the four rolls by adding a column to the DataFrame named `mean_roll`:

- `dice["mean_roll"] = (dice["die1"] +
                    - dice["die2"] +
                    - dice["die3"] +
                    - dice["die4"]) / 4`

As `mean_roll` takes discrete values rather than continuous ones, the best way to view its distribution is by drawing a bar plot:

- `dice["mean_roll"] = dice["mean_roll"].astype("category")` - First, we convert `mean_roll` into a categorical variable by setting its data type as "category."

- `dice["mean_roll"].value_counts(sort=False).plot(kind="bar")` - We are interested in the counts of each value, so we use `value_counts`, passing the argument `sort=False` to ensure that the x-axis ranges from one to six rather than sorting the bars by frequency. The result will be a bar plot representing the distribution of `mean_roll`.

This way, we obtain the exact sampling distribution of the mean roll (`mean_roll`) because it contains all combinations of dice rolls.

We can generate a sample mean of four dice rolls using the `np.random.choice` method by specifying a size of four:

- `np.random.choice(list(range(1, 7)), size=4, replace=True).mean()` - It will randomly select values from a specific list, in this case, four values from the numbers one to six, created using a range from one to seven wrapped in a list. `replace=True` because we can roll the same number multiple times.

Next, we use a for loop to generate sample means:

- `sample_means_1000 = []` 
- `for i in range(1000):
    - sample_means_1000.append(
        - np.random.choice(list(range(1, 7)), size=4, replace=True).mean())` - The result contains a sample of many of the same values we saw with the exact sampling distribution. It's called an approximate sampling distribution, and it closely resembles the exact sampling distribution.
    
**Exercises:**

**Exact sampling distribution**

To quantify how the point estimate (sample statistic) you are interested in varies, you need to know all the possible values it can take and how often. That is, you need to know its distribution.

The distribution of a sample statistic is called the sampling distribution. When we can calculate this exactly, rather than using an approximation, it is known as the exact sampling distribution.

Let's take another look at the sampling distribution of dice rolls. This time, we'll look at five eight-sided dice. (These have the numbers one to eight.

pandas, numpy, and matplotlib.pyplot are loaded with their usual aliases. The expand_grid() function is also available, which expects a dictionary of key-value pairs as its argument. The definition of the expand_grid() function is provided in the pandas documentation.

Instructions:

-Expand a grid representing 5 8-sided dice. That is, create a DataFrame with five columns from a dictionary, named die1 to die5. The rows should contain all possibilities for throwing five dice, each numbered 1 to 8.

-Add a column, mean_roll, to dice, that contains the mean of the five rolls as a categorical.

-Create a bar plot of the mean_roll categorical column, so it displays the count of each mean_roll in increasing order from 1.0 to 8.0.

      # Expand a grid representing 5 8-sided dice
      dice = expand_grid(
      {'die1': [1, 2, 3, 4, 5, 6, 7, 8],
         'die2': [1, 2, 3, 4, 5, 6, 7, 8],
         'die3': [1, 2, 3, 4, 5, 6, 7, 8],
         'die4': [1, 2, 3, 4, 5, 6, 7, 8],
         'die5': [1, 2, 3, 4, 5, 6, 7, 8]
      })

      # Add a column of mean rolls and convert to a categorical
      dice['mean_roll'] = (dice['die1'] + dice['die2'] + 
                           dice['die3'] + dice['die4'] + 
                           dice['die5']) / 5
      dice['mean_roll'] = dice['mean_roll'].astype('category')

      # Draw a bar plot of mean_roll
      dice["mean_roll"].value_counts(sort=False).plot(kind="bar")
      plt.show()

![Image127](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d3dd8104-81b2-40f6-9908-af36003cbf95)

**Generating an approximate sampling distribution**

Calculating the exact sampling distribution is only possible in very simple situations. With just five eight-sided dice, the number of possible rolls is 8**5, which is over thirty thousand. When the dataset is more complicated, for example, where a variable has hundreds or thousands of categories, the number of possible outcomes becomes too difficult to compute exactly.

In this situation, you can calculate an approximate sampling distribution by simulating the exact sampling distribution. That is, you can repeat a procedure over and over again to simulate both the sampling process and the sample statistic calculation process.

pandas, numpy, and matplotlib.pyplot are loaded with their usual aliases.

Instructions:

-Sample one to eight, five times, with replacement. Assign to five_rolls.

-Calculate the mean of five_rolls.

-Replicate the sampling code 1000 times, assigning each result to the list sample_means_1000.

-Plot sample_means_1000 as a histogram with 20 bins.

      # Replicate the sampling code 1000 times
      sample_means_1000 = []
      for i in range(1000):
         sample_means_1000.append(
  		      np.random.choice(list(range(1, 9)), size=5, replace=True).mean()
         )

      # Draw a histogram of sample_means_1000 with 20 bins
      plt.hist(sample_means_1000, bins=20)
      plt.show()

![Image128](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/5729f121-e3ac-4aa3-8af3-971b60160096)

# Standard errors and the Central Limit Theorem

**Personal notes:**

Standard Errors and the Central Limit Theorem

The Gaussian distribution (normal distribution) plays a crucial role in statistics. The central limit theorem states that the means of independent samples have normal distributions. So, as the sample size increases, we observe two things: the distribution of these means approaches normality, and the width of this sampling distribution becomes narrower.

- `np.std(ddof=0)` - Remember to specify `ddof=0` when calculating the population standard deviation and `ddof=1` when calculating sample and sampling distributions.

Another consequence of the central limit theorem is that if we divide the population standard deviation by the square root of the sample size, we obtain an estimate of the standard deviation of the sampling distribution for that sample size. It is not exact due to the randomness involved in the sampling process, but it is very close.

We've just seen the impact of sample size on the standard deviation of the sampling distribution. This standard deviation of the sampling distribution is called the standard error. It is useful in various contexts, from estimating the population standard deviation to setting expectations about the level of variability we would expect from the sampling process.

**Exercises:**

**Population & sampling distribution means**

One of the useful features of sampling distributions is that you can quantify them. Specifically, you can calculate summary statistics on them. Here, you'll look at the relationship between the mean of the sampling distribution and the population parameter's mean.

Three sampling distributions are provided. For each, the employee attrition dataset was sampled using simple random sampling, then the mean attrition was calculated. This was done 1000 times to get a sampling distribution of mean attritions. One sampling distribution used a sample size of 5 for each replicate, one used 50, and one used 500.

attrition_pop, sampling_distribution_5, sampling_distribution_50, and sampling_distribution_500 are available; numpy as np is loaded.

Instructions:

-Calculate the mean of sampling_distribution_5, sampling_distribution_50, and sampling_distribution_500 (a mean of sample means).

      # Calculate the mean of the mean attritions for each sampling distribution
      mean_of_means_5 = np.mean(sampling_distribution_5)
      mean_of_means_50 = np.mean(sampling_distribution_50)
      mean_of_means_500 = np.mean(sampling_distribution_500)
      # Print the results
      print(mean_of_means_5)
      print(mean_of_means_50)
      print(mean_of_means_500)

**Population & sampling distribution variation**

You just calculated the mean of the sampling distribution and saw how it is an estimate of the corresponding population parameter. Similarly, as a result of the central limit theorem, the standard deviation of the sampling distribution has an interesting relationship with the population parameter's standard deviation and the sample size.

attrition_pop, sampling_distribution_5, sampling_distribution_50, and sampling_distribution_500 are available; numpy is loaded with its usual alias.

Instructions:

-Calculate the standard deviation of sampling_distribution_5, sampling_distribution_50, and sampling_distribution_500 (a standard deviation of sample means).

      # Calculate the std. dev. of the mean attritions for each sampling distribution
      sd_of_means_5 = np.std(sampling_distribution_5, ddof=1)
      sd_of_means_50 = np.std(sampling_distribution_50, ddof=1)
      sd_of_means_500 = np.std(sampling_distribution_500, ddof=1)

      #  Print the results
      print(sd_of_means_5)
      print(sd_of_means_50)
      print(sd_of_means_500)

