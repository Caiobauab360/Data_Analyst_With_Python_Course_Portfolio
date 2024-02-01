# Preparing to Communicate the Data

**Chapter description:**

Deepen your storytelling knowledge. Learn how to avoid common mistakes when telling stories with data by tailoring your presentations to your audience. Then learn best practices for including visualizations and choosing between oral or written formats to make sure your presentations pack a punch!

# Selecting the right data

**Personal notes:**

*Inclusive Insights:*
Selecting the right data involves incorporating sufficient contextual insights into our story to support our main point without overwhelming our report with information. In other words, we include the minimum amount of results that will bolster our narrative. Remember that data is one of the three central elements of any story. Once we find the insights, we need to showcase our results appropriately to highlight a different view of the data for each audience.

*Stakeholders:*
Stakeholders can be anyone or a group of people with an interest in the outcome of a project, decision, or activity derived from it. Different stakeholders will be interested in different findings, so we need to tailor how we present our results to each of them. As mentioned earlier, stakeholders can be technical or non-technical.

*Identifying Personas:*
Among them, we may have different types of audiences. A useful tool is identifying audience personas. This means describing the interests in project outcome and technical knowledge of someone who represents our ideal target audience. Defining personas helps select customized findings to better convey our key insights.

1. *Executive Team:*
   The first person you might report to is the executive team—likely the CEO, an investor, a director, or a founder. They have a basic understanding of technical aspects and usually need to inform their decisions using our project findings.

2. *Project Manager:*
   When telling the story to our project manager, we can showcase the total cost of the upcoming proposal steps and general metrics, as well as the risk of our plan failing.

3. *Tech Team:*
   We can also present a report to our project collaborators or a technical supervisor with high technical knowledge. They are likely interested in replicating or continuing the project.

4. *General Audience:*
   Finally, we can present our story to an external client or another department employee, likely with basic technical knowledge, wanting to understand the project's impact.
 
**Exercises:**

**The truth about salaries**

Your predictive model for customer churn, which you worked on in Chapter 1, has been deployed. Your project manager asks you to work on a new internal project. The goal is to analyze a database with employee salaries in San Francisco, USA.

After doing an exhaustive exploratory data analysis, you have to present your findings to the human resources team. They want to compare San Francisco salary growth to the one at the company; they need to understand how to forecast salaries for the next year. You are about to copy the graphs from your analysis. Your manager reminds you to select the right data for your stakeholders.

You start by writing down what you believe can help you choose the proper findings.

One of the statements you wrote is false. Can you select which one it is?

        Answer: "Select all collected numerical data about San Francisco salaries and show them in a big dashboard so it helps understand in detail why salaries have been increasing."


**Earning interests**

Well done! Your presentation with the human resource department was a success. Your team lead asks you to show your data analysis results to different stakeholders. Before you dive into preparing the presentation or the report, you want to make sure that you are aligned with their interests.

With that goal in mind, you define several personas. It will help you select the suitable data later. You write down the personas, their knowledge, and their interest on this project.

Can you classify your notes into the following audience personas?

**Instruction:**

- Correctly classify the following examples as Human Resources Director, technical supervisor, or marketing staff.

![Image 9](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/e054ecb9-99cc-4099-9ebb-83a61cddd8a7)

# Showing relevant statistics

**Personal notes:**

*Variations of Data:*

Sometimes, we want to compare one or several specific variables over time. The difference can be expressed with an absolute number or a growth rate. When focusing on one variable, an absolute number is okay, but when looking at various variables, the growth rate tends to be more informative as it allows for comparisons across different scales. Absolute changes for a small number may seem small even if the relative change is large, and vice versa.

*Ratio:*

A ratio is a comparison of two variables expressed as a quotient, like revenue per customer: calculated as the total revenue of the product in dollars divided by the number of customers. Ratios help normalize values, which, in turn, aids in comparing the distribution of data from originally different scales.

*Aggregates:*

Sometimes we need to summarize numerical data into an aggregate—a number that gives an idea of one or a representative value. It can be a simple total or count, like total sales or how long a campaign will last. Another common aggregate is the average, such as the average number of chocolates or snacks sold per year or the average (median) price of each product. The average can be misleading, especially if there are outliers.

*p-value:*

When communicating results, we often need to provide evidence that they are statistically significant (i.e., not due to randomness). A p-value below 0.05 is considered an indicator of significance by convention. The lower it is below 0.05, the stronger the indicator. However, it is not proof of evidence; it only rejects or accepts a hypothesis without saying anything about its truth. Due to the frequency with which p-value metrics are misunderstood or confusing for the public, consider alternative metrics or add a few more in support.

**Exercises:**

**Salary variation**

You have selected suitable data for your story on San Francisco salaries. Now, you evaluate which metrics you should use.

You want to convey the following message to the human resource team: "The total pay of employees has increased or decreased according to their job title from 2017 to 2018."

You prepared the two visualizations below, but you are unsure which one is best.

One of the following options is True. Can you select which one is it?

        "The graph on the right is the best way to convey the message. With percentage change, the magnitude of the salary change depending on the job is more evident."

**On a payroll**

Good job on selecting the most impactful visualization! Your insight made an impact. The human resource team lead asked you to show more findings. You go back to your exploratory data analysis and select some data.

But you want to explore different variants of the same data to discover the best one for explaining your distinct insights to the human resource team.

Can you decide what data variant would be best suited depending on the finding you want to show?

**Instruction:**

- Correctly classify the following examples as total values, change or ratio.

![Image 10](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/b4f84a31-44cc-4c60-af18-84c5050e05cd)

**It's not significant**

You have a big deadline ahead. You need to submit a report on the data analysis for the project on San Francisco salaries to your technical lead. He will read it and report your results to the senior management team.

You have a story, and you select data to support it. You want to show comparisons of average pay for people with different job titles.

You are hesitant to show p-values. You know that there are a lot of misconceptions around it. You decide to use it anyway. However, you plan to clarify any confusion about p-values, so your audience understands its meaning and trusts your results.

Can you classify these statements as good use or misuse of the p-value?

**Instruction:**

- Correctly classify the following examples as either a good use or a misuse.

![Image 11](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/400817b9-39fa-429e-8654-fec175543f4c)

# Visualizations for different audiences

**Personal notes:**

*Provide Context:*

When we find insights and have the right data, we still need to choose and adjust a visualization for the message we want to convey. Again, we should consider our audience's expertise and familiarity with concepts to select charts they can easily interpret.

*Provide Context:*

Visualizations should also provide context to support our message. For an investor, we might include a chart showing the factors that most influence a customer to buy our products. A technical leader will be interested in that but also more details about the analysis itself, like the detailed importance of the feature.

*More Best Practices:*

The Pareto principle states that the majority of outputs come from a minority of inputs. Therefore, in addition to the data contributing to our story, there will be some less relevant data that we still want to include. We should aggregate them to reduce noise. Our visual assets can become accessible and engaging by considering the audience's background and simplifying the visuals to the audience's knowledge level. Basically, you care about how many insights your audience gets from your visualization and how quickly they get it. A complex plot gives many insights but takes time to understand; a simple plot gives few insights but is quick to understand. Overall, less is more. Instead of showing many detailed visuals, we should focus on the simplest and most relevant ones that support our message.

*McCandless Method:*

There are some steps we can follow to include and present the visualization effectively to our audience. They were established by David McCandless, a British data journalist. First, we should give a title to our chart, which we then use to introduce the visualization and focus the audience's attention on it. The title should be short, clear, and obvious: it supports our story and clarifies the visualization. When in doubt, we can use the y-axis vs x-axis technique. Next, we should anticipate common questions from our audience. With these questions answered before they are even asked, attention is directed to our chart and our story. After that, we need to clarify which insights the visual is showing. We should explain what they are seeing and not assume they will ask later or understand on their own. For example, chocolate sales decreased over time. Finally, we need to help the audience relate to the chart and its insights. Make sure they understand why the insights are important, how it will support additional insights in the presentation, or how these insights can be put into practice.

**Exercises:**

**Salary development**

You are presenting your data analysis of San Francisco salaries to the business development department.

You have your story, and you selected data and metrics to support it. But choosing the visualizations is still an ongoing task. You decide to speed it up by getting hands-on. You want to follow the best practices.

The message you want to convey is: "San Francisco salaries have been constantly going up in the last 4 years. The percentage variation is 10% annually. The salary of people working in the private sector, such as software or biotechnology, have increased by 100k."

Can you classify if these practices would be good or bad when presenting to the business department?

**Instruction:**

- Correctly classify the following statements as being either true or false for choosing an effective visualization.

![Image 12](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/a0a1ee33-07cc-4e01-91e6-1706b9bd7c9c)

**Salary on demand**

You have selected visualizations for the business development department.

It's time to include them in your report and present them. You are aware of the steps you should follow to include and present visualizations effectively, and you want to do your best and impress your business coworkers. So you ask a colleague to help you organize your thoughts.

Can you order the steps for including and presenting visual data effectively?

**Instruction:**

- Order the steps chronologically: the first step should be on top and the last step at the bottom.

![Image 13](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/49883af4-8387-4bc8-b181-1851657627e4)

# Choosing the appropriate format

**Personal notes:**

*Presentation Strategy:*

A good communication format displays key project information in an innovative and easy-to-understand way. There are two main formats we will discuss here: written reports and oral presentations. Most data science projects will require both a written report and an oral presentation, but ultimately, it depends on the situation and the specific project.

*Presentation Strategy:*

There are several things to consider when sharing findings: our audience, the content to include, special requirements to take into account, and which channel to use. All these elements help us define the best format to communicate our results.

*Stakeholders:*

The first thing to consider is who we are presenting to; this helps figure out why they need to know about the findings. Is it for accountability? To understand the methodology? How will they use our findings - to make a decision, initiate a new project? What information do they need from our results? The impact our findings have?

*Content:*

The answers to these questions help us decide what content to include. Should we focus on results, conclusions, include recommendations, or just explain the methods in detail?

*Requirements:*

The next step is to identify if any stakeholders have special requirements. Do they have enough time to read a detailed report, or is a short meeting better? Do they report to someone else and need a document to back up a claim? Are they in a different time zone, so written communication is preferable?

*Consumption:*

We also need to think about how our presentation will be consumed. Could we write a document like a Word file, a Jupyter notebook, a blog post, or an article? We could also build a slide deck. How will it be delivered? Will we present directly to stakeholders, being able to respond to comments or questions, or will we share via email or Slack and answer questions later? Finally, what would be the audience size? We cannot present things the same way in a conference room with six people or in a hall for two hundred people.

*Oral Communication:*

Oral communication allows building a relationship with the audience and facilitates immediate feedback or actions. It conveys a rich message because body language and voice add meaning. However, the message cannot be revised because there is no permanent record of communication and is not suitable for long messages, as the longer the presentation, the higher the chance the audience will lose focus at some point.

*Written Communication:*

The written format provides records of communication so that the message can be reviewed in the long term. It is easy to share with large audiences and is less prone to emotional reactions. It is also suitable for sharing code with any interested technical individuals for review or replication. However, not seeing the audience's reaction makes adaptation more challenging, as feedback is not immediate but will come later in the form of comments.

**Exercises:**

**A communication problem**

Your coworker has been working on a project on price predictions. He asks you to help him choose the most suitable format to deliver his results to the executive board as well as to his team.

You give him a set of advice and rules of thumb, so he can make an informed decision. When you arrive home, you realize that you made one mistake.

Which of the following advice should you not have provided?

        "If a software engineer in your team wants to continue your project with new data, the central piece of information to include in your meeting is the project conclusions."

**Should we meet?**

It's Friday. Your project manager comes by your desk. She asks you about the status of your project on salaries for San Francisco employees. She tells you that you need to close the project. Fortunately, you have finished building the model.

But to close it, you need to communicate the results to the different stakeholders. After she talks with the people involved, you start to receive emails asking about the results. You need to decide if you are going to use an oral presentation or a written report.

Can you decide what type of format would be best suited depending on the situation and requirements?

**Instruction:**

- Correctly classify the following inquiries as suitable for an oral or written format.

![Image 14](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/3f8b92bd-a175-4cd9-be14-35bc84b531d2)

**When in doubt**

You manage to deliver the results to almost all the stakeholders. You are about to start writing the report for the founder when you get an email. Your founder is coming by the office the following Friday. Your manager wants to know if presenting the project during a meeting would be better.

You have second thoughts about changing the format. So you decide to write down beneficial and unfavorable aspects of an oral presentation.

Can you classify your thoughts correctly?

**Instruction:**

- Correctly classify examples where an oral presentation is either beneficial or a unfavorable.

![Image 15](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/90a0d6b3-93b5-40d9-a9cb-d029f3a91f18)