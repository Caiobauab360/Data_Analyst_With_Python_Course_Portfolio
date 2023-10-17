# Hypothesis Testing in Python

**Course Description**

Hypothesis testing lets you answer questions about your datasets in a statistically rigorous way. In this course, you'll grow your Python analytical skills as you learn how and when to use common tests like t-tests, proportion tests, and chi-square tests. Working with real-world data, including Stack Overflow user feedback and supply-chain data for medical supply shipments, you'll gain a deep understanding of how these tests work and the key assumptions that underpin them. You'll also discover how non-parametric tests can be used to go beyond the limitations of traditional hypothesis tests.

# Introduction to Hypothesis Testing

**Description:**

How does hypothesis testing work and what problems can it solve? To find out, you’ll walk through the workflow for a one sample proportion test. In doing so, you'll encounter important concepts like z-scores, p-values, and false negative and false positive errors.

# Hypothesis tests and z-scores

**Personal notes:**

One of the uses of hypothesis tests is to determine whether a sample statistic is close to or far from an expected value.

A/B Testing - Used to test different advertising scenarios to see which one drove sales more.

We can start by examining the average annual compensation from the sample survey data:

- mean_comp_samp = stack_overflow["converted_comp"].mean() - The annual compensation in the example is stored in the converted_comp column. The result is the sample mean.

The sample mean is a type of point estimate, also known as a summary statistic.

To find out if the sample mean is significantly different from the hypothetical value of $110,000 in the example, we need to generate a bootstrap distribution of sample means:

- #First step: Resample

- stack_overflow.sample(frac=1, replace=True)["converted_comp"] - Performing resampling of the dataset.

- #Second step: Calculate the sample mean

- np.mean(stack_overflow.sample(frac=1, replace=True)["converted_comp"]) - Sample mean of the resampling.

- #Third step: Repeat steps 1 and 2 several times:

- so_boot_distn = [] 
- for i in range(5000):
	- so_boot_distn.append(
		- np.mean(
			- stack_overflow.sample(frac=1, replace=True)["converted_comp"]
		- )
	- )

Finally, visualize it with plt.hist(so_boot_distn, bins=50).

Remember that the standard deviation of the sample statistics in the bootstrap distribution estimates the standard error.

- std_error = np.std(so_boot_distn, ddof=1)

Z-scores

As variables have arbitrary units and ranges, before testing our hypothesis, we need to standardize the values. One common way to standardize values is to subtract the mean and divide by the standard deviation. For hypothesis testing, we use a variation where we take the sample statistic, subtract the hypothetical parameter value, and divide by the standard error. The result is called a z-score.

- z_score = (mean_comp_samp - mean_comp_hyp) / std_error

The standard normal (z) distribution is a normal distribution with a mean of zero and a standard deviation of one. It's often referred to as the z-distribution, and z-scores are related to this distribution.

**Exercises:**

**Calculating the sample mean**

The late_shipments dataset contains supply chain data on the delivery of medical supplies. Each row represents one delivery of a part. The late columns denotes whether or not the part was delivered late. A value of "Yes" means that the part was delivered late, and a value of "No" means the part was delivered on time.

You'll begin your analysis by calculating a point estimate (or sample statistic), namely the proportion of late shipments.

In pandas, a value's proportion in a categorical DataFrame column can be quickly calculated using the syntax:

prop = (df['col'] == val).mean()
late_shipments is available, and pandas is loaded as pd.

Instructions:

-Print the late_shipments dataset.

-Calculate the proportion of late shipments in the sample; that is, the mean cases where the late column is "Yes".

		# Print the late_shipments dataset
		print(late_shipments)

		# Calculate the proportion of late shipments
		late_prop_samp = (late_shipments['late'] == "Yes").mean()

		# Print the results
		print(late_prop_samp)

**Calculating a z-score**

Since variables have arbitrary ranges and units, we need to standardize them. For example, a hypothesis test that gave different answers if the variables were in Euros instead of US dollars would be of little value. Standardization avoids that.

One standardized value of interest in a hypothesis test is called a z-score. To calculate it, you need three numbers: the sample statistic (point estimate), the hypothesized statistic, and the standard error of the statistic (estimated from the bootstrap distribution).

The sample statistic is available as late_prop_samp.

late_shipments_boot_distn is a bootstrap distribution of the proportion of late shipments, available as a list.

pandas and numpy are loaded with their usual aliases.

Instructions:

-Hypothesize that the proportion of late shipments is 6%.

-Calculate the standard error from the standard deviation of the bootstrap distribution.

-Calculate the z-score.

		# Hypothesize that the proportion is 6%
		late_prop_hyp = 0.06

		# Calculate the standard error
		std_error = np.std(late_shipments_boot_distn, ddof=1)

		# Find z-score of late_prop_samp
		z_score = (late_prop_samp - late_prop_hyp) / std_error

		# Print z_score
		print(z_score)

# p-values

**Personal notes:**

- A hypothesis is a statement about a population parameter. We don't know the true value of that population parameter; we can only make inferences about it from data.

- Hypothesis tests compare two competing hypotheses.

- These two hypotheses are the null hypothesis (H0), representing the existing idea.

- The alternative hypothesis (HA), representing a new idea that challenges the existing one.

*In the example used in the module, the null hypothesis is that the proportion of data scientists who started coding as children follows the research on software developers, at 35%. The alternative hypothesis is that the percentage is greater than 35.

One-tailed and two-tailed tests:

The tails of a distribution are the left and right edges of its PDF (null distribution). Hypothesis tests determine whether sample statistics are in the tails of the null distribution, which is the distribution of the statistic if the null hypothesis were true.

There are three types of tests, and the formulation of the alternative hypothesis determines which type we should use.

1. If we're checking for a difference from a hypothetical value, we look for extreme values in either tail and perform a two-tailed test.

2. If the alternative hypothesis uses language like "less" or "lower," we perform a left-tailed test.

3. If the alternative hypothesis uses words like "greater" or "exceeds," it corresponds to a right-tailed test.

*For the example test, we need a right-tailed test because we're looking for extreme values in the right tail. "The alternative hypothesis is that the percentage is greater than 35."

p-values

- p-values measure the strength of support for the null hypothesis or, in other words, they measure the probability of obtaining a result, assuming the null hypothesis is true.

- High p-values mean that our statistic is producing a result that's likely not in a tail of our null distribution, and chance might be a good explanation for the result.

- Low p-values mean that our statistic is producing a result likely in the tail of our null distribution.

To calculate the p-value, you first need to calculate the z-score:

- prop_child_samp = (stack_overflow["age_first_code_out"] == "child").mean() - Calculate the sample statistic, in this case, the proportion of data scientists who started coding as children.

- prop_child_hyp = 0.35

- std_error = np.std(first_code_boot_distn, ddof=1) - Get the standard error from the standard deviation of the bootstrap distribution.

- z_score = (prop_child_samp - prop_child_hyp) / std_error - The z-score is the difference between proportions divided by the standard error.

Pass the z_score to the standard normal CDF using norm.cdf:

- from scipy.stats import norm

- 1 - norm.cdf(z_score, loc=0, scale=1) - Setting the default values of mean to zero (loc) and standard deviation to one (scale). Since we are performing a right-tailed test, not a left-tailed test, the p-value is calculated by taking one minus the norm.cdf result.

**Exercises:**

**Calculating p-values**

In order to determine whether to choose the null hypothesis or the alternative hypothesis, you need to calculate a p-value from the z-score.

You'll now return to the late shipments dataset and the proportion of late shipments.

The null hypothesis, 
, is that the proportion of late shipments is six percent.

The alternative hypothesis, 
, is that the proportion of late shipments is greater than six percent.

The observed sample statistic, late_prop_samp, the hypothesized value, late_prop_hyp (6%), and the bootstrap standard error, std_error are available. norm from scipy.stats has also been loaded without an alias.

Instructions:

-Calculate the z-score of late_prop_samp.

-Calculate the p-value for the z-score, using a right-tailed test.

		# Calculate the z-score of late_prop_samp
		z_score = (late_prop_samp - late_prop_hyp) / std_error

		# Calculate the p-value
		p_value = 1 - norm.cdf(z_score, loc=0, scale=1)
                 
		# Print the p-value
		print(p_value) 

# Statistical significance

**Personal notes:**

The cutoff point is known as the significance level and is denoted as alpha (α). The appropriate significance level depends on the dataset and the field of study.

- Common values for alpha: 0.2, 0.1, 0.05, and 0.01.

- The significance level provides a decision-making process for which hypothesis to support.

- If the p-value is less than or equal to alpha, we reject the null hypothesis. Otherwise, we fail to reject it.

- It's important to decide what an appropriate significance level should be before conducting our test. Otherwise, there is a temptation to choose a significance level that allows us to select the hypothesis we prefer.

Calculating the p-value

First, we start by setting the significance level, in this case, 0.05.

- alpha = 0.05

Next, we calculate the sample mean and assign the hypothetical mean:

- prop_child_samp = (stack_overflow["age_first_code_cut"] == "child").mean()

- prop_child_hyp = 0.35

Then, we calculate the z-score using the sample mean, hypothetical mean, and standard error, and use the standard normal CDF to get the p-value:

- z_score = (prop_child_samp - prop_child_hyp) / std error

- p_value = 1 - norm.cdf(z_score, loc=0, scale=1)

In this case, the p-value is approximately 3.14714795... which is less than or equal to 0.05, so we reject the null hypothesis.

To get a sense of potential values for the population parameter, it's common to choose a confidence interval level of 1 minus the significance level.

- For a significance level of 0.05, we would use a 95% confidence interval.

- import numpy as np

- lower = np.quantile(first_code_boot_distn, 0.025)

- upper = np.quantile(first_code_boot_distn, 0.975) - To calculate it using the quantile method.

The interval provides a range of plausible values for the proportion of the data scientist population who started coding as children.

For hypothesis testing, there are two ways to get it right and two types of errors. If we support the alternative hypothesis when the null hypothesis was correct, we make a false positive error (type 1 errors). If we support the null hypothesis when the alternative hypothesis was correct, we make a false negative error (type 2 errors).

In the case of data scientists coding as children, if we had a p-value less than or equal to the significance level and rejected the null hypothesis, we might have made a false positive error (type 1). Although we believed that data scientists started coding as children at a higher rate, it may not be true in the entire population. On the other hand, if the p-value is greater than the significance level, and we fail to reject the null hypothesis, we might have made a false negative error (type 2).

**Exercises:**

**Calculating a confidence interval**

If you give a single estimate of a sample statistic, you are bound to be wrong by some amount. For example, the hypothesized proportion of late shipments was 6%. Even if evidence suggests the null hypothesis that the proportion of late shipments is equal to this, for any new sample of shipments, the proportion is likely to be a little different due to sampling variability. Consequently, it's a good idea to state a confidence interval. That is, you say, "we are 95% 'confident' that the proportion of late shipments is between A and B" (for some value of A and B).

Sampling in Python demonstrated two methods for calculating confidence intervals. Here, you'll use quantiles of the bootstrap distribution to calculate the confidence interval.

late_prop_samp and late_shipments_boot_distn are available; pandas and numpy are loaded with their usual aliases.

Instructions:

-Calculate a 95% confidence interval from late_shipments_boot_distn using the quantile method, labeling the lower and upper intervals lower and upper.

		# Calculate 95% confidence interval using quantile method
		lower = np.quantile(late_shipments_boot_distn, 0.025)
		upper = np.quantile(late_shipments_boot_distn, 0.975)

		# Print the confidence interval
		print((lower, upper))