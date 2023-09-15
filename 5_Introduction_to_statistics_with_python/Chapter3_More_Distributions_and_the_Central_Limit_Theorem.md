# More Distributions and the Central Limit Theorem

**Description:**

It’s time to explore one of the most important probability distributions in statistics, normal distribution. You’ll create histograms to plot normal distributions and gain an understanding of the central limit theorem, before expanding your knowledge of statistical functions by adding the Poisson, exponential, and t-distributions to your repertoire.

# The normal distribution

**Personal notes:**

The normal distribution, also known as the Gaussian distribution, is one of the most important probability distributions in statistics. It has widespread applications in various fields and is often referred to as the "bell curve" due to its characteristic symmetric shape.

Key properties of the normal distribution:

1. Symmetry: The normal distribution is symmetric, meaning that the left side is a mirror image of the right side when plotted on a graph.

2. Area under the curve: The total area under the curve of the normal distribution is always equal to 1, representing the probability of all possible outcomes.

3. Continuous probability: Unlike discrete distributions, the normal distribution assigns a non-zero probability to every possible real number, even though the probabilities become extremely small in the tails of the distribution.

The normal distribution is characterized by two parameters:

- Mean (μ): The mean represents the central location of the distribution and determines where the peak of the curve is located.

- Standard deviation (σ): The standard deviation measures the spread or dispersion of the data points. Larger standard deviations result in wider and flatter curves, while smaller standard deviations result in narrower and taller curves.

When a normal distribution has a mean of 0 and a standard deviation of 1, it is referred to as the standard normal distribution. The standard normal distribution is often used as a reference distribution in statistical calculations.

Empirical Rule (68-95-99.7 Rule):

- Approximately 68% of the data falls within one standard deviation of the mean.

- Approximately 95% of the data falls within two standard deviations of the mean.

- Approximately 99.7% of the data falls within three standard deviations of the mean.

In Python, you can work with the normal distribution using the SciPy library. Functions like `norm.cdf()` and `norm.ppf()` allow you to calculate probabilities and percentiles of the normal distribution, respectively. The `norm.rvs()` function generates random samples from a normal distribution with specified parameters.

Understanding the normal distribution is crucial in statistics, as many statistical methods and tests are based on the assumption that data follows a normal distribution, or they require normality for valid inference.

**Exercises:**

**Distribution of Amir's sales**

Since each deal Amir worked on (both won and lost) was different, each was worth a different amount of money. These values are stored in the amount column of amir_deals As part of Amir's performance review, you want to be able to estimate the probability of him selling different amounts, but before you can do this, you'll need to determine what kind of distribution the amount variable follows.

Both pandas as pd and matplotlib.pyplot as plt are loaded and amir_deals is available.

Instructions:

-Create a histogram with 10 bins to visualize the distribution of the amount. Show the plot.

      # Histogram of amount with 10 bins and show plot
      amir_deals["amount"].hist(bins=10)
      plt.show()

![Image46](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/95dbe498-a6ea-4d4b-9707-9dc6a5421096)

**Probabilities from the normal distribution**

Since each deal Amir worked on (both won and lost) was different, each was worth a different amount of money. These values are stored in the amount column of amir_deals and follow a normal distribution with a mean of 5000 dollars and a standard deviation of 2000 dollars. As part of his performance metrics, you want to calculate the probability of Amir closing a deal worth various amounts.

norm from scipy.stats is imported as well as pandas as pd. The DataFrame amir_deals is loaded.

Instructions:

-What's the probability of Amir closing a deal worth less than $7500?

      # Probability of deal < 7500
      prob_less_7500 = norm.cdf(7500, 5000, 2000)

      print(prob_less_7500)

-What's the probability of Amir closing a deal worth more than $1000?

      # Probability of deal > 1000
      prob_over_1000 = 1 - norm.cdf(1000, 5000, 2000)

      print(prob_over_1000)

-What's the probability of Amir closing a deal worth between $3000 and $7000?

      # Probability of deal between 3000 and 7000
      prob_3000_to_7000 = norm.cdf(7000, 5000, 2000) - norm.cdf(3000, 5000, 2000)

      print(prob_3000_to_7000)
   
-What amount will 25% of Amir's sales be less than?

      # Calculate amount that 25% of deals will be less than
      pct_25 = norm.ppf(0.25, 5000, 2000)

      print(pct_25)

**Simulating sales under new market conditions**

The company's financial analyst is predicting that next quarter, the worth of each sale will increase by 20% and the volatility, or standard deviation, of each sale's worth will increase by 30%. To see what Amir's sales might look like next quarter under these new market conditions, you'll simulate new sales amounts using the normal distribution and store these in the new_sales DataFrame, which has already been created for you.

In addition, norm from scipy.stats, pandas as pd, and matplotlib.pyplot as plt are loaded.

Instructions:

-Currently, Amir's average sale amount is $5000. Calculate what his new average amount will be if it increases by 20% and store this in new_mean.

-Amir's current standard deviation is $2000. Calculate what his new standard deviation will be if it increases by 30% and store this in new_sd.

-Create a variable called new_sales, which contains 36 simulated amounts from a normal distribution with a mean of new_mean and a standard deviation of new_sd.

-Plot the distribution of the new_sales amounts using a histogram and show the plot.

      # Calculate new average amount
      new_mean = 5000 * 1.2

      # Calculate new standard deviation
      new_sd = 2000 * 1.3

      # Simulate 36 new sales
      new_sales = norm.rvs(new_mean, new_sd, size=36)

      # Create histogram and show
      plt.hist(new_sales)
      plt.show()

![Image47](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/db44766e-1f15-4add-a045-6ccb4d19485c)

**Which market is better?**
The key metric that the company uses to evaluate salespeople is the percent of sales they make over $1000 since the time put into each sale is usually worth a bit more than that, so the higher this metric, the better the salesperson is performing.

Recall that Amir's current sales amounts have a mean of $5000 and a standard deviation of $2000, and Amir's predicted amounts in next quarter's market have a mean of $6000 and a standard deviation of $2600.

norm from scipy.stats is imported.

Based only on the metric of percent of sales over $1000, does Amir perform better in the current market or the predicted market?

      Amir performs about equally in both markets.

# The central limit theorem

**Personal notes:**

The Central Limit Theorem (CLT) is a fundamental concept in statistics that describes the behavior of the sampling distribution of the sample mean (or other sample statistics) as the sample size increases, regardless of the shape of the population distribution. The key points about the Central Limit Theorem are as follows:

1. **Approximation to Normal Distribution:* According to the CLT, when you take random samples from a population (with replacement or sufficiently large samples without replacement) and calculate the sample means, the distribution of those sample means will tend to follow a normal distribution, even if the original population distribution is not normal. This is true as long as the sample size is sufficiently large (typically, n ≥ 30 is considered large enough).

2. **Random and Independent Samples:* The samples must be random and independent. In other words, each observation in a sample should be chosen randomly, and the selection of one observation should not affect the selection of others. For example, random sampling with replacement or sufficiently large samples without replacement satisfies this condition.

3. **Sample Size Matters:* As the sample size increases, the sampling distribution of the sample mean becomes closer and closer to a normal distribution. This means that for sufficiently large sample sizes, you can make inferences about population parameters (e.g., population mean) using the properties of the normal distribution.

The CLT is a powerful concept because it allows statisticians and data analysts to make statistical inferences about population parameters, even when the population distribution is unknown or not normal. It's particularly useful in hypothesis testing, confidence interval estimation, and other statistical analyses.

Additionally, the CLT is not limited to the sample mean; it also applies to other sample statistics, such as the sample variance, sample proportion, and more. This makes it a versatile tool in statistical analysis.

In practical terms, the CLT is often used when dealing with large populations or when it's impractical to collect data on the entire population. By taking random samples and applying the CLT, you can make valid statistical conclusions about the population based on the properties of the normal distribution.

**Exercises:**

**The CLT in action**

The central limit theorem states that a sampling distribution of a sample statistic approaches the normal distribution as you take more samples, no matter the original distribution being sampled from.

In this exercise, you'll focus on the sample mean and see the central limit theorem in action while examining the num_users column of amir_deals more closely, which contains the number of people who intend to use the product Amir is selling.

pandas as pd, numpy as np, and matplotlib.pyplot as plt are loaded and amir_deals is available.

Instructions:

-Create a histogram of the num_users column of amir_deals and show the plot.

      # Create a histogram of num_users and show
      amir_deals["num_users"].hist()
      plt.show()

![Image48](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d0722260-e69f-429d-bb54-a8187e6fc717)

-Set the seed to 104.

-Take a sample of size 20 with replacement from the num_users column of amir_deals, and take the mean.

      # Set seed to 104
      np.random.seed(104)

      # Sample 20 num_users with replacement from amir_deals
      samp_20 = amir_deals["num_users"].sample(20, replace=True)

      # Take mean of samp_20
      print(np.mean(samp_20))

-Repeat this 100 times using a for loop and store as sample_means. This will take 100 different samples and calculate the mean of each.

      # Set seed to 104
      np.random.seed(104)

      # Sample 20 num_users with replacement from amir_deals and take mean
      samp_20 = amir_deals['num_users'].sample(20, replace=True)
      np.mean(samp_20)

      sample_means = []
      # Loop 100 times
      for i in range(100):
      # Take sample of 20 num_users
      samp_20 = amir_deals['num_users'].sample(20, replace=True)
      # Calculate mean of samp_20
      samp_20_mean = np.mean(samp_20)
      # Append samp_20_mean to sample_means
      sample_means.append(samp_20_mean)
  
      print(sample_means)

-Convert sample_means into a pd.Series, create a histogram of the sample_means, and show the plot.

      # Set seed to 104
      np.random.seed(104)

      sample_means = []
      # Loop 100 times
      for i in range(100):
      # Take sample of 20 num_users
      samp_20 = amir_deals['num_users'].sample(20, replace=True)
      # Calculate mean of samp_20
      samp_20_mean = np.mean(samp_20)
      # Append samp_20_mean to sample_means
      sample_means.append(samp_20_mean)
  
      # Convert to Series and plot histogram
      sample_means_series = pd.Series(sample_means)
      sample_means_series.hist()
      # Show plot
      plt.show()

![Image49](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/48d66a05-063a-43ab-afa2-63b64d85460e)

**The mean of means**

You want to know what the average number of users (num_users) is per deal, but you want to know this number for the entire company so that you can see if Amir's deals have more or fewer users than the company's average deal. The problem is that over the past year, the company has worked on more than ten thousand deals, so it's not realistic to compile all the data. Instead, you'll estimate the mean by taking several random samples of deals, since this is much easier than collecting data from everyone in the company.

amir_deals is available and the user data for all the company's deals is available in all_deals. Both pandas as pd and numpy as np are loaded.

Instructions:

-Set the random seed to 321.

-Take 30 samples (with replacement) of size 20 from all_deals['num_users'] and take the mean of each sample. Store the sample means in sample_means.

-Print the mean of sample_means.

-Print the mean of the num_users column of amir_deals.

      # Set seed to 321
      np.random.seed(321)

      sample_means = []
      # Loop 30 times to take 30 means
      for i in range(30):
      # Take sample of size 20 from num_users col of all_deals with replacement
      cur_sample = all_deals['num_users'].sample(20, replace=True)
      # Take mean of cur_sample
      cur_mean = np.mean(cur_sample)
      # Append cur_mean to sample_means
      sample_means.append(cur_mean)

      # Print mean of sample_means
      print(np.mean(sample_means))

      # Print mean of num_users in amir_deals
      print(amir_deals["num_users"].mean())

# The Poisson distribution

**Personal notes:**

The Poisson distribution is a probability distribution commonly used to model the number of events that occur in a fixed interval of time or space when the events happen at a known average rate but are independent of the time since the last event. Key points about the Poisson distribution include:

1. **Rate Parameter (λ):* The Poisson distribution is parameterized by a single parameter, often denoted as λ (lambda), which represents the average rate of events occurring in the specified interval. This parameter tells you how many events you expect to occur on average in that interval.

2. **Events are Discrete:* The Poisson distribution deals with discrete events, such as the number of customer arrivals at a store in an hour, the number of phone calls received at a call center in a day, or the number of accidents at an intersection in a month.

3. **Probability Mass Function (PMF):* You can calculate the probability of observing a specific number of events (k) in the interval using the probability mass function (PMF) of the Poisson distribution. The PMF is given by:

   \[P(X = k) = \frac{e^{-λ} * λ^k}{k!}\]

   Where:
   - \(P(X = k)\) is the probability of observing exactly k events.
   - \(λ\) is the average rate of events.
   - \(e\) is the base of the natural logarithm (approximately 2.71828).
   - \(k\) is the specific number of events you want to calculate the probability for.
   - \(k!\) represents the factorial of k.

4. **Cumulative Distribution Function (CDF):* You can also calculate the probability of observing less than or equal to a certain number of events (K) using the cumulative distribution function (CDF) of the Poisson distribution. The CDF is given by:

   \[P(X \leq K) = \sum_{k=0}^{K} \frac{e^{-λ} * λ^k}{k!}\]

   Where:
   - \(P(X \leq K)\) is the probability of observing K or fewer events.
   - The summation goes from \(k = 0\) to \(k = K\).

5. **Simulation:* You can generate random samples from a Poisson distribution using libraries like SciPy in Python. The `poisson.rvs()` function allows you to simulate random samples with a specified average rate (λ) and sample size.

The Poisson distribution is particularly useful for modeling rare events or events with low probabilities, such as accidents, customer arrivals, or rare defects in a manufacturing process. It's an essential tool in various fields, including queuing theory, epidemiology, and reliability analysis.

**Exercises:**

**Tracking lead responses**

Your company uses sales software to keep track of new sales leads. It organizes them into a queue so that anyone can follow up on one when they have a bit of free time. Since the number of lead responses is a countable outcome over a period of time, this scenario corresponds to a Poisson distribution. On average, Amir responds to 4 leads each day. In this exercise, you'll calculate probabilities of Amir responding to different numbers of leads.

Instructions:

-Import poisson from scipy.stats and calculate the probability that Amir responds to 5 leads in a day, given that he responds to an average of 4.

      # Import poisson from scipy.stats
      from scipy.stats import poisson

      # Probability of 5 responses
      prob_5 = poisson.pmf(5, 4)

      print(prob_5)

-Amir's coworker responds to an average of 5.5 leads per day. What is the probability that she answers 5 leads in a day?

      # Import poisson from scipy.stats
      from scipy.stats import poisson

      # Probability of 5 responses
      prob_coworker = poisson.pmf(5, 5.5)

      print(prob_coworker)

-What's the probability that Amir responds to 2 or fewer leads in a day?

      # Import poisson from scipy.stats
      from scipy.stats import poisson

      # Probability of 2 or fewer responses
      prob_2_or_less = poisson.cdf(2, 4)

      print(prob_2_or_less)
   
-What's the probability that Amir responds to more than 10 leads in a day?

      # Import poisson from scipy.stats
      from scipy.stats import poisson

      # Probability of > 10 responses
      prob_over_10 = 1 - poisson.cdf(10, 4)

      print(prob_over_10)

# More probability distributions

**Personal notes:**

You've provided a summary of several probability distributions, and I'll expand on each of them:

1. **Exponential Distribution:*
   - The exponential distribution models the probability of time passing between events following a Poisson process.
   - It is often used to predict scenarios like the time between customer arrivals at a restaurant, the time between adoptions of pets, or the time between earthquakes.
   - The parameter in the exponential distribution, often denoted as λ (lambda), represents the rate at which events occur.
   - It is a continuous distribution, as it deals with time intervals.
   - The expected value of the exponential distribution is given by \(E(X) = \frac{1}{\lambda}\).
   - You can calculate probabilities using the cumulative distribution function (CDF) with `expon.cdf()`.
   - For probabilities greater than a certain value, subtract the CDF value from 1.

2. **t-Distribution (Student's t-Distribution):*
   - The t-distribution is similar in shape to the normal distribution but has thicker tails, which means it is more likely to have observations far from the mean.
   - The t-distribution has a parameter called degrees of freedom (df), which influences the thickness of the tails.
   - For a small number of degrees of freedom, the t-distribution has fatter tails and higher variance compared to the normal distribution.
   - As the degrees of freedom increase, the t-distribution approaches the normal distribution.
   - It is commonly used in hypothesis testing when the population standard deviation is unknown and must be estimated from the sample data.

3. **Log-Normal Distribution:*
   - The log-normal distribution is used to model data where the natural logarithm of the variable follows a normal distribution.
   - This results in a distribution with a right-skewed (positively skewed) shape, as the logarithm of a variable can't be negative.
   - Many real-world phenomena exhibit log-normal behavior, such as the lengths of chess games, adult blood pressure, or the number of hospitalizations during disease outbreaks.
   - The distribution has two parameters: μ (mu) and σ (sigma), which correspond to the mean and standard deviation of the associated normal distribution.
   - The log-normal distribution is commonly used in finance to model asset prices and in biology to describe the size distribution of biological populations.

Each of these probability distributions has its own characteristics and use cases in various fields of statistics and data analysis. Understanding these distributions is essential for making informed decisions and drawing meaningful conclusions from data.

**Exercises:**

**Modeling time between leads**

To further evaluate Amir's performance, you want to know how much time it takes him to respond to a lead after he opens it. On average, he responds to 1 request every 2.5 hours. In this exercise, you'll calculate probabilities of different amounts of time passing between Amir receiving a lead and sending a response.

Instructions:

-Import expon from scipy.stats. What's the probability it takes Amir less than an hour to respond to a lead?

      # Import expon from scipy.stats
      from scipy.stats import expon

      # Print probability response takes < 1 hour
      print(expon.cdf(1, scale=2.5))

-What's the probability it takes Amir more than 4 hours to respond to a lead?

      # Import expon from scipy.stats
      from scipy.stats import expon

      # Print probability response takes > 4 hours
      print(1 - expon.cdf(4, scale=2.5))

-What's the probability it takes Amir 3-4 hours to respond to a lead?

      # Import expon from scipy.stats
      from scipy.stats import expon

      # Print probability response takes 3-4 hours
      print(expon.cdf(3, scale=2.5) - expon.cdf(4, scale=2.5))