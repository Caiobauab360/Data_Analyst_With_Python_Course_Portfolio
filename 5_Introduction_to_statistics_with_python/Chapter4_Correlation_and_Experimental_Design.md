# Correlation and Experimental Design

**Description:**

In this chapter, you'll learn how to quantify the strength of a linear relationship between two variables, and explore how confounding variables can affect the relationship between two other variables. You'll also see how a study’s design can influence its results, change how the data should be analyzed, and potentially affect the reliability of your conclusions.

# Correlation

**Personal notes:**

You've provided an overview of correlation between two numeric variables. Here are the key points:

**Correlation between Numeric Variables:*
- Correlation measures the strength and direction of the linear relationship between two numeric variables.

- The variables are often referred to as the independent (X) and dependent (Y) variables.

- Correlation coefficients range from -1 to 1, where the magnitude indicates the strength of the relationship, and the sign (positive or negative) indicates the direction.

- A correlation coefficient of 0.99 is considered a near-perfect or very strong relationship, suggesting that if you know the value of X, you can make a good prediction of Y. A coefficient of 0.75 is considered a strong relationship, 0.56 is moderately correlated, and around 0.21 is considered a weak relationship.

- A correlation coefficient close to 0 indicates no linear relationship, and the scatter plot appears random.

- A positive correlation coefficient implies that as X increases, Y also increases, while a negative correlation coefficient implies that as X increases, Y decreases.

**Visualizing Relationships:*

- Seaborn, a data visualization library built on top of Matplotlib, can be used to create scatter plots to visualize relationships between two variables.

- You can add a linear trendline to a scatter plot using `sns.lmplot()` with the `ci=None` argument to remove confidence intervals.

**Calculating Correlation:*

- The correlation between two series can be calculated using the `.corr()` method. For example: `msleep["sleep_total"].corr(msleep["sleep_rem"])`.

**Pearson Correlation:*

- The chapter uses the Pearson product-moment correlation, denoted as r. It is the most commonly used measure of correlation and quantifies the strength and direction of a linear relationship.

Understanding correlation is crucial in data analysis, as it helps identify relationships between variables, which can be valuable for making predictions or drawing insights from data.

**Exercises:**

**Relationships between variables**

In this chapter, you'll be working with a dataset world_happiness containing results from the 2019 World Happiness Report. The report scores various countries based on how happy people in that country are. It also ranks each country on various societal aspects such as social support, freedom, corruption, and others. The dataset also includes the GDP per capita and life expectancy for each country.

In this exercise, you'll examine the relationship between a country's life expectancy (life_exp) and happiness score (happiness_score) both visually and quantitatively. seaborn as sns, matplotlib.pyplot as plt, and pandas as pd are loaded and world_happiness is available.

Instructions:

-Create a scatterplot of happiness_score vs. life_exp (without a trendline) using seaborn.

-Show the plot.

      # Create a scatterplot of happiness_score vs. life_exp and show
      sns.scatterplot(x="life_exp", y="happiness_score", data=world_happiness)

      # Show plot
      plt.show()

![Image50](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/ed6f55b2-cc5a-4fb1-a144-468816fba147)


-Create a scatterplot of happiness_score vs. life_exp with a linear trendline using seaborn, setting ci to None.

-Show the plot.

-Calculate the correlation between life_exp and happiness_score. Save this as cor.


      # Create scatterplot of happiness_score vs life_exp with trendline
      sns.lmplot(x="life_exp", y="happiness_score", data=world_happiness, ci=None)

      # Show plot
      plt.show()

      # Correlation between life_exp and happiness_score
      cor = world_happiness["life_exp"].corr(world_happiness["happiness_score"])

      print(cor)

![Image51](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/114eb0e5-fb61-4ac9-ae76-8792a7d48e45)

# Correlation caveats

**Personal notes:**

You've discussed some important caveats when dealing with correlation:

**1. Linearity of Correlation:*
   - Correlation measures the strength of linear relationships between variables. It may not capture non-linear relationships effectively.
   - For highly skewed data, transformations like taking the logarithm (e.g., `np.log()`) can be applied to make the relationship more linear.

**2. Transformation Techniques:*
   - In addition to log transformations, other techniques such as square root (e.g., `np.sqrt()`), reciprocal (e.g., `1/x`), or other power transformations can be used to linearize relationships.
   - The choice of transformation depends on the data and the degree of distortion.

**3. Linear Assumptions:*
   - Certain statistical methods, like calculating a correlation coefficient or performing linear regression, assume that variables have a linear relationship.
   - Transformations may be necessary to meet these assumptions.

**4. Correlation vs. Causality:*
   - Correlation does not imply causality. If two variables (X and Y) are correlated, it doesn't mean that X causes Y or vice versa.
   - Spurious correlations can occur due to a lurking or confounding variable. This third variable may be the actual cause of the observed correlation between X and Y.

Understanding these caveats is crucial in data analysis to avoid drawing incorrect conclusions or making unwarranted assumptions about causality based on correlation alone. It's essential to consider the nature of the data and apply appropriate techniques when analyzing relationships between variables.

**Exercises:**

**What can't correlation measure?**

While the correlation coefficient is a convenient way to quantify the strength of a relationship between two variables, it's far from perfect. In this exercise, you'll explore one of the caveats of the correlation coefficient by examining the relationship between a country's GDP per capita (gdp_per_cap) and happiness score.

pandas as pd, matplotlib.pyplot as plt, and seaborn as sns are imported, and world_happiness is loaded.

Instructions:

-Create a seaborn scatterplot (without a trendline) showing the relationship between gdp_per_cap (on the x-axis) and life_exp (on the y-axis).

-Show the plot

-Calculate the correlation between gdp_per_cap and life_exp and store as cor.

      # Scatterplot of gdp_per_cap and life_exp
      sns.scatterplot(x='gdp_per_cap', y='life_exp', data=world_happiness)

      # Show plot
      plt.show()
  
      # Correlation between gdp_per_cap and life_exp
      cor = world_happiness["gdp_per_cap"].corr(world_happiness["life_exp"])

      print(cor)

![Image52](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/9c7404cf-1c0d-4ac4-bf16-107bfdda5a66)


**Transforming variables**

When variables have skewed distributions, they often require a transformation in order to form a linear relationship with another variable so that correlation can be computed. In this exercise, you'll perform a transformation yourself.

pandas as pd, numpy as np, matplotlib.pyplot as plt, and seaborn as sns are imported, and world_happiness is loaded.

Instructions:

-Create a scatterplot of happiness_score versus gdp_per_cap and calculate the correlation between them.

      # Scatterplot of happiness_score vs. gdp_per_cap
      sns.scatterplot(x="gdp_per_cap", y="happiness_score", data=world_happiness)
      plt.show()

      # Calculate correlation
      cor = world_happiness["gdp_per_cap"].corr(world_happiness["happiness_score"])
      print(cor)

![Image53](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/f97dde45-14c3-4895-898f-dcfb150ca6f6)

-Add a new column to world_happiness called log_gdp_per_cap that contains the log of gdp_per_cap.

-Create a seaborn scatterplot of happiness_score versus log_gdp_per_cap.

-Calculate the correlation between log_gdp_per_cap and happiness_score.

      # Create log_gdp_per_cap column
      world_happiness['log_gdp_per_cap'] = np.log(world_happiness["gdp_per_cap"])

      # Scatterplot of happiness_score vs. log_gdp_per_cap
      sns.scatterplot(x="log_gdp_per_cap", y="happiness_score", data=world_happiness)
      plt.show()

      # Calculate correlation
      cor = world_happiness["log_gdp_per_cap"].corr(world_happiness["happiness_score"])
      print(cor)

![Image54](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/fe07690b-ad73-4d18-9018-6e63aeea8dc1)

**Does sugar improve happiness?**

A new column has been added to world_happiness called grams_sugar_per_day, which contains the average amount of sugar eaten per person per day in each country. In this exercise, you'll examine the effect of a country's average sugar consumption on its happiness score.

pandas as pd, matplotlib.pyplot as plt, and seaborn as sns are imported, and world_happiness is loaded.

Instructions:

-Create a seaborn scatterplot showing the relationship between grams_sugar_per_day (on the x-axis) and happiness_score (on the y-axis).

-Calculate the correlation between grams_sugar_per_day and happiness_score.

      # Scatterplot of grams_sugar_per_day and happiness_score
      sns.scatterplot(x="grams_sugar_per_day", y="happiness_score", data=world_happiness)
      plt.show()

      # Correlation between grams_sugar_per_day and happiness_score
      cor = world_happiness["grams_sugar_per_day"].corr(world_happiness["happiness_score"])
      print(cor)

![Image55](https://github.com/Caiobauab360/Data_Analyst_Course_Portfolio/assets/127256295/d3e39890-7709-455c-9c03-1a57b54f523e)

# Design of experiments

**Personal notes:**

**Design of Experiments*

Many times, data is created as a result of a study aimed at answering a specific question. However, data needs to be analyzed and interpreted differently depending on how it was generated and how the study was designed. Experiments often aim to answer a question in the form of "What is the effect of the treatment on the response?" In this scenario, the treatment refers to the explanatory or independent variable, and the response refers to the outcome or dependent variable.

**Longitudinal and Cross-Sectional Studies*

- In longitudinal studies, participants are followed over a period of time to examine the effect of treatment on the response. These studies track changes or developments within the same individuals over time.

- In a cross-sectional study, data is collected from a single snapshot in time. These studies provide a snapshot of a population or group at a specific point in time but do not track changes within individuals over time.

The choice between a longitudinal and a cross-sectional study design depends on the research question and the nature of the investigation. Longitudinal studies are ideal for examining changes and trends over time, while cross-sectional studies provide insights into a population's characteristics at a specific moment. Each design has its advantages and limitations, and researchers must carefully select the most appropriate design to address their research objectives.


