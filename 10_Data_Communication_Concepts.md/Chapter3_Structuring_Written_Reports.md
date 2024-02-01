# Structuring Written Reports

**Chapter description:**

Now that you understand how to prepare for communicating findings, it’s time to learn how to structure your reports. You'll also learn the importance of reproducibility (work smarter, not harder) and how to get to the point when describing your findings. You’ll then get to apply all you’ve learned to a real-world use case as you create a compelling report on credit risk.

# Types of reports

**Personal notes:**

*Types of Reports:*

There are different types of reports:

- *Informative Reports:* Provide factual information, are usually short, lack a rigid structure, and aim to inform about facts without adding any analysis.
  
- *Analytical Reports:* Provide analyses and demonstrate relationships or recommendations, can vary in size but have a rigid structure, and aim to guide decision-making based on data.
  
- *Final Reports:* Include detailed data analyses, findings, and results, as well as visual resources. They are generally long because they are intended for audiences that need technical details.
  
- *Summary Reports:* Include key findings and recommendations, as well as visual resources. They are usually short, under five pages, and, as a summary of a final report, may include links to the main document. They are intended for decision-makers who do not need technical details.

*Report Structure:*

There is a straightforward structure to follow for analytical, final, and summary reports. The first section is the introduction, where we summarize the report's objective. After that, contextual information about why we conducted the analysis shown should be included. To conclude the introduction, we must summarize our analysis questions.

Next, we create sections for the body of the report. In the data section, we write a description of the most relevant data used, potentially including tables. In the methods section, we describe the methods used to collect and analyze the data and build the model. In the analysis section, we include the selected data for analysis and model using visual resources, such as charts. In the results section, we describe and explain the results of our analysis, and we may include visual resources to assess them.

Finally, we create a conclusion section, where we restate the analysis questions, as well as summarize the most important results of the analysis. This part is the appropriate place to add our recommendations for the next steps.

*Report Structure (Business Context):*

In a business context, your audience is different, so you need to adapt. An efficient method is the 1-3-25 approach: 1-page abstract, a maximum of 3 pages of an executive summary, and a maximum of 25 pages of details. The executive summary is enough for people to understand and have their conclusions about whether it's worth reading the full report. Again, we must keep our audience in mind. Each stakeholder is interested in different parts of our report, so we should tailor accordingly.

**Exercises:**

**Something to report**

You need to present a report regarding your findings about customer churn and the predictive model you used, which you worked on in Chapter 1. Your project manager asks you to write it according to industry standards. You're aware that this requires you to follow a strict structure. Your manager also specifies that the report will be shared with technical stakeholders.

First, you write the sections separately: it's easier to handle that way. Then comes the time to bring all the sections together.

Can you organize the sections you wrote for the report in the correct order?

**Instruction:**

- Order the report sections so that the first section should be on top and the last at the bottom.

![image 16](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/8cd1a2b7-b507-40e8-afce-61af48563015)

**In summary**

Well done ordering the sections in your technical stakeholder report. Your project lead asks you to write a report to send to the directory board. They are non-technical stakeholders. You will revisit your previous report and tailor it as a summary report. But first, you want to refresh how a final report and a summary report differ.

Can you correctly classify the statements as characteristics of a final or summary report?

**Instruction:**

- Correctly classify the examples as a feature of either a final or summary report.

![Image 17](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/5773ed60-0b53-4393-9fec-01a13910edd5)

# Reproducibility and references

**Personal notes:**

### Reproducibility and References

*Written Report:*

A fundamental part of communicating our findings is ensuring that a report is clear and reproducible.

*Best Practices:*

- *Documentation:* Document all scripts used to obtain results, using comments in the code, and list all packages used in the environment. Version control systems like git can be useful for tracking changes and versions of scripts.
  
- *Avoid Manual Manipulation:* Avoid any manual data manipulation. Never directly edit the dataset in an editor. Save all versions of the dataset if possible. Save raw data along with a script with intermediate steps to create a clear narrative around data transformation.

- *Machine Learning Algorithms and Pipelines:* Use machine learning algorithms or pipelines in your workflow. Set a random seed to introduce reproducibility in model outputs. A random seed controls variable randomness, ensuring that a change is due to the model, not just randomness.

- *Interpretability:* Interpretability is crucial. A compelling narrative helps the audience understand and interpret findings. A clear story with a convincing narrative aids in reproducibility as the audience can comprehend and reproduce the conclusions.

- *Citations:* Properly cite the work of others used in the analysis. Citations provide essential information to identify and locate a specific publication. The APA style, which places the author's name first and the publication date next, is commonly used. Reference management tools like EndNote, Mendeley, and RefWorks help manage citations, change styles automatically, and search for sources online.

*In a Business Context:*

In a business context, reference citation rules are more relaxed. Many people simply include a hyperlink to the reference source. In this case, what matters is that the information is easily retrievable if the reader wants to consult the material from the sources.

**Exercises:**

**Replicate me**

Your manager asks you to write a report on your customer churn project for your peers at the New York office. She mentions that the team wants to replicate your work. After wrapping up the report, you add a link to your code repository. She looks confused and asks you why you did that.

You explain: If the New York team wants to replicate my work, then they should have access to the same ___ and the same ___ I used. However, if they want to achieve ___ , they can use their own set of tools.

Fill in the blank spaces by choosing the correct word combination from the options.

        "data, code, reproducibility"

**Same results**

Your manager is very interested in learning more about reproducibility. She asks you to give a short presentation at the weekly meeting. You're going to introduce the best practices to create reproducible data science results.

You prepare a slide presenting bad practices, and another one highlighting best practices.

Which of the following statements are considered best practices in reproducibility, and which should be avoided?

**Instruction:**

- Correctly classify the statements as best or bad practices.

![Image 18](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/a4527643-d122-4544-a2b6-3ae1d70d1185)

# Write precise and clear reports

**Personal notes:**

In data science, writing should be concise and precise to avoid misunderstandings and confusion. The target audience should understand our message, and there is no place for sentences that do not add information or introduce possible misunderstandings in our reports.

*Empty Phrases:*

Empty phrases distract and should be avoided. Be direct and get straight to the point. If a sentence doesn't add relevant information, remove it.

*Concrete Nouns:*

Effective technical writing is concise and direct. Use concrete nouns and avoid excessive use of pronouns like 'this' and 'that' to ensure clarity about what they refer to. Both active and passive voices have their critiques, with the active voice emphasizing the author over the facts and the passive voice being criticized for being too passive and challenging to read.

*Redundant Adjectives and Adverbs:*

In an attempt to emphasize an argument, it's easy to use redundant adjectives and adverbs. To keep the report concise, eliminate these unnecessary descriptors.

**Exercises:**

**Half-empty glass**

Your coworker, whom you helped with a project on price predictions in Chapter 2, asks you now to read his report. He wants your feedback as the report is designed for the executive team. Particularly, you should focus on fixing any empty or fat phrase, or colloquialism.

Can you help him identify improvable sentences, and suggest a better alternative?

**Instruction:**

- Correctly classify the examples as improvable or intelligible versions.

![Image 19](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/3c17ea43-6c55-4ab0-adbd-001151a7ed30)

**Strong words**

Your coworker is very satisfied with your feedback. He now asks you to look at another report he wrote for technical stakeholders. You noticed that the writing style is confusing and verbose. You decide to help him use more concrete nouns, and to fix redundant adjectives and run-on sentences.

Can you classify which of the following examples are intelligible, and which ones can be improved?

**Instruction:**

- Correctly classify the examples as either the correct or uncorrected version.

![Image 20](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/e002552b-2aa1-4519-a17d-f8e6c553dd09)

# Case study: report on credit risk

**Exercises:**

**Credit me**

You are about to leave the office when you get a call from the operation director. She tells you that you need to write a report on the credit score to present to the advisory board. She explains: "They want to understand your analysis to help plan a strategy to pre-select customers for loans".

Which of the following reports is the most suitable to write in this case?

       "An analytic report with boxplots displaying the relationship between loan and customer traits, and a barplot of most important predictors."

**Report my credit**

Your analytic report on the credit score project was a success. Your project manager was very satisfied with your work. Now, it's time to write the summary report for the financial department director. You want her to understand the key findings. Particularly, that the most important features for predicting a loan default are income, age, and employment length.

Can you put in order the sections of your summary report?

**Instruction:**

- Order the report sections so that the first section should be on top and the last at the bottom.

![Image 21](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/90634f40-1077-4e83-92a8-15c42ca2a125)