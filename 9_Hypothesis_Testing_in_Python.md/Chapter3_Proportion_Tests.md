# Proportion Tests

**Description:**

Now it’s time to test for differences in proportions between two groups using proportion tests. Through hands-on exercises, you’ll extend your proportion tests to more than two groups with chi-square independence tests, and return to the one sample case with chi-square goodness of fit tests.

# One-sample proportion tests

**Personal notes:**

Standardized test statistic for proportions

- p - An unknown population parameter that is a proportion, or population proportion.

- p̂ - The sample proportion; 

- p0 - The hypothetical value for the population proportion.

As in Chapter 1, the standardized test statistic is a z-score. We calculate it by starting with the sample statistic, subtracting its mean, and dividing by its standard error. p̂ minus the mean of p̂ divided by the standard error of p̂.

- z = p̂ - mean(p̂ )/SE(p̂ ) = p̂ - p / SE(p̂ )

Under the null hypothesis, the unknown proportion p is assumed to be the hypothetical population proportion p0. The z-score is now p̂ - p0 divided by the standard error of p̂.

- z = p̂ - p0/SE(p̂)

The example in the lesson returns to the Stack Overflow survey data. Suppose we want to test whether half of the users in the population are under thirty and check for differences. Setting a significance level of 0.01.

- H0: Proportion of Stack Overflow users under thirty = 0.5

- HA: Proportion of Stack Overflow users under thirty != 0.5

- alpha = 0.01

- stack_overflow["age_cat"].value_counts(normalize=True) 

We will obtain the necessary numbers for the z-score. 

- p_hat = (stack_overflow["age_cat"] == "under 30").mean()

- p_0 = 0.50 - According to the null hypothesis. 

- n = len(stack_overflow) 

Calculating the z-score:

- numerator = p_hat - p_0

- denominator = np.sqrt(p_0 * (1 - p_0) / n)

- z_score = numerator / denominator

Calculating the p-value -

For left-tailed alternative hypotheses ("less than"), we transform the z-score into a p-value using norm.cdf:

- p_value = norm.cdf(z_score)

For right-tailed alternative hypotheses ("greater than"), we subtract the result from one:

- p_value = 1 - norm.cdf(z_score)

For two-tailed alternative hypotheses ("not equal"), we check if the test statistic is in either tail, so the p-value is the sum of these two values: one corresponding to the z-score and the other to its negative on the other side of the distribution:

- p_value = norm.cdf(-z_score) + 1 - norm.cdf(z_score)

Since the normal distribution PDF is symmetric, this simplifies to twice the right-tailed p-value because the z-score is positive.

- p_value = 2 * (1 - norm.cdf(z_score))

In the lesson example, the p-value is less than the 0.01 significance level, so we reject the null hypothesis, concluding that the proportion of users under thirty is not equal to 0.5.

**Exercises:**

**Test for single proportions**

In Chapter 1, you calculated a p-value for a test hypothesizing that the proportion of late shipments was greater than 6%. In that chapter, you used a bootstrap distribution to estimate the standard error of the statistic. An alternative is to use an equation for the standard error based on the sample proportion, hypothesized proportion, and sample size.

late_shipments is available. pandas and numpy are available under their usual aliases, and norm is loaded from scipy.st

Instructions:

-Hypothesize that the proportion of late shipments is 6%.

-Calculate the sample proportion of shipments where late equals "Yes".

-Calculate the number of observations in the sample.

-Calculate the numerator and denominator of the z-score.

-Calculate the z-score as the ratio of these numbers

-Transform the z-score into a p-value, remembering that this is a "greater than" alternative hypothesis.

        # Hypothesize that the proportion of late shipments is 6%
        p_0 = 0.06

        # Calculate the sample proportion of late shipments
        p_hat = (late_shipments['late'] == "Yes").mean()

        # Calculate the sample size
        n = len(late_shipments)

        # Calculate the numerator and denominator of the test statistic
        numerator = p_hat - p_0
        denominator = np.sqrt(p_0 * (1 - p_0) / n)

        # Calculate the test statistic
        z_score = numerator / denominator

        # Calculate the p-value from the z-score
        p_value = 1 - norm.cdf(z_score)

        # Print the p-value
        print(p_value)

# Two-sample proportion tests

**Personal notes:**

In the previous lesson, we tested a single proportion against a specific value. Just like means, we can also test differences between proportions in two populations.

Hypotheses in the lesson example: We can assume that the proportion of hobbyists is the same for the less than thirty years category as for the thirty years or more category, which is a two-tailed test.

The null hypothesis is that the difference between the population parameters for each group is zero.

- H0: p >= 30 - p <= 30  = 0

- HA: p >= 30 - p <= 30 != 0

- alpha = 0.05

Calculating the z-score

The sample statistic is the difference in proportions for each category. These are the two p̂ values in the numerator. We subtract the hypothetical population parameter value, and assuming the null hypothesis is true, it's zero. The denominator is the standard error of the sample statistic.

- z = ( p̂ >=30 -  p̂ < 30) - 0 / SE( p̂ >=30 -  p̂ < 30) 

We can again avoid having to generate a bootstrap distribution to calculate the standard error using a standard error equation, which is a slightly more complicated version of the sample case. Note that p̂ is a weighted average of the sample proportions for each category, and it's also known as a pooled estimate of the population proportion.

Getting the numbers for the z-score

To calculate the four missing numbers to find the z-score, we group by age category and calculate the sample proportions using .value_counts() and the row counts using .count():

- p_hats = stack_overflow.groupby("age_cat")["hobbyist"].value_counts(normalize=True)

- n = stack_overflow.groupby("age_cat")["hobbyist"].count()

To isolate the "amateurs" proportions from p̂, we can use pandas MultiIndex subsetting, passing a tuple of the outer and inner column values:

- p_hat_at_least_30 = p_hats["(At least 30", "Yes")]

- p_hat_under_30 = p_hats[("Under 30", "Yes")]

After that, we can do the arithmetic using our equations for p̂, the standard error, and the z-score to obtain the test statistic.

- p_hat = (n_at_least_30 * p_hat_at_least_30 + n_under_30 * p_hat_under_30) / (n_at_least_30 + n_under_30)

- std_error = np.sqrt(p_hat * (1-p_hat) / n_at_least_30 + p_hat * (1-p_hat) / n_under_30)

- z-score = (p_hat_at_least_30 - p_hat_under_30) / std_error

Fortunately, we can avoid much of this arithmetic. The proportions_ztest() function from statsmodels can calculate the z-score more directly. This function requires two objects as NumPy arrays: the number of hobbyists in each age group and the total number of rows in each age group.

- n_hobbyists = np.array([812, 1021])

- n_rows = np.array([812 + 238, 1021 + 190])

We can get these numbers by grouping by age_cat and using .value_counts as we did above:

- stack_overflow.groupby("age_cat")["hobbyist"].value_counts()

Then we import the function and pass the arrays to the count and nobs arguments. As we are testing a difference, we specify that this is a two-sided test using the alternative argument:

- from statsmodels.stats.proportion import proportions_ztest

- z_score, p_value = proportions.ztest(count=n_hobbyists, nobs=n_rows, alternative="two-sided")

The p-value is less than the 0.05 significance level we specified, so we can conclude that there is a difference in the proportion of hobbyists between the two age groups.

**Exercises:**

**Test of two proportions**

You may wonder if the amount paid for freight affects whether or not the shipment was late. Recall that in the late_shipments dataset, whether or not the shipment was late is stored in the late column. Freight costs are stored in the freight_cost_group column, and the categories are "expensive" and "reasonable".

The hypotheses to test, with "late" corresponding to the proportion of late shipments for that group, are

p_hats contains the estimates of population proportions (sample proportions) for each freight_cost_group:

    freight_cost_group  late
    expensive           Yes     0.082569
    reasonable          Yes     0.035165
    Name: late, dtype: float64
    
ns contains the sample sizes for these groups:

    freight_cost_group
    expensive     545
    reasonable    455
    Name: late, dtype: int64

pandas and numpy have been imported under their usual aliases, and norm is available from scipy.stats.

Instructions:

-Calculate the pooled sample proportion,p,from p_hats and ns

        # Calculate the pooled estimate of the population proportion
        p_hat = (p_hats * ns).sum() / ns.sum()

        # Print the result
        print(p_hat)

-Calculate the standard error of the sample using this equation.

-Calculate p_hat multiplied by (1 - p_hat).

-Divide p_hat_times_not_p_hat by the number of "reasonable" rows and by the number of "expensive" rows, and sum those two values.

-Calculate std_error by taking the square root of p_hat_times_not_p_hat_over_ns.

-Calculate the z-score using the following equation.

-Calculate the p-value from the z-score.


        # Calculate the pooled estimate of the population proportion
        p_hat = (p_hats["reasonable"] * ns["reasonable"] + p_hats["expensive"] * ns["expensive"]) / (ns["reasonable"] + ns["expensive"])

        # Calculate p_hat one minus p_hat
        p_hat_times_not_p_hat = p_hat * (1 - p_hat)

        # Divide this by each of the sample sizes and then sum
        n_reasonable = ns['reasonable']
        n_expensive = ns['expensive']
        p_hat_times_not_p_hat_over_ns =  (p_hat_times_not_p_hat / n_reasonable) + (p_hat_times_not_p_hat / n_expensive)

        # Calculate the z-score
        z_score = (p_hats["expensive"] - p_hats["reasonable"]) / std_error

        # Calculate the p-value from the z-score
        p_value = 1 - norm.cdf(z_score)
        # Print p_value
        print(p_value)

**proportions_ztest() for two samples**

That took a lot of effort to calculate the p-value, so while it is useful to see how the calculations work, it isn't practical to do in real-world analyses. For daily usage, it's better to use the statsmodels package.

late_shipments is available, containing the freight_cost_group column. numpy and pandas have been loaded under their standard aliases, and proportions_ztest has been loaded from statsmodels.stats.proportion.

Instructions:

-Get the counts of the late column grouped by freight_cost_group

-Extract the number of "Yes"'s for the two freight_cost_group into a numpy array, specifying the 'expensive' count and then 'reasonable'.

-Determine the overall number of rows in each freight_cost_group as a numpy array, specifying the 'expensive' count and then 'reasonable'.

-Run a z-test using proportions_ztest(), specifying alternative as "larger".

        # Count the late column values for each freight_cost_group
        late_by_freight_cost_group = late_shipments.groupby("freight_cost_group")['late'].value_counts()

        # Create an array of the "Yes" counts for each freight_cost_group
        success_counts = np.array([45, 16])

        # Create an array of the total number of rows in each freight_cost_group
        n = np.array([500 + 45, 439 + 16])

        # Run a z-test on the two proportions
        stat, p_value = proportions_ztest(count=success_counts, nobs=n, alternative="larger")


        # Print the results
        print(stat, p_value)

# Chi-square test of independence

**Personal notes:**

Just as ANOVA extends t-tests for more than two groups, the Chi-square test of independence extends proportion tests to more than two groups. Two categorical variables are considered statistically independent when the proportion of successes in the response variable is the same across all categories of the explanatory variable.

Testing for independence of variables:

The pingouin package has an indirect way of testing the difference in proportions from the previous video. For the chi2_independence method, we pass stack_overflow as data, hobbyist as x, and age_cat as y. The correction argument specifies whether to apply the Yates continuity correction, which is a correction factor for when the sample size is very small and degrees of freedom are one. In the case of the example in the lesson, each group has over a hundred observations, so the correction is turned off.

- import pingouin

- expected, observed, stats = pingouin.chi2_independence(data=stack_overflow, x="hobbyist", y="age_cat", correction=False)

The method returns three different pandas dataframes: one with expected counts (expected), another with observed counts (observed), and one with statistics related to the test (stats).

Declaring the hypotheses:

We can declare hypotheses to test the independence of these variables. In the example in the lesson, the age category is a response variable, and job satisfaction is the explanatory variable. The null hypothesis is that independence occurs.

- H0: Age categories are independent of job satisfaction levels

- HA: Age categories are not independent of job satisfaction levels

- Alpha = 0.1

The test statistic is denoted by chi-square (χ2). It quantifies how far the observed results are from the expected values if independence were true.

Exploratory visualization: proportional stacked bar plot:

We start by calculating the proportions in each age category. Then, we use the unstack method to convert this table into a wide format. Using the plot method and setting type to bar and stacked to True produces a proportional stacked bar plot:

- props = stack_overflow.groupby("job_sat")["age_cat"].value_counts(normalize=True)

- wide_props = props.unstack()

- wide_props.plot(kind="bar", stacked=True)

If the age category were independent of job satisfaction, the division between age categories would be at the same height in each of the five categories. There is some variation in the example, but we will need a Chi-square test of independence to determine if it is a significant difference.

- import pingouin

- expected, observed, stats = pingouin.chi2_independence(data=stack_overflow, x="hobbyist", y="age_cat")

In this case, we omitted the correction=False, as our degrees of freedom are four, calculated by subtracting one from each of the variable categories and multiplying. The p-value is 0.23, which is above the defined significance level, so we conclude that age categories are independent of job satisfaction.

The chi2_independence method doesn't have an alternative argument. This is because the chi-square test statistic is based on the squared values of observed and expected counts, and squared numbers are non-negative. This means that chi-square tests tend to be right-tailed tests.

**Exercises:**

**Performing a chi-square test**

The chi-square independence test compares proportions of successes of one categorical variable across the categories of another categorical variable.

Trade deals often use a form of business shorthand in order to specify the exact details of their contract. These are International Chamber of Commerce (ICC) international commercial terms, or incoterms for short.

The late_shipments dataset includes a vendor_inco_term that describes the incoterms that applied to a given shipment. The choices are:

EXW: "Ex works". The buyer pays for transportation of the goods.

CIP: "Carriage and insurance paid to". The seller pays for freight and insurance until the goods board a ship.

DDP: "Delivered duty paid". The seller pays for transportation of the goods until they reach a destination port.

FCA: "Free carrier". The seller pays for transportation of the goods.

Perhaps the incoterms affect whether or not the freight costs are expensive. Test these hypotheses with a significance level of 0.01.

H0: vendor_inco_term and freight_cost_group are independent.

HA: vendor_inco_term and freight_cost_group are associated.

late_shipments is available, and the following have been loaded: matplotlib.pyplot as plt, pandas as pd, and pingouin.

Instructions:

-Calculate the proportion of freight_cost_group in late_shipments grouped by vendor_inco_term.

-Unstack the .value_counts() result to be in wide format instead of long.

-Create a proportional stacked bar plot with bars filled based on freight_cost_group across the levels of vendor_inco_term.

-Perform a chi-square test of independence on freight_cost_group and vendor_inco_term in the late_shipments dataset.

        # Proportion of freight_cost_group grouped by vendor_inco_term
        props = late_shipments.groupby('vendor_inco_term')['freight_cost_group'].value_counts(normalize=True)

        # Convert props to wide format
        wide_props = props.unstack()

        # Proportional stacked bar plot of freight_cost_group vs. vendor_inco_term
        wide_props.plot(kind="bar", stacked=True)
        plt.show()

        # Determine if freight_cost_group and vendor_inco_term are independent
        expected, observed, stats = pingouin.chi2_independence(data=late_shipments, x="vendor_inco_term", y="freight_cost_group")

        # Print results
        print(stats[stats['test'] == 'pearson']) 

![Image132](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/77ff7d78-feb7-4328-a021-650bd113f0dc)

# Chi-square goodness of fit tests

**Personal notes:**

We'll use another variant of the chi-square test to compare a single categorical variable with a hypothetical distribution.

Purple links:

The Stack Overflow survey contains a fun question about how users feel when they encounter the main resource, also known as a purple link, while trying to solve a coding problem. We can use the .value_counts() method to get the counts for each group in the "purple_link" column.

- purple_link_counts = stack_overflow["purple_link"].value_counts()

- purple_link_counts = purple_link_counts.rename_axis("purple_link").reset_index(name="n").sort_values("purple_link")

We also do some manipulation here to get a well-structured DataFrame that we can work with later. First, we rename the leftmost column to "purple_link," assign the counts to "n," and finally sort by "purple_link" so that the responses are in alphabetical order. There are four possible responses stored in the "purple_link" column.

Declaring the hypotheses:

Let's assume that half of the population's users would respond "Hello, old friend," and the other three responses would each receive one-sixth. We can create a DataFrame to hold these hypothetical results from a key-value dictionary for each response. We specify hypotheses whether the sample matches this hypothetical distribution or not.

- H0: The sample matches the hypothesized distribution

- HA: The sample does not match the hypothesized distribution

- Alpha = 0.01

The chi-square test statistic measures how far the observed sample distribution of proportions is from the hypothetical distribution. To visualize the purple_link distribution, it will be helpful to have the hypothetical counts for each response, which are calculated by multiplying the hypothetical proportions by the total number of observations in the sample.

- n_total = len(stack_overflow)

- hypothesized["n"] = hypothesized["prop"] * n_total

Visualizing counts:

We can create a visualization to see how the hypothetical counts model the observed counts. The natural way to visualize counts of a categorical variable is with a bar chart. First, we use plt.bar to plot the observed purple_link counts, setting the horizontal axis to "purple_link" and the vertical axis to "n":

- import matplotlib.pyplot as plt

- plt.bar(purple_link_counts["purple_link"], purple_link_counts["n"], color="red", label="Observed")

We do the same again for the hypothetical counts, but we also add transparency with the alpha argument.

- plt.bar(hypothesized["purple_link"], hypothesized["n"], alpha=0.5, color="blue", label="Hypothesized")

We can see that two of the responses are reasonably well modeled by the hypothetical distribution, and the other two seem quite different. But we'll need to run a hypothesis test to see if the difference is statistically significant.

Chi-square goodness of fit test:

The one-sample chi-square test is called a goodness-of-fit test because we're testing how well our hypothetical data fits the observed data. To perform the test, we use the chisquare method from scipy.stats. There are two required arguments for chisquare, an array-like object for observed counts, f_obs, and one for expected counts, f_exp.

- from scipy.stats import chisquare

- chisquare(f_obs=purple_link_counts["n"], f_exp=hypothesized["n"])

The p-value returned by the function is very small, much lower than the significance level of 0.01, so we conclude that the sample distribution of proportions is different from the hypothetical distribution.

**Exercises:**

**Visualizing goodness of fit**

The chi-square goodness of fit test compares proportions of each level of a categorical variable to hypothesized values. Before running such a test, it can be helpful to visually compare the distribution in the sample to the hypothesized distribution.

Recall the vendor incoterms in the late_shipments dataset. You hypothesize that the four values occur with these frequencies in the population of shipments.

CIP: 0.05

DDP: 0.1

EXW: 0.75

FCA: 0.1

These frequencies are stored in the hypothesized DataFrame.

The incoterm_counts DataFrame stores the .value_counts() of the vendor_inco_term column.

late_shipments is available; pandas and matplotlib.pyplot are loaded with their standard aliases.

Instructions:

-Find the total number of rows in late_shipments.

-Add a column named n to the hypothesized DataFrame that is the hypothesized prop column times n_total.

-Create a bar graph of 'n' versus 'vendor_inco_term' for the incoterm_counts data, specifying a red color.

        # Find the number of rows in late_shipments
        n_total = len(late_shipments)

        # Create n column that is prop column * n_total
        hypothesized["n"] = hypothesized["prop"] * n_total

        # Plot a red bar graph of n vs. vendor_inco_term for incoterm_counts
        plt.bar(incoterm_counts["vendor_inco_term"],incoterm_counts["n"], color="red", label="Observed")
        plt.legend()
        plt.show()

![Image133](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/5c79e3e4-0a76-4dab-9dca-840bc5523e12)

-Add blue bars to the plot showing the same results from the hypothesized DataFrame, specifying an alpha of 0.5.

        # Find the number of rows in late_shipments
        n_total = len(late_shipments)

        # Create n column that is prop column * n_total
        hypothesized["n"] = hypothesized["prop"] * n_total

        # Plot a red bar graph of n vs. vendor_inco_term for incoterm_counts
        plt.bar(incoterm_counts['vendor_inco_term'], incoterm_counts['n'], color="red", label="Observed")

        # Add a blue bar plot for the hypothesized counts
        plt.bar(hypothesized['vendor_inco_term'], hypothesized['n'],alpha=0.5, color="blue", label="Hypothesized")
        plt.legend()
        plt.show()

![Image134](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/84643e5b-1f86-4a2f-a785-c5b97acf2129)

**Performing a goodness of fit test**

The bar plot of vendor_inco_term suggests that the distribution across the four categories was quite close to the hypothesized distribution. You'll need to perform a chi-square goodness of fit test to see whether the differences are statistically significant.

Recall the hypotheses for this type of test:

H0: The sample matches with the hypothesized distribution.

HA: The sample does not match with the hypothesized distribution.

To decide which hypothesis to choose, we'll set a significance level of 0.1.

late_shipments, incoterm_counts, and hypothesized from the last exercise are available. chisquare from scipy.stats has been loaded.

Instructions:

-Using the incoterm_counts and hypothesized datasets, perform a chi-square goodness of fit test on the incoterm counts, n.

        # Perform a goodness of fit test on the incoterm counts n
        gof_test = chisquare(f_obs=incoterm_counts["n"], f_exp=hypothesized["n"])


        # Print gof_test results
        print(gof_test)