# Sampling in Python

**Course description:**

Sampling in Python is the cornerstone of inference statistics and hypothesis testing. It's a powerful skill used in survey analysis and experimental design to draw conclusions without surveying an entire population. In this Sampling in Python course, you’ll discover when to use sampling and how to perform common types of sampling—from simple random sampling to more complex methods like stratified and cluster sampling. Using real-world datasets, including coffee ratings, Spotify songs, and employee attrition, you’ll learn to estimate population statistics and quantify uncertainty in your estimates by generating sampling distributions and bootstrap distributions.

# Introduction to Sampling

**Description:**

Learn what sampling is and why it is so powerful. You’ll also learn about the problems caused by convenience sampling and the differences between true randomness and pseudo-randomness.

# Sampling and point estimates

**Personal notes:**

The population is the complete set of data we're interested in. The sample is the subset of data we're working with.

The `sample` method - returns a random subset of rows. Setting `n` to 10 means that ten random rows are returned.

A population parameter is a calculation made on the population dataset. While a point estimate or sample statistic is a calculation based on the sample dataset.

**Exercises:**

**Simple sampling with pandas**

Throughout this chapter, you'll be exploring song data from Spotify. Each row of this population dataset represents a song, and there are over 40,000 rows. Columns include the song name, the artists who performed it, the release year, and attributes of the song like its duration, tempo, and danceability. You'll start by looking at the durations.

Your first task is to sample the Spotify dataset and compare the mean duration of the population with the sample.

spotify_population is available and pandas is loaded as pd.

Instructions:

-Sample 1000 rows from spotify_population, assigning to spotify_sample.

-Calculate the mean duration in minutes from spotify_population using pandas.

-Calculate the mean duration in minutes from spotify_sample using pandas.

    # Sample 1000 rows from spotify_population
    spotify_sample = spotify_population.sample(n=1000)

    # Print the sample
    print(spotify_sample)

    # Calculate the mean duration in mins from spotify_population
    mean_dur_pop = spotify_population["duration_minutes"].mean()

    # Calculate the mean duration in mins from spotify_sample
    mean_dur_samp = spotify_sample["duration_minutes"].mean()

    # Print the means
    print(mean_dur_pop)
    print(mean_dur_samp)

**Simple sampling and calculating with NumPy**

You can also use numpy to calculate parameters or statistics from a list or pandas Series.

You'll be turning it up to eleven and looking at the loudness property of each song.

spotify_population is available and numpy is loaded as np.

Instructions:

-Create a pandas Series, loudness_pop, by subsetting the loudness column from spotify_population.

-Sample loudness_pop to get 100 random values, assigning to loudness_samp.

-Calculate the mean of loudness_pop using numpy.

-Calculate the mean of loudness_samp using numpy.

    # Create a pandas Series from the loudness column of spotify_population
    loudness_pop = spotify_population['loudness']

    # Sample 100 values of loudness_pop
    loudness_samp = loudness_pop.sample(n=100)

    # Calculate the mean of loudness_pop
    mean_loudness_pop = loudness_pop.mean()

    # Calculate the mean of loudness_samp
    mean_loudness_samp = loudness_samp.mean()

    print(mean_loudness_pop)
    print(mean_loudness_samp)

# Convenience sampling

**Personal notes:**

Before sampling, we need to think about our data collection process to avoid biased results. Convenience sampling is not representative of the entire population.

**Exercises:**

**Are findings from the sample generalizable?**

You just saw how convenience sampling—collecting data using the easiest method—can result in samples that aren't representative of the population. Equivalently, this means findings from the sample are not generalizable to the population. Visualizing the distributions of the population and the sample can help determine whether or not the sample is representative of the population.

The Spotify dataset contains an acousticness column, which is a confidence measure from zero to one of whether the track was made with instruments that aren't plugged in. You'll compare the acousticness distribution of the total population of songs with a sample of those songs.

spotify_population and spotify_mysterious_sample are available; pandas as pd, matplotlib.pyplot as plt, and numpy as np are loaded.

Instructions:

-Plot a histogram of the acousticness from spotify_population with bins of width 0.01 from 0 to 1 using pandas .hist().

    # Visualize the distribution of acousticness with a histogram
    spotify_population['acousticness'].hist(bins=np.arange(0, 1.01, 0.01))
    plt.show()

![Image116](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/fbb9fa51-5b50-4f6a-b716-fd5c05204cf6)

-Update the histogram code to use the spotify_mysterious_sample dataset.

    # Update the histogram to use spotify_mysterious_sample
    spotify_mysterious_sample['acousticness'].hist(bins=np.arange(0, 1.01, 0.01))
    plt.show()

![Image117](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/238a46c5-7f91-485a-b6db-16f7638bef1f)

**Are these findings generalizable?**

Let's look at another sample to see if it is representative of the population. This time, you'll look at the duration_minutes column of the Spotify dataset, which contains the length of the song in minutes.

spotify_population and spotify_mysterious_sample2 are available; pandas, matplotlib.pyplot, and numpy are loaded using their standard aliases.

Instructions:

-Plot a histogram of duration_minutes from spotify_population with bins of width 0.5 from 0 to 15 using pandas .hist().

    # Visualize the distribution of duration_minutes as a histogram
    spotify_population['duration_minutes'].hist(bins=np.arange(0, 15.5, 0.5))
    plt.show()

![Image118](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/b6d8b669-727f-447d-9de3-81e14636beee)

-Update the histogram code to use the spotify_mysterious_sample2 dataset.

    # Update the histogram to use spotify_mysterious_sample2
    spotify_mysterious_sample2['duration_minutes'].hist(bins=np.arange(0, 15.5, 0.5))
    plt.show()

![Image119](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/00b06874-73f4-4388-b117-24dd921dbce6)

# Pseudo-random number generation

**Personal notes:**

**Pseudo-random Number Generation**

If we want to choose data points randomly from a population, we should not be able to predict which data points would be selected beforehand in some systematic way. To generate truly random numbers, we usually have to use a physical process like flipping coins or rolling dice.

Pseudo-random means that, although each value appears to be random, it's actually calculated from the previous random number. The first random number is calculated from what's known as a seed value, so if we start with a particular seed value, all future generated numbers will be the same.

- *seed=1*

  - **calc_next_random(seed)* - We choose a seed number, in this case, one. The calc_next_random variable performs some calculations and returns 3.

- **randoms = np.random.beta(a=2, b=2, size=5000)* - The first arguments to each random number function specify distribution parameters. The size argument specifies how many numbers will be generated, in this case, five thousand. In this case, the beta distribution was chosen with its parameters denoted as a and b.

- **np.random.normal(loc=2, scale=1.5, size=2)* - The .normal function generates pseudo-random numbers from the normal distribution. The loc and scale arguments set the mean and standard deviation of the distribution, and the size argument determines how many random numbers from this distribution will be returned.

- **plt.hist(randoms, bins=np.arange(0, 1, 0.05))* - For plotting histograms.

- **np.random.seed(20000229)* - To set a random seed with NumPy.

**Exercises:**

**Generating random numbers**

You've used .sample() to generate pseudo-random numbers from a set of values in a DataFrame. A related task is to generate random numbers that follow a statistical distribution, like the uniform distribution or the normal distribution.

Each random number generation function has distribution-specific arguments and an argument for specifying the number of random numbers to generate.

matplotlib.pyplot is loaded as plt, and numpy is loaded as np.

Instructions:

-Generate 5000 numbers from a uniform distribution, setting the parameters low to -3 and high to 3.

-Generate 5000 numbers from a normal distribution, setting the parameters loc to 5 and scale to 2.

    # Generate random numbers from a Uniform(-3, 3)
    uniforms = np.random.uniform(low=-3, high=3, size=5000)

    # Generate random numbers from a Normal(5, 2)
    normals = np.random.normal(loc=5, scale=2, size=5000)

    # Print normals
    print(normals)
  
-Plot a histogram of uniforms with bins of width of 0.25 from -3 to 3 using plt.hist().

    # Generate random numbers from a Uniform(-3, 3)
    uniforms = np.random.uniform(low=-3, high=3, size=5000)

    # Plot a histogram of uniform values, binwidth 0.25
    plt.hist(uniforms, bins=np.arange(-3, 3.25, 0.25))
    plt.show()

![Image120](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/455412b7-1f2c-4f8c-8974-7f47f7e35c5d)

-Plot a histogram of normals with bins of width of 0.5 from -2 to 13 using plt.hist().

    # Generate random numbers from a Normal(5, 2)
    normals = np.random.normal(loc=5, scale=2, size=5000)

    # Plot a histogram of normal values, binwidth 0.5
    plt.hist(normals, bins=np.arange(-2, 13.5, 0.5))
    plt.show()

![Image121](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/96b70a7a-3ad0-4a2d-8793-2ebccbec9f0c)
