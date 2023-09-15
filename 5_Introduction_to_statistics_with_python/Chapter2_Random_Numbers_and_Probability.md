# Random Numbers and Probability

**Description:**

In this chapter, you'll learn how to generate random samples and measure chance using probability. You'll work with real-world sales data to calculate the probability of a salesperson being successful. Finally, you’ll use the binomial distribution to model events with binary outcomes.

# What are the chances?

**Personal notes:**

Probability is a measure of the likelihood of an event occurring. It can be calculated by taking the number of ways the event can happen and dividing it by the total number of possible outcomes. Probability always falls between 0 and 100 percent.

Sampling from a DataFrame can be done using the `.sample()` method. By default, it randomly selects one row from the DataFrame, and the selection is random each time you use it.

To ensure reproducibility when using random sampling, you can set a random seed using `np.random.seed(x)`. When you set a random seed, the random sampling will produce the same result each time you use that specific seed. This is useful for generating the same random selections when needed.

Sampling with replacement can be done by setting the `replace` argument to `True` in the `DataFrame.sample()` method. This allows variables to be sampled more than once, and you can specify the number of times you want the sampling to be done.

Events are considered independent when the outcome of one event does not affect the probability of the second event. Conversely, events are considered dependent when the result of the first event alters the probability of the second event.

**Exercises:**

**Calculating probabilities**

You're in charge of the sales team, and it's time for performance reviews, starting with Amir. As part of the review, you want to randomly select a few of the deals that he's worked on over the past year so that you can look at them more deeply. Before you start selecting deals, you'll first figure out what the chances are of selecting certain deals.

Both pandas as pd and numpy as np are loaded and amir_deals is available.

Instructions: 

-Count the number of deals Amir worked on for each product type and store in counts.

-Calculate the probability of selecting a deal for the different product types by dividing the counts by the total number of deals Amir worked on. Save this as probs.

    # Count the deals for each product
    counts = amir_deals['product'].value_counts()

    # Calculate probability of picking a deal with each product
    probs = counts / len(amir_deals["product"])
    print(probs)

**Sampling deals**

In the previous exercise, you counted the deals Amir worked on. Now it's time to randomly pick five deals so that you can reach out to each customer and ask if they were satisfied with the service they received. You'll try doing this both with and without replacement.

Additionally, you want to make sure this is done randomly and that it can be reproduced in case you get asked how you chose the deals, so you'll need to set the random seed before sampling from the deals.

Both pandas as pd and numpy as np are loaded and amir_deals is available.

Instructions:

-Set the random seed to 24.

-Take a sample of 5 deals without replacement and store them as sample_without_replacement.

    # Set random seed
    np.random.seed(24)
    # Sample 5 deals without replacement
    sample_without_replacement = amir_deals.sample(5, replace=False)
    print(sample_without_replacement)

-Take a sample of 5 deals with replacement and save as sample_with_replacement.

    # Set random seed
    np.random.seed(24)

    # Sample 5 deals with replacement
    sample_with_replacement = amir_deals.sample(5, replace=True)
    print(sample_with_replacement)

# Discrete distributions

**Personal notes:**

Probability distributions describe the likelihood of each possible outcome in a scenario. They can be used to model situations involving discrete or countable variables.

The expected value, also known as the mean, of a probability distribution is calculated by multiplying each value by its probability and summing up all the probabilities.

Discrete probability distributions are used to represent situations with discrete outcomes. Discrete variables can be thought of as countable variables.

A discrete uniform distribution occurs when all outcomes have the same probability of occurring.

The Law of Large Numbers states that as the sample size increases, the sample mean will approach the theoretical mean. In other words, as you collect more data, the sample average will get closer to the population average. This is a fundamental concept in statistics.

**Exercises:**

**Creating a probability distribution**

A new restaurant opened a few months ago, and the restaurant's management wants to optimize its seating space based on the size of the groups that come most often. On one night, there are 10 groups of people waiting to be seated at the restaurant, but instead of being called in the order they arrived, they will be called randomly. In this exercise, you'll investigate the probability of groups of different sizes getting picked first. Data on each of the ten groups is contained in the restaurant_groups DataFrame.

Remember that expected value can be calculated by multiplying each possible outcome with its corresponding probability and taking the sum. The restaurant_groups data is available. pandas is loaded as pd, numpy is loaded as np, and matplotlib.pyplot is loaded as plt.

Instructions:

-Create a histogram of the group_size column of restaurant_groups, setting bins to [2, 3, 4, 5, 6]. Remember to show the plot.

    # Create a histogram of restaurant_groups and show plot
    restaurant_groups['group_size'].hist(bins=[2, 3, 4, 5, 6])
    plt.show()

![Image44](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/64d60481-8ab6-41bb-9765-4557f02a041d)

-Count the number of each group_size in restaurant_groups, then divide by the number of rows in restaurant_groups to calculate the probability of randomly selecting a group of each size. Save as size_dist.

-Reset the index of size_dist.

-Rename the columns of size_dist to group_size and prob.

    # Create probability distribution
    size_dist = restaurant_groups["group_size"] / restaurant_groups.shape[0]

    # Reset index and rename columns
    size_dist = size_dist.reset_index()
    size_dist.columns = ['group_size', 'prob']
    print(size_dist)

-Calculate the expected value of the size_distribution, which represents the expected group size, by multiplying the group_size by the prob and taking the sum.

    # Create probability distribution
    size_dist = restaurant_groups['group_size'].value_counts() / restaurant_groups.shape[0]
    # Reset index and rename columns
    size_dist = size_dist.reset_index()
    size_dist.columns = ['group_size', 'prob']

    # Calculate expected value
    expected_value = (size_dist["group_size"] * size_dist["prob"]).sum()
    print(expected_value)

-Calculate the probability of randomly picking a group of 4 or more people by subsetting for groups of size 4 or more and summing the probabilities of selecting those groups.

    # Create probability distribution
    size_dist = restaurant_groups['group_size'].value_counts() / restaurant_groups.shape[0]
    # Reset index and rename columns
    size_dist = size_dist.reset_index()
    size_dist.columns = ['group_size', 'prob']

    # Expected value
    expected_value = np.sum(size_dist['group_size'] * size_dist['prob'])

    # Subset groups of size 4 or more
    groups_4_or_more = size_dist[size_dist["group_size"] >= 4]

    # Sum the probabilities of groups_4_or_more
    prob_4_or_more = groups_4_or_more["prob"].sum()
    print(prob_4_or_more)

# Continuous distribution

**Personal notes:**

Continuous distributions are used to model continuous variables, which can take on any real value within a certain range.

A continuous uniform distribution is a specific type of continuous distribution in which all values within a specified range have equal probability.

In Python, you can calculate probabilities for a continuous uniform distribution using functions from libraries like SciPy. The `uniform.cdf()` function calculates the cumulative distribution function, which gives the probability that a random variable is less than or equal to a specific value. The `uniform.rvs()` function generates random numbers according to a uniform distribution within a specified range.

Continuous distributions can take various shapes, not just uniform ones. Different continuous distributions represent different patterns of probabilities for different values. Regardless of the distribution's shape, the total area under the curve must always equal 1, as it represents the entire probability space.

**Exercises:**

**Data back-ups**

The sales software used at your company is set to automatically back itself up, but no one knows exactly what time the back-ups happen. It is known, however, that back-ups happen exactly every 30 minutes. Amir comes back from sales meetings at random times to update the data on the client he just met with. He wants to know how long he'll have to wait for his newly-entered data to get backed up. Use your new knowledge of continuous uniform distributions to model this situation and answer Amir's questions.

Instructions:

-To model how long Amir will wait for a back-up using a continuous uniform distribution, save his lowest possible wait time as min_time and his longest possible wait time as max_time. Remember that back-ups happen every 30 minutes.

-Import uniform from scipy.stats and calculate the probability that Amir has to wait less than 5 minutes, and store in a variable called prob_less_than_5.

    # Min and max wait times for back-up that happens every 30 min
    min_time = 0
    max_time = 30

    # Import uniform from scipy.stats
    from scipy.stats import uniform

    # Calculate probability of waiting less than 5 mins
    prob_less_than_5 = uniform.cdf(5, min_time, max_time)
    print(prob_less_than_5)

-Calculate the probability that Amir has to wait more than 5 minutes, and store in a variable called prob_greater_than_5.

    # Min and max wait times for back-up that happens every 30 min
    min_time = 0
    max_time = 30

    # Import uniform from scipy.stats
    from scipy.stats import uniform

    # Calculate probability of waiting more than 5 mins
    prob_greater_than_5 = 1 - uniform.cdf(5, min_time, max_time)
    print(prob_greater_than_5)

-Calculate the probability that Amir has to wait between 10 and 20 minutes, and store in a variable called prob_between_10_and_20.

    # Min and max wait times for back-up that happens every 30 min
    min_time = 0
    max_time = 30

    # Import uniform from scipy.stats
    from scipy.stats import uniform

    # Calculate probability of waiting 10-20 mins
    prob_between_10_and_20 = uniform.cdf(20, min_time, max_time) - \
                            uniform.cdf(10, min_time, max_time)
    print(prob_between_10_and_20)

**Simulating wait times**

To give Amir a better idea of how long he'll have to wait, you'll simulate Amir waiting 1000 times and create a histogram to show him what he should expect. Recall from the last exercise that his minimum wait time is 0 minutes and his maximum wait time is 30 minutes.

As usual, pandas as pd, numpy as np, and matplotlib.pyplot as plt are loaded.

Instructions:

-Set the random seed to 334.

-Import uniform from scipy.stats.

-Generate 1000 wait times from the continuous uniform distribution that models Amir's wait time. Save this as wait_times.

-Create a histogram of the simulated wait times and show the plot.

    # Set random seed to 334
    np.random.seed(334)

    # Import uniform
    from scipy.stats import uniform

    # Generate 1000 wait times between 0 and 30 mins
    wait_times = uniform.rvs(0, 30, size=1000)

    # Create a histogram of simulated times and show plot
    plt.hist(wait_times)
    plt.show()

![Image45](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/f771f8b7-719c-46da-b14c-6046fc6b370f)

# The binomial distribution

**Personal notes:**

The binomial distribution is a probability distribution that describes the number of successes (e.g., heads in a coin toss) in a fixed number of independent and identically distributed Bernoulli trials (e.g., repeated coin tosses). It is characterized by two parameters: `n` (the number of trials) and `p` (the probability of success on each trial).

In Python, you can work with the binomial distribution using the SciPy library. The `binom.rvs()` function generates random samples from a binomial distribution, where you specify the number of trials (`n`), the probability of success (`p`), and the number of samples to generate (`size`).

The `binom.pmf()` function calculates the probability mass function, which gives the probability of obtaining exactly `x` successes in `n` trials with a probability of success `p`. You can use this function to calculate specific probabilities related to the binomial distribution.

The expected value (mean) of a binomial distribution is given by `n * p`, which represents the average number of successes you would expect in `n` trials with a success probability of `p`. This expected value is a key parameter for understanding the distribution.

It's important to note that the binomial distribution assumes that each trial is independent of the others, meaning the outcome of one trial does not affect the outcome of subsequent trials. This independence condition is crucial for the applicability of the binomial distribution.

**Exercises:**

**Simulating sales deals**

Assume that Amir usually works on 3 deals per week, and overall, he wins 30% of deals he works on. Each deal has a binary outcome: it's either lost, or won, so you can model his sales deals with a binomial distribution. In this exercise, you'll help Amir simulate a year's worth of his deals so he can better understand his performance.

numpy is imported as np.

Instructions:

-Import binom from scipy.stats and set the random seed to 10.

-Simulate 1 deal worked on by Amir, who wins 30% of the deals he works on.

    # Import binom from scipy.stats
    from scipy.stats import binom

    # Set random seed to 10
    np.random.seed(10)

    # Simulate a single deal
    print(binom.rvs(1, 0.3, size=1))

-Simulate a typical week of Amir's deals, or one week of 3 deals.

    # Import binom from scipy.stats
    from scipy.stats import binom

    # Set random seed to 10
    np.random.seed(10)

    # Simulate 1 week of 3 deals
    print(binom.rvs(3, 0.3, size=1))

-Simulate a year's worth of Amir's deals, or 52 weeks of 3 deals each, and store in deals.

-Print the mean number of deals he won per week.

    # Import binom from scipy.stats
    from scipy.stats import binom

    # Set random seed to 10
    np.random.seed(10)

    # Simulate 52 weeks of 3 deals
    deals = binom.rvs(3, 0.3, size=52)

    # Print mean deals won per week
    print(np.mean(deals)) 

**Calculating binomial probabilities**

Just as in the last exercise, assume that Amir wins 30% of deals. He wants to get an idea of how likely he is to close a certain number of deals each week. In this exercise, you'll calculate what the chances are of him closing different numbers of deals using the binomial distribution.

binom is imported from scipy.stats.

Instructions:

-What's the probability that Amir closes all 3 deals in a week? Save this as prob_3.

    # Probability of closing 3 out of 3 deals
    prob_3 = binom.pmf(3, 3, 0.3)

    print(prob_3)

-What's the probability that Amir closes 1 or fewer deals in a week? Save this as prob_less_than_or_equal_1.

    # Probability of closing <= 1 deal out of 3 deals
    prob_less_than_or_equal_1 = binom.cdf(1, 3, 0.3)

    print(prob_less_than_or_equal_1)

-What's the probability that Amir closes more than 1 deal? Save this as prob_greater_than_1.

    # Probability of closing > 1 deal out of 3 deals
    prob_greater_than_1 = 1 - binom.cdf(1, 3, 0.3)

    print(prob_greater_than_1)

**How many sales will be won?**

Now Amir wants to know how many deals he can expect to close each week if his win rate changes. Luckily, you can use your binomial distribution knowledge to help him calculate the expected value in different situations. Recall from the video that the expected value of a binomial distribution can be calculated by n x p.

Instructions:

-Calculate the expected number of sales out of the 3 he works on that Amir will win each week if he maintains his 30% win rate.

-Calculate the expected number of sales out of the 3 he works on that he'll win if his win rate drops to 25%.

-Calculate the expected number of sales out of the 3 he works on that he'll win if his win rate rises to 35%.

    # Expected number won with 30% win rate
    won_30pct = 3 * 0.3
    print(won_30pct)

    # Expected number won with 25% win rate
    won_25pct = 3 * 0.25
    print(won_25pct)

    # Expected number won with 35% win rate
    won_35pct = 3 * 0.35
    print(won_35pct)
