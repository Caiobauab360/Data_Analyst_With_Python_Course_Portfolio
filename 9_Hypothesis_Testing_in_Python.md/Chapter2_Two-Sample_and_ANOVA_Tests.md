# Two-Sample and ANOVA Tests

**Description:**

In this chapter, you’ll learn how to test for differences in means between two groups using t-tests and extend this to more than two groups using ANOVA and pairwise t-tests.

# Performing t-tests

**Personal notes:**

Two-sample problems - We will look at a problem of comparing sample statistics between groups on a single variable.

In the dataset used in the class, "converted_comp" is a numerical variable representing annual compensation. "age_first_code_cut" is a categorical variable with two levels: "child" and "adult," describing when the user started coding. The null hypothesis (H0) is that the population mean for the two groups is the same, and the alternative hypothesis (HA) is that the population mean for users who started coding as children is greater than for users who started coding as adults.

We can write these hypotheses using equations:

*µ represents an unknown population mean, and we use subscripts to denote which group's population mean we're referring to.

- H0: µchild = µadult;

- HA: µchild > µadult

An alternative way to write the equations is to compare the differences in population means to zero:

- H0: µchild - µadult = 0

- HA: µchild - µadult > 0

In this case, zero corresponds to our hypothetical value for the mean difference.

To calculate summary statistics for each group:

- stack_overflow.groupby("age_first_code_cut")["converted_comp"].mean() - We start with the sample by grouping it by the categorical variable and then calculate the mean on the numerical variable.

Test statistics

Although we don't know the population mean, we estimate it using the sample mean.

- x̄ (x-bar) is used to denote a sample mean.

We then use subscripts to denote which group a sample mean corresponds to.

- x̄child - sample mean for the group that started coding as children;

- x̄adult - sample mean for the group that started coding as adults;

The difference between these two sample means is the test statistic for the hypothesis test:

- x̄child - x̄adult - a test statistic.

*Z-scores are a type of standardized test statistic.

In the case of two samples, the test statistic, denoted as t, is calculated by taking the difference between the sample statistics for the two groups, divided by:

- t = (x̄child - x̄adult) - (x̄child - x̄adult)  / SE(x̄child - x̄adult)

To calculate the standard error (SE), which is needed for the denominator of the test statistic equation, bootstrapping is often a good option. But you can also calculate the standard deviation for the numerical variable in each group in the sample and the number of observations in each group. Then, plug these values into the equation and calculate the result.

If we assume that the null hypothesis is true, there's a simplification we can make. The null hypothesis assumes that the population means are equal, and their difference is zero, so the population term in the numerator disappears:

- H0: µchild - µadult = 0 --> t = (x̄child - x̄adult) - (x̄child - x̄adult)  / SE(x̄child - x̄adult)

You need to calculate the mean, standard deviation, and number of observations for each group to fill in the formula for t:

- xbar = stack_overflow.groupby("age_first_code_cut")["converted_comp"].mean() - Mean;

- s = stack_overflow.groupby("age_first_code_cut")["converted_comp"].std() - Standard deviation;

- n = stack_overflow.groupby("age_first_code_cut")["converted_comp"].count() - Number of observations;

Calculating the test statistic

Assigning the values to six different variables, the numerator is a subtraction of sample means, and the denominator is like a weighted hypotenuse.

- numerator = xbar_child - xbar_adult

- denominator = np.sqrt(s_child ** 2/ n_child + s_adult ** 2 / n_adult) 

- t_stat = numerator / denominator 

The result will be the t-value.

**Exercises:**

**Two sample mean test statistic**

The hypothesis test for determining if there is a difference between the means of two populations uses a different type of test statistic to the z-scores you saw in Chapter 1. It's called "t", and it can be calculated from three values from each sample using this equation.

While trying to determine why some shipments are late, you may wonder if the weight of the shipments that were on time is less than the weight of the shipments that were late. The late_shipments dataset has been split into a "yes" group, where late == "Yes" and a "no" group where late == "No". The weight of the shipment is given in the weight_kilograms variable.

The sample means for the two groups are available as xbar_no and xbar_yes. The sample standard deviations are s_no and s_yes. The sample sizes are n_no and n_yes. numpy is also loaded as np.

Instructions:

-Calculate the numerator of the t test statistic.

-Calculate the denominator of the t test statistic.

-Use those two numbers to calculate the t test statistic.

        # Calculate the numerator of the test statistic
        numerator = xbar_no - xbar_yes
        # Calculate the denominator of the test statistic
        denominator = np.sqrt(s_no**2/n_no+s_yes**2/n_yes)

        # Calculate the test statistic
        t_stat = numerator/denominator

        # Print the test statistic

        print(t_stat)

# Calculating p-values from t-statistics

**Personal notes:**

The t-test statistic follows a t-distribution. T-distributions have a parameter called degrees of freedom (df). T-distributions for small degrees of freedom have fatter tails compared to the normal distribution, but are otherwise similar. As we increase the degrees of freedom, the t-distribution approaches the normal distribution. A normal distribution is a t-distribution with infinitely many degrees of freedom. Degrees of freedom are defined as the maximum number of logically independent values in the sample data.

Calculating degrees of freedom - Suppose our dataset has 5 independent observations, and four values are 2, 6, 8, and 5. We also know that the sample mean is 5. With this knowledge, the fifth value is no longer independent; it must be 4. Even if all five observations in the sample were independent, because we know an additional fact about the sample - that it has a mean of 5 - we only have 4 degrees of freedom.

* The example from the module continues to be used, and we're working with a right-tailed test.

First, you need to decide the significance level:

- α = 0.1

    if p <= α then reject H0. - We reject the null hypothesis in favor of the alternative if the p-value is less than or equal to 0.1.

Now, you are calculating means instead of proportions, and the z-score is replaced by a t-test statistic.

- numerator = xbar_child - xbar_adult

- denominator = np.sqrt(s_child ** 2/ n_child + s_adult ** 2 / n_adult)

- t_stat = numerator / denominator

The calculation also requires degrees of freedom, which is the number of observations in both groups minus 2:

- degrees_of_freedom = n_child + n_adult - 2

To calculate the p-value, you need to transform the test statistic using the t-distribution's CDF instead of the normal distribution's CDF.

- from scipy.stats import t

- 1 - t.cdf(t_stat, df=degrees_of_freedom)

The resulting p-value is less than the 0.1 significance level, so we should reject the null hypothesis in favor of the alternative hypothesis that Stack Overflow data scientists who started coding as children earn more.

**Exercises:**

**From t to p**

Previously, you calculated the test statistic for the two-sample problem of whether the mean weight of shipments is smaller for shipments that weren't late (late == "No") compared to shipments that were late (late == "Yes"). In order to make decisions about it, you need to transform the test statistic with a cumulative distribution function to get a p-value.

Recall the hypotheses:

H0: The mean weight of shipments that weren't late is the same as the mean weight of shipments that were late.

HA: The mean weight of shipments that weren't late is less than the mean weight of shipments that were late.

The test statistic, t_stat, is available, as are the samples sizes for each group, n_no and n_yes. Use a significance level of alpha = 0.05.

t has also been imported from scipy.stats.

Instructions:

-Calculate the degrees of freedom for the test.

-Compute the p-value using the test statistic, t_stat.

        # Calculate the degrees of freedom
        degrees_of_freedom = n_no + n_yes - 2

        # Calculate the p-value from the test stat
        p_value = t.cdf(t_stat, df=degrees_of_freedom)
        # Print the p_value
        print(p_value)

# Paired t-tests

**Personal notes:**

In this lesson, the example being used is a dataset with the percentage of votes for the Republican candidate in the United States elections for the years 2008 and 2012. The question is whether the percentage of Republican votes was lower in 2008 compared to 2012.

The null hypothesis is that our guess is wrong, and the population parameters are the same in each year group. The alternative hypothesis is that the parameter in 2008 was less than in 2012.

- H0: µ2008 - µ2012 = 0

- HA: µ2008 - µ2012 < 0

Let's set a significance level of 0.05:

- α = 0.05

One characteristic of this dataset is that the 2008 votes and the 2012 votes are paired, meaning they are not independent as they both refer to the same county. This means that voting patterns may occur due to local demographics and politics, and we want to capture this pairing in our model.

From two samples to one

For paired analyses, instead of considering the two variables separately, we can consider a single variable of the difference.

- sample_data = repub_votes_potus_08_12

- sample_data["diff"] = sample_data["repub_percent_08"] - sample_data["repub_percent_12"]

- sample_data["diff"].hist(bins=20)

Visualizing the difference histogram, most values are between -10 and 10, with at least one outlier.

- xbar_diff = sample_data["diff"].mean() - The sample mean x-bar is calculated from the difference above, resulting in a sample mean of -2.87 in the example.

We can reformulate the hypotheses in terms of a single population mean, µdiff, being equal to or less than zero.

- H0: µdiff = 0

- HA: µdiff < 0

Calculating the p-value

To calculate the test statistic, we need the number of rows in the dataset and the standard deviation of the differences:

- n_diff = len(sample_data)

- s_diff = sample_data["diff"].std()

We've already calculated x-bar-diff, which is the mean of the differences. Now we have everything we need to plug into the equation to calculate t.

- t_stat = (xbar_diff-0) / np.sqrt(s_diff**2/n_diff)

The degrees of freedom are one less than n_diff:

- degrees_of_freedom = n_diff - 1

Finally, we transform t using the t-distribution's CDF:

- from scipy.stats import t

- p_value = t.cdf(t_stats, df=n_diff-1)

The resulting p-value is very low, which means we reject the null hypothesis in favor of the alternative hypothesis that Republican candidates received a lower percentage of votes in 2008 compared to 2012.

Testing differences between two means using ttest()

There is a simpler way to perform all these calculations. The pingouin package provides various methods for hypothesis testing and returns results as a pandas dataframe.

One method in pingouin is ttest, which works with array-like objects, so the first argument is the difference series. For a one-sample test like this, y specifies the hypothetical difference value from the null hypothesis, which is zero. The type of alternative hypothesis can be specified as two-sided, less, or greater, corresponding to two-tailed, left-tailed, and right-tailed tests, respectively.

- import pingouin

- pingouin.ttest(x=sample_data["diff"],
                y=0,
                alternative="less")

Returns the test statistic value, degrees of freedom, alternative direction, and p-value.

ttest() with paired=true

There is a variation of ttest for paired data that requires even less work. Instead of calculating the difference between the two paired variables, you can directly pass both of them to ttest as x and y and set paired=True.

- pingouin.ttest(x=sample_data["repub_percent_08"],
                y=sample_data["repub_percent_12"],
                paired=True,
                alternative="less")

*Performing an unpaired t-test when your data is paired increases the chances of false negatives.

**Exercises:**

**Visualizing the difference**

Before you start running hypothesis tests, it's a great idea to perform some exploratory data analysis; that is, calculating summary statistics and visualizing distributions.

Here, you'll look at the proportion of county-level votes for the Democratic candidate in 2012 and 2016, sample_dem_data. Since the counties are the same in both years, these samples are paired. The columns containing the samples are dem_percent_12 and dem_percent_16.

dem_votes_potus_12_16 is available as sample_dem_data. pandas and matplotlib.pyplot are loaded with their usual aliases.

Instructions:

-Create a new diff column containing the percentage of votes for the democratic candidate in 2012 minus the percentage of votes for the democratic candidate in 2016.

-Calculate the mean of the diff column as xbar_diff

-Calculate the standard deviation of the diff column as s_diff

-Plot a histogram of the diff column with 20 bins.

        # Calculate the differences from 2012 to 2016
        sample_dem_data['diff'] = sample_dem_data['dem_percent_12'] - sample_dem_data['dem_percent_16']

        # Find the mean of the diff column
xbar_diff = sample_dem_data['diff'].mean()

        # Find the standard deviation of the diff column
        s_diff = sample_dem_data['diff'].std()

        # Plot a histogram of diff with 20 bins
        sample_dem_data['diff'].hist(bins=20)
        plt.show()

![Image130](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/7a91db28-1f93-47d8-a154-473562225074)

**Using ttest()**

Manually calculating test statistics and transforming them with a CDF to get a p-value is a lot of effort to compare two sample means. The comparison of two sample means is called a t-test, and the pingouin Python package has a .ttest() method to accomplish it. This method provides some flexibility in how you perform the test.

As in the previous exercise, you'll explore the difference between the proportion of county-level votes for the Democratic candidate in 2012 and 2016 to identify if the difference is significant. The hypotheses are as follows:

H0: The proportion of democratic votes in 2012 and 2016 were the same. 
HA: The proportion of democratic votes in 2012 and 2016 were different.

sample_dem_data is available and has the columns diff, dem_percent_12, and dem_percent_16 in addition to the state and county names. pingouin and has been loaded along with pandas as pd.

Instructions:

-Conduct a t-test on the sample differences (the diff column of sample_dem_data), using an appropriate alternative hypothesis chosen from "two-sided", "less", and "greater".

        # Conduct a t-test on diff
        test_results = pingouin.ttest(x=sample_dem_data["diff"], y=0, alternative="two-sided")
                              
        # Print the test results
        print(test_results)

-Conduct a paired test on the democratic votes in 2012 and 2016 (the dem_percent_12 and dem_percent_16 columns of sample_dem_data), using an appropriate alternative hypothesis.

        # Conduct a t-test on diff
        test_results = pingouin.ttest(x=sample_dem_data['diff'], 
                                    y=0, 
                                    alternative="two-sided")

        # Conduct a paired t-test on dem_percent_12 and dem_percent_16
        paired_test_results = pingouin.ttest(x=sample_dem_data["dem_percent_12"],
                                            y=sample_dem_data["dem_percent_16"],
                                            paired=True,
                                            alternative="two-sided")
                     
        # Print the paired test results
        print(paired_test_results)

# ANOVA tests

**Personal notes:**

Visualizing multiple distributions

Suppose we want to determine if the average annual compensation is different for each of the job satisfaction levels. The first thing to do is visualize the distributions with box plots.

- import seaborn as sns

- import matplotlib.pyplot as plt

- sns.boxplot(x="converted_comp",
            - y="job_sat",
            - data=stack_overflow)

ANOVA tests determine whether there are differences between groups. We start by defining our significance level as 0.2. This value is higher than in many situations but will help us understand the implications of comparing different numbers of groups later.

Using the pingouin anova method to compare values in multiple groups:

- alpha = 0.2

- pingouin.anova(data=stack_overflow, 
                - dv="converted_comp", 
                - between="job_sat")

The p-value is stored in the p-unc column, and we can see that it is less than alpha, which means that at least two of the job satisfaction categories in the example have significant differences in their compensation levels, but this doesn't tell us which two categories.

Pairwise tests

To identify which categories are different, we compare all five job satisfaction categories, testing each pair one at a time. There are ten ways to choose two items from a set of five, so we have ten tests to perform.

To execute all these hypothesis tests at once, we can use pairwise_tests. The first three arguments, data, dv, and between, are the same as for the anova method. The padjust will be discussed shortly.

- pingouin.pairwise_tests(data=stack_overflow,
                        - dv="converted_comp",
                        - between="job_sat",
                        - padjust="none")

The result shows a dataframe where A and B are the two levels being compared in each row. Then we look at the p-unc column of p-values, where three of them are less than our significance level of 0.2.

In this lesson's example, we have five groups, resulting in ten pairs. As the number of groups increases, the number of pairs increases, and the number of hypothesis tests we must perform increases quadratically. The more tests we run, the greater the chance that at least one of them will yield a false positive significant result.

The solution to this is to apply an adjustment to the pairwise test to increase the p-values, reducing the chance of a false positive. A common adjustment is the Bonferroni correction:

- pingouin.pairwise_tests(data=stack_overflow,
                        - dv="converted_comp",
                        - between="job_sat",
                        - padjust="bonf")

Pingouin provides several options for adjusting p-values, with some being more conservative than others. Here's a list of options for padjust:

- "none" - no correction [default];

- "bonf" - one-step Bonferroni correction;

- "sidak" - one-step sidak correction;

- "holm" - step-down method using Bonferroni adjustments;

- "fdr_bh" - Benjamini/Hochberg FDR correction;

- "fdr_by" - Benjamini/Yekutieli FDR correction.

**Exercises:**

**Visualizing many categories**

So far in this chapter, we've only considered the case of differences in a numeric variable between two categories. Of course, many datasets contain more categories. Before you get to conducting tests on many categories, it's often helpful to perform exploratory data analysis (EDA), calculating summary statistics for each group and visualizing the distributions of the numeric variable for each category using box plots.

Here, we'll return to the late shipments data, and how the price of each package (pack_price) varies between the three shipment modes (shipment_mode): "Air", "Air Charter", and "Ocean".

late_shipments is available; pandas and matplotlib.pyplot are loaded with their standard aliases, and seaborn is loaded as sns.

Intructions:

-Group late_shipments by shipment_mode and calculate the mean pack_price for each group, storing the result in xbar_pack_by_mode.

-Group late_shipments by shipment_mode and calculate the standard deviation pack_price for each group, storing the result in s_pack_by_mode.

-Create a boxplot from late_shipments with "pack_price" as x and "shipment_mode" as y.

        # Calculate the mean pack_price for each shipment_mode
        xbar_pack_by_mode = late_shipments.groupby("shipment_mode")['pack_price'].mean()

        # Calculate the standard deviation of the pack_price for each shipment_mode
        s_pack_by_mode = late_shipments.groupby("shipment_mode")['pack_price'].std()

        # Boxplot of shipment_mode vs. pack_price
        sns.boxplot(x="pack_price",
                    y="shipment_mode",
                    data=late_shipments)
        plt.show()

![Image131](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/c3ea855d-5858-4646-88d1-a40311bd0a49)

**Conducting an ANOVA test**

The box plots made it look like the distribution of pack price was different for each of the three shipment modes. However, it didn't tell us whether the mean pack price was different in each category. To determine that, we can use an ANOVA test. The null and alternative hypotheses can be written as follows.

: Pack prices for every category of shipment mode are the same.

: Pack prices for some categories of shipment mode are different.

Use a significance level of 0.1.

late_shipments is available and pingouin has been loaded.

Instructions:

-Run an ANOVA on late_shipments investigating 'pack_price' (the dependent variable) between the groups of 'shipment_mode'

        # Run an ANOVA for pack_price across shipment_mode
        anova_results = pingouin.anova(data=late_shipments, 
				        dv="pack_price", 
				        between="shipment_mode")

        # Print anova_results
        print(anova_results)

**Pairwise t-tests**

The ANOVA test didn't tell you which categories of shipment mode had significant differences in pack prices. To pinpoint which categories had differences, you could instead use pairwise t-tests.

late_shipments is available and pingouin has been loaded.

Instructions:

-Perform pairwise t-tests on late_shipments's pack_price variable, grouped by shipment_mode, without doing any p-value adjustment.

        # Perform a pairwise t-test on pack price, grouped by shipment mode
        pairwise_results = pingouin.pairwise_tests(data=late_shipments,
                                                    dv="pack_price",
                                                    between="shipment_mode",
                                                    padjust="none")

        # Print pairwise_results
        print(pairwise_results)

-Modify the pairwise t-tests to use the Bonferroni p-value adjustment.

        # Modify the pairwise t-tests to use Bonferroni p-value adjustment
        pairwise_results = pingouin.pairwise_tests(data=late_shipments, 
                                                dv="pack_price",
                                                between="shipment_mode",
                                                padjust="bonf")

        # Print pairwise_results
        print(pairwise_results)

