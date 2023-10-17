# Bootstrap Distributions

**Description:**

You’ll get to grips with resampling to perform bootstrapping and estimate variation in an unknown population. You’ll learn the difference between sampling distributions and bootstrap distributions using resampling.

# Introduction to bootstrapping

**Personal notes:**

Bootstrapping is the opposite of sampling from a population. With sampling, we treat the dataset as the population and move to a smaller sample. With bootstrapping, we treat the dataset as a sample and use it to construct a theoretical population. 

One use case for bootstrapping is to understand the variability due to sampling. This is important in cases where we cannot sample the population multiple times to create a sampling distribution.

The bootstrapping process involves three steps, resulting in a bootstrap distribution:

1. Randomly sample with replacement to obtain a resampling of the same size as the original dataset.
2. Calculate a statistic, such as the mean of one of the columns. The mean does not always have to be the choice in this step; bootstrapping allows complex statistics to be calculated.
3. Repeat steps one and two several times to obtain many of these bootstrap statistics.

- `np.mean(coffee_sample.sample(frac=1, replace=True)["flavor"])` - The resampling step can be done using this code.

To repeat steps one and two multiple times, you can use a for loop:

- `mean_flavors_1000 = []`
- `for i in range(1000):`
   - `mean_flavors_1000.append(np.mean(coffee_sample.sample(frac=1, replace=True)["flavor"]))`

To visualize the bootstrap distribution of the sample mean, you can plot a histogram:

- `plt.hist(mean_flavors_1000)` 

**Exercises:**

**Generating a bootstrap distribution**

The process for generating a bootstrap distribution is similar to the process for generating a sampling distribution; only the first step is different.

To make a sampling distribution, you start with the population and sample without replacement. To make a bootstrap distribution, you start with a sample and sample that with replacement. After that, the steps are the same: calculate the summary statistic that you are interested in on that sample/resample, then replicate the process many times. In each case, you can visualize the distribution with a histogram.

Here, spotify_sample is a subset of the spotify_population dataset. To make it easier to see how resampling works, a row index column called 'index' has been added, and only the artist name, song name, and danceability columns have been included.

spotify_sample is available; pandas, numpy, and matplotlib.pyplot are loaded with their usual aliases.

Instructions:

-Generate a single bootstrap resample from spotify_sample.

-Calculate the mean of the danceability column of spotify_1_resample using numpy.

      # Generate 1 bootstrap resample
      spotify_1_resample = spotify_sample.sample(frac=1, replace=True)

      # Calculate of the danceability column of spotify_1_resample
      mean_danceability_1 = np.mean(spotify_1_resample['danceability'])

      # Print the result
      print(mean_danceability_1)

-Replicate the expression provided 1000 times.

-Create a bootstrap distribution by drawing a histogram of mean_danceability_1000.

      # Replicate this 1000 times
      mean_danceability_1000 = []
      for i in range(1000):
	      mean_danceability_1000.append(
            np.mean(spotify_sample.sample(frac=1, replace=True)['danceability'])
	      )

      # Draw a histogram of the resample means
      plt.hist(mean_danceability_1000)
      plt.show()

![Image129](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/8ff3c688-d443-418f-9de1-841fd592a08e)

# Comparing sampling and bootstrap distributions

**Personal notes:**

The mean of the bootstrap distribution is generally almost identical to the mean of the original sample. However, this is not always a good thing. If the original sample was not representative of the population, then the mean of the bootstrap distribution will not be a good estimate of the population mean. Bootstrapping cannot correct any potential biases due to differences between the sample and the population.

Although we have this limitation in estimating the population mean, one great thing about distributions is that we can also quantify variability. Remember that one of the goals of bootstrapping is to quantify the variability we can expect in our sample statistic as we move from one sample to another. This quantity is called the standard error, measured by the standard deviation of the sampling distribution of that statistic.

The standard deviation of the bootstrap means can be used as a way to estimate this measure of uncertainty. If we multiply this standard error by the square root of the sample size, we get an estimate of the standard deviation in the original population:

- `standard_error * np.sqrt(500)`

So, while bootstrapping is not great for estimating the population mean, it is good for estimating the population standard deviation.

**Exercises:**

**Sampling distribution vs. bootstrap distribution**

The sampling distribution and bootstrap distribution are closely linked. In situations where you can repeatedly sample from a population (these occasions are rare), it's helpful to generate both the sampling distribution and the bootstrap distribution, one after the other, to see how they are related.

Here, the statistic you are interested in is the mean popularity score of the songs.

spotify_population (the whole dataset) and spotify_sample (500 randomly sampled rows from spotify_population) are available; pandas and numpy are loaded with their usual aliases.

Instrutions:

-Generate a sampling distribution of 2000 replicates.
Sample 500 rows of the population without replacement and calculate the mean popularity.

      mean_popularity_2000_samp = []

      # Generate a sampling distribution of 2000 replicates
      for i in range(2000):
         mean_popularity_2000_samp.append(
    	      # Sample 500 rows and calculate the mean popularity 
    	      np.mean(spotify_population.sample(n=500, replace=False)["popularity"])
         )

      # Print the sampling distribution results
      print(mean_popularity_2000_samp)

-Generate a bootstrap distribution of 2000 replicates.
Sample 500 rows of the sample with replacement and calculate the mean popularity.

      mean_popularity_2000_boot = []

      # Generate a bootstrap distribution of 2000 replicates
      for i in range(2000):
         mean_popularity_2000_boot.append(
    	      # Resample 500 rows and calculate the mean popularity     
    	      np.mean(spotify_sample.sample(n=500, replace=True)["popularity"])
         )

      # Print the bootstrap distribution results
      print(mean_popularity_2000_boot)

**Compare sampling and bootstrap means**

To make calculation easier, distributions similar to those calculated from the previous exercise have been included, this time using a sample size of 5000.

spotify_population, spotify_sample, sampling_distribution, and bootstrap_distribution are available; pandas and numpy are loaded with their usual aliases.

Instructions:

Calculate the mean popularity in 4 ways:

-Population: from spotify_population, take the mean of popularity.

-Sample: from spotify_sample, take the mean of popularity.

-Sampling distribution: from sampling_distribution, take its mean.

-Bootstrap distribution: from bootstrap_distribution, take its mean.

      # Calculate the population mean popularity
      pop_mean = spotify_population["popularity"].mean()

      # Calculate the original sample mean popularity
      samp_mean = np.mean(spotify_sample["popularity"])

      # Calculate the sampling dist'n estimate of mean popularity
      samp_distn_mean = np.mean(sampling_distribution)

      # Calculate the bootstrap dist'n estimate of mean popularity
      boot_distn_mean = np.mean(bootstrap_distribution)

      # Print the means
      print([pop_mean, samp_mean, samp_distn_mean, boot_distn_mean])


**Compare sampling and bootstrap standard deviations**

In the same way that you looked at how the sampling distribution and bootstrap distribution could be used to estimate the population mean, you'll now take a look at how they can be used to estimate variation, or more specifically, the standard deviation, in the population.

Recall that the sample size is 5000.

spotify_population, spotify_sample, sampling_distribution, and bootstrap_distribution are available; pandas and numpy are loaded with their usual aliases.

Instructions:

Calculate the standard deviation of popularity in 4 ways.

-Population: from spotify_population, take the standard deviation of popularity.

-Original sample: from spotify_sample, take the standard deviation of popularity.

-Sampling distribution: from sampling_distribution, take its standard deviation and multiply by the square root of the sample size (5000).

-Bootstrap distribution: from bootstrap_distribution, take its standard deviation and multiply by the square root of the sample size.

      # Calculate the population std dev popularity
      pop_sd = spotify_population["popularity"].std(ddof=0)

      # Calculate the original sample std dev popularity
      samp_sd = spotify_sample["popularity"].std(ddof=1)

      # Calculate the sampling dist'n estimate of std dev popularity
      samp_distn_sd = np.std(sampling_distribution, ddof=1) * np.sqrt(5000)

      # Calculate the bootstrap dist'n estimate of std dev popularity
      boot_distn_sd = np.std(bootstrap_distribution, ddof=1) * np.sqrt(5000)

      # Print the standard deviations
      print([pop_sd, samp_sd, samp_distn_sd, boot_distn_sd])

# Confidence intervals

**Personal notes:**

Quantifying distributions can be done through the concept of "values within one standard deviation of the mean."

**Exercises:**

**Calculating confidence intervals**

You have learned about two methods for calculating confidence intervals: the quantile method and the standard error method. The standard error method involves using the inverse cumulative distribution function (inverse CDF) of the normal distribution to calculate confidence intervals. In this exercise, you'll perform these two methods on the Spotify data.

spotify_population, spotify_sample, and bootstrap_distribution are available; pandas and numpy are loaded with their usual aliases, and norm has been loaded from scipy.stats.

Instructions:

-Generate a 95% confidence interval using the quantile method on the bootstrap distribution, setting the 0.025 quantile as lower_quant and the 0.975 quantile as upper_quant.

      # Generate a 95% confidence interval using the quantile method
      lower_quant = np.quantile(bootstrap_distribution, 0.025)
      upper_quant = np.quantile(bootstrap_distribution, 0.975)

      # Print quantile method confidence interval
      print((lower_quant, upper_quant))

-Generate a 95% confidence interval using the standard error method from the bootstrap distribution.

-Calculate point_estimate as the mean of bootstrap_distribution, and standard_error as the standard deviation of bootstrap_distribution.

-Calculate lower_se as the 0.025 quantile of an inv. CDF from a normal distribution with mean point_estimate and standard deviation standard_error.

-Calculate upper_se as the 0.975 quantile of that same inv. CDF.

      # Find the mean and std dev of the bootstrap distribution
      point_estimate = np.mean(bootstrap_distribution)
      standard_error = np.std(bootstrap_distribution, ddof=1)

      # Find the lower limit of the confidence interval
      lower_se = norm.ppf(0.025, loc=point_estimate, scale=standard_error)

      # Find the upper limit of the confidence interval
      upper_se = norm.ppf(0.975, loc=point_estimate, scale=standard_error)

      # Print standard error method confidence interval
      print((lower_se, upper_se))