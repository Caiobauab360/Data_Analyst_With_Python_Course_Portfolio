# Non-Parametric Tests

**Description:**

Finally, it’s time to learn about the assumptions made by parametric hypothesis tests, and see how non-parametric tests can be used when those assumptions aren't met.

# Assumptions in hypothesis testing

**Personal notes:**

Every hypothesis test we've seen so far makes assumptions about the data. It's only when these assumptions are met that it's appropriate to use that hypothesis test. Whether you're using a single sample or multiple samples, every hypothesis test assumes that each sample is drawn randomly from its population. If we don't have a random sample, it won't be representative of the population. To check this assumption, we need to know where our data came from. There are no statistical or coding tests we can perform to verify this.

Tests also assume that each observation is independent. There are some special cases like paired t-tests where dependencies between two samples are allowed, but they change the calculations, so we need to understand where these dependencies occur. As we saw with the paired t-test, not accounting for dependencies results in a higher chance of both false negatives and false positives. Not accounting for dependencies is a problem that's difficult to diagnose during analysis. Ideally, it needs to be discussed before data collection.

Hypothesis tests also assume that our sample is large enough for the central limit theorem to apply, and the sample distribution can be considered normally distributed. Smaller samples incur more uncertainty, which can mean that the central limit theorem doesn't apply, and the sample distribution may not be normally distributed. Increased uncertainty in a small sample means that we get wider confidence intervals on the parameter we're trying to estimate. If the central limit theorem doesn't apply, the calculations on the sample and any conclusions drawn from them may be nonsensical, which increases the chance of both false negatives and false positives. The size our sample needs to be to be "large enough" depends on the test.

Large sample size: t-test

- For a one-sample t-test, a popular heuristic is that we need at least thirty observations in our sample.

- For two-sample or ANOVA cases, we need thirty observations from each group.

- For paired samples, we need thirty pairs of observations.

The key is that the null distribution looks normal. This generally happens around 30, and that's the reason for this somewhat arbitrary cutoff.

Large sample size: proportion tests

For one-sample proportion tests, the sample is considered large enough if it contains at least ten successes and ten failures. Note that if the probability of success is close to zero or close to one, we need a larger sample.

For two-sample tests, we require ten successes and ten failures from each sample.

Large sample size: chi-square tests

The chi-square test is a bit more tolerant and only requires five successes and five failures in each group, rather than ten.

Another check we can perform is to compute a bootstrap distribution and visualize it with a histogram. If we don't see a normal bell-shaped curve, one of the assumptions wasn't met. In that case, we should revisit the data collection and see if any of the three assumptions of randomness, independence, and sample size didn't hold up.

**Exercises:**

**Testing sample size**

In order to conduct a hypothesis test and be sure that the result is fair, a sample must meet three requirements: it is a random sample of the population, the observations are independent, and there are enough observations. Of these, only the last condition is easily testable with code.

The minimum sample size depends on the type of hypothesis tests you want to perform. You'll now test some scenarios on the late_shipments dataset.

Note that the .all() method from pandas can be used to check if all elements are true. For example, given a DataFrame df with numeric entries, you check to see if all its elements are less than 5, using (df < 5).all().

late_shipments is available, and pandas is loaded as pd.

Instructions:

-Get the count of each value in the freight_cost_group column of late_shipments.

-Insert a suitable number to inspect whether the counts are "big enough" for a two sample t-test.

		# Count the freight_cost_group values
		counts = late_shipments["freight_cost_group"].value_counts()

		# Print the result
		print(counts)

		# Inspect whether the counts are big enough
		print((counts >= 30).all())

-Get the count of each value in the late column of late_shipments.

-Insert a suitable number to inspect whether the counts are "big enough" for a one sample proportion test.

		# Count the late values
		counts = late_shipments["late"].value_counts()

		# Print the result
		print(counts)

		# Inspect whether the counts are big enough
		print((counts >= 10).all())

-Get the count of each value in the freight_cost_group column of late_shipments grouped by vendor_inco_term.

-Insert a suitable number to inspect whether the counts are "big enough" for a chi-square independence test.

		# Count the values of freight_cost_group grouped by vendor_inco_term
		counts = late_shipments.groupby("vendor_inco_term")["freight_cost_group"].value_counts()

		# Print the result
		print(counts)

		# Inspect whether the counts are big enough
		print((counts >= 5 ).all())

-Get the count of each value in the shipment_mode column of late_shipments.

-Insert a suitable number to inspect whether the counts are "big enough" for an ANOVA test.

		# Count the shipment_mode values
		counts = late_shipments["shipment_mode"].value_counts()

		# Print the result
		print(counts)

		# Inspect whether the counts are big enough
		print((counts >= 30).all())

# Non-parametric tests

**Personal notes:**

The tests we've seen so far are known as parametric tests. Tests like the z-test, t-test, and ANOVA are all based on the assumption that the population is normally distributed. Parametric tests also require sample sizes that are large enough for the central limit theorem to apply.

Results with pingouin.ttest()

Let's attempt to perform a paired t-test on this small sample. Remember that we need at least 30 pairs to feel confident using the t-test, and the sample in the example from the lesson contains only five. We use the ttest method to perform the one-tailed paired t-test:

- alpha = 0.01

- import pingouin

- pingouin.ttest(x=repub_votes_potus_08_12_small["repub_percent_08"],
				- y=repub_votes_potus_08_12_small["repub_percent_012"],
				- paired=True,
				- alternative="less")

The small p-value indicates that we should reject the null hypothesis, leading us to suspect that the 2008 election had a lower percentage of Republican votes than the 2012 election.

Non-parametric tests

In situations where you are not sure about these assumptions or are certain that the assumptions are not met, you can use non-parametric tests. They don't make the assumptions of normal distribution or the sample size conditions we saw in the video.

There are many different ways to perform tests without these parametric assumptions. In this chapter, we will focus on those related to ranking. We can access the so-called ranks of the elements in x using the rankdata method from scipy.stats:

- from scipy.stats import rankdata

- x = [1, 15, 3, 10, 6]

- rankdata(x)

Now, let's use a non-parametric test to see what kind of result it provides. Remember that non-parametric tests work better than the parametric alternative in situations where the sample size is small or the data cannot be considered normally distributed.

Wilcoxon signed-rank test 

(Step 1)

The Wilcoxon signed-rank test requires us to calculate the absolute differences in the paired data and then rank them. First, we take the differences in the paired values.

- repub_votes_small["diff"] = repub_votes_small["repub_percent_08"] - repub_votes_small["repub_percent_12"]

(Step 2)

Next, we take the absolute value of the differences using the .abs method and put them in the abs_diff column:

- repub_votes_small["abs_diff"] = repub_votes_small["diff"].abs()

(Step 3)

Then, we rank these absolute differences using the rankdata method:

- repub_votes_small["rank_abs_diff"] = rankdata(repub_votes_small["abs_diff"])

(Step 4)

The last part involves calculating a test statistic called W, which uses the signs from the diff column to split the ranks into two groups: one for rows with negative differences and another for positive differences. T-minus is defined as the sum of the ranks with negative differences, and T-plus is the sum of the ranks with positive differences.

- T_minus = [1 + 4 + 5 + 2 + 3]

- T_plus = 0

- W = np.min([T_minus, T_plus]) - The test statistic W is the minimum of T_minus and T_plus, which in this case is zero.

Implementation with pingouin.wilcoxon()

We can calculate W and its corresponding p-value using a pingouin method instead of manual calculation. The wilcoxon() method in pingouin takes many similar arguments to the ttest method, except it doesn't have a paired argument.

- alpha = 0.01

- pingouin.wilcoxon(x=repub_votes_potus_08_12_small["repub_percent_08"],
				- y=repub_votes_potus_08_12_small["repub_percent_012"],
				- alternative="less")

The function returns a W value of zero - the same as our manual calculation. This corresponds to a p-value of about three percent, which is more than ten times larger than the p-value from the t-test, so we should feel more confident about this result due to the small sample size.

**Exercises:**

**Wilcoxon signed-rank test**

You'll explore the difference between the proportion of county-level votes for the Democratic candidate in 2012 and 2016 to identify if the difference is significant.

sample_dem_data is available, and has columns dem_percent_12 and dem_percent_16 in addition to state and county names. The following packages have also been loaded: pingouin and pandas as pd.

Instructions:

-Conduct a paired t-test on the percentage columns using an appropriate alternative hypothesis.

		# Conduct a paired t-test on dem_percent_12 and dem_percent_16
		paired_test_results = pingouin.ttest(x=sample_dem_data["dem_percent_12"], 
                                      		y=sample_dem_data["dem_percent_16"],
                                      		paired=True,
                                      		alternative="two-sided")

		# Print paired t-test results
		print(paired_test_results)

-Conduct a Wilcoxon-signed rank test on the same columns.

		# Conduct a Wilcoxon test on dem_percent_12 and dem_percent_16
		wilcoxon_test_results = pingouin.wilcoxon(x=sample_dem_data["dem_percent_12"],
						y=sample_dem_data["dem_percent_16"],
			 		alternative="two-sided") 



		# Print Wilcoxon test results
		print(wilcoxon_test_results)

# Non-parametric ANOVA and unpaired t-tests

**Personal notes:**

We can avoid assumptions about normally distributed data by running hypothesis tests on the ranks of a numerical input. The Wilcoxon-Mann-Whitney test is like a t-test on ranked data. This test is similar to the Wilcoxon signed-rank test in the previous lesson but works with unpaired data.

Wilcoxon-Mann-Whitney test setup

We start by focusing on just these two columns in a new dataframe called age_vs_comp.

- age_vs_comp = stack_overflow[["converted_comp", "age_first_code_cut"]]

To perform a Wilcoxon-Mann-Whitney test with pingouin, we first need to convert our data from long format to wide format. This is done with the pivot method of pandas, which, unlike pivot_table, doesn't aggregate; it instead returns the raw values for each group of rows.

- age_vs_comp_wide = age_vs_comp.pivot(columns="age_first_code_cut", values="converted_comp")

We can run a Wilcoxon-Mann-Whitney test using pingouin's mwu method. It takes arguments x and y corresponding to the two columns of numbers you want to compare, in this case, child and adult.

- import pingouin

- pingouin.mwu(x=age_vs_comp_wide["child"],
				- y=age_vs_comp_wide["adult"],
				- alternative="greater")

Kruskal-Wallis test

Just as ANOVA extends t-tests to more than two groups, the Kruskal-Wallis test extends the Wilcoxon-Mann-Whitney test to more than two groups, making it a non-parametric version of ANOVA.
We use pingouin's kruskal method to perform a Kruskal-Wallis test to investigate if there's a difference in converted_comp among the job satisfaction groups. We pass in stack_overflow as the data, the dependent variable dv as converted_comp, and compare between the job_sat groups.

- alpha=0.01

- pingouin.kruskal(data=stack_overflow, dv="converted_comp", between="job_sat")

**Exercises:**

**Wilcoxon-Mann-Whitney**

Another class of non-parametric hypothesis tests are called rank sum tests. Ranks are the positions of numeric values from smallest to largest. Think of them as positions in running events: whoever has the fastest (smallest) time is rank 1, second fastest is rank 2, and so on.

By calculating on the ranks of data instead of the actual values, you can avoid making assumptions about the distribution of the test statistic. It's more robust in the same way that a median is more robust than a mean.

One common rank-based test is the Wilcoxon-Mann-Whitney test, which is like a non-parametric t-test.

late_shipments is available, and the following packages have been loaded: pingouin and pandas as pd.

Instructions:

-Select weight_kilograms and late from late_shipments, assigning the name weight_vs_late.

-Convert weight_vs_late from long-to-wide format, setting columns to 'late'.

-Run a Wilcoxon-Mann-Whitney test for a difference in weight_kilograms when the shipment was late and on-time.


		# Select the weight_kilograms and late columns
		weight_vs_late = late_shipments[["weight_kilograms", "late"]]

		# Convert weight_vs_late into wide format
		weight_vs_late_wide = weight_vs_late.pivot(columns="late", values="weight_kilograms")

		# Run a two-sided Wilcoxon-Mann-Whitney test on weight_kilograms vs. late
		wmw_test = pingouin.mwu(x=weight_vs_late_wide["No"],
                        		y=weight_vs_late_wide["Yes"],
                        		alternative="two-sided")

		# Print the test results
		print(wmw_test)

**Kruskal-Wallis**

Recall that the Kruskal-Wallis test is a non-parametric version of an ANOVA test, comparing the means across multiple groups.

late_shipments is available, and the following packages have been loaded: pingouin and pandas as pd.

Instructions:

-Run a Kruskal-Wallis test on weight_kilograms between the different shipment modes in late_shipments.

		# Run a Kruskal-Wallis test on weight_kilograms vs. shipment_mode
		kw_test = pingouin.kruskal(data=late_shipments,dv="weight_kilograms", between="vendor_inco_term")

		# Print the results
		print(kw_test)