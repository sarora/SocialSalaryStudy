# Social Standards and Salary Inclinations Study

## Summary Links

Updated Analysis Workflow PDF rendering

| Deliverables      | Description |
|------------------|-------------|
| [Report](https://github.com/sarora/SocialSalaryStudy/tree/master/doc/sss_report.pdf)   | Final Report PDF |
| [Report RMD](https://github.com/sarora/SocialSalaryStudy/tree/master/doc/sss_report.Rmd)   |  Final Report ran in Rmd |
| [Proposal and Questions](https://github.com/sarora/SocialSalaryStudy/blob/master/doc/proposal.md) | Questions from survey

## Hypothesis

<h4 align="center"> Is a person's social standards correlated with a person's drive for financial wealth ?

 </a></h4>

<br>

## Overview

The purpose of this study is to measure whether a person is driven by money or not. We found it reasonable to assume that a person who is driven by money would expect to earn more than the average person who has the same skillset and experience. The `null` hypothesis is that the people who are driven by financial wealth and those that are driven by job satisfaction share the same social standards in terms of spending patterns while the `alternative` is that there is enough evidence to support that the two groups do not share the same spending patterns. A logistic regression is used to model the probability of belonging to the said groups given the explanatory spending and country of origin variables.


## Methodology

### Survey Study Design

The hypothesis test requires data collection. A survey is the best practical way of collecting the required data for this study. The questions for the study needs to be well formulated to ensure that the correct data is collected to reach a conclusion. The questions for this survey will contribute to determining either a person's social standards or expected salary. To avoid response bias the survey questions should not reveal what the hypothesis is that is being tested.

 The intended audience was originally our MDS class, but the invitation was extended to our social media accounts (LinkedIn, Facebook, etc.). The 5 questions [here](https://github.com/sarora/SocialSalaryStudy/blob/master/doc/proposal.md) are  conceptualized from both pertinent topics, one pertaining to the salary motivations and the latter is a measure of a participants social standards.

 The survey also captured the percentages of the main expenses of each participant. Each participant had to assign percentages that adds up to 100%. The different expense categories were strategically chosen which are believed to relate to a person's social standards. This is admittedly a difficult concept to measure, thus our focus is mainly to delineate the difference between essential expenditure versus lifestyle enhancement spendings. The vacation spending category is considered a non-essential category since it can be extrapolated that any non-conspicuous travels would (such as traveling to a nearby town to visit relatives) will only make up a marginal proportion of the overall spending. The daily leisure, hobbies and consumer goods categories are all deemed to fall under the non-necessary spending categories and the living expenses, savings and other are classified as basic needs.



### Data Overview


The following table summarises the key fields populated by the survey data and the calculated value, `ratio`, as a ratio of the two salary values.

|  Features       | Description                                                                |
|--------------------------|----------------------------------------------------------------------------|
| `salary_base`            | An indicator meant to be a subjective baseline of what salary a <br> person of their expertise would earn.      |
| `salary_expect`          | The expected salary combined with the base salary provides a relative <br> indicator to the respondent's pursuit of monetary gains. |
| `no_increase_acceptance` | A binary metric indicating whether a person prefers high job satisfaction of a salary increase.  |
| `ratio`                  | $\frac{Salary_{expect} - Salary_{base}}{Salary_{base}}$ allows us to differentiate those who <br>have a desire for a high increase in salary vs those that are satisfied with a modest amount.   |
| `living_expenses`        | Living Expenses (utilities, rent, mortgage, transportation, property taxes if owner, etc.) percentage of spending |
| `savings`                | Savings (retirement, investments, emergency funds, etc.) percentage of spending |
| `vacation`               | Vacation (lodging, transportation, day trips, etc.) percentage of spending |
| `daily_leisure`          | Daily Leisure (eating out, books, movies, self-care, etc.) percentage of spending |
| `consumption_goods`      | Consumption Goods (clothing, electronics, other luxury items, etc.) percentage of spending |
| `sports_hobbies`         | Personal Sports and Hobbies (sporting goods and services, gym, arts and crafts, etc.) percentage of spending |
| `other`                  | Other (health care, taxes, dependent expenses, etc.) percentage of spending |


Our response variable underwent a transformation to better differentiate the participants of interest since we cannot assume that a person with a high salary ratio is primarily driven by wealth as they may have specified that job satisfaction is a bigger driver than salary increase and vice-versa. Those that do not fall into either these two groups are considered to have answered ambiguously (expects a high salary increase, but is content with job satisfaction or the opposite) and cannot be considered for our study.


## Analysis Overview and Final Results

Our analysis wants to compare the two defined groups (participants who are driven by wealth and those who are not) in terms of spending habits.

|  Variable Type       | Variable Name                                                                |
|--------------------------|----------------------------------------------------------------------------|
| `response`            | `Participant Group` |
| `explanatory`          | `living_expenses` |
| `explanatory`          | `savings` |
| `explanatory`          | `vacation` |
| `explanatory`          | `daily_leisure` |
| `explanatory`          | `consumption_goods` |
| `explanatory`          | `sports_hobbies` |
| `explanatory`          | `other` |


Given the nature of our model variables, a logistic regression model would be the the most appropriate model choice - all the explanatory variables are continuous, whereas the response variable is a binary outcome.

Before excepting that this model is sufficient, it should be considered whether we are dealing with any confounding variables.

Each person who completed the survey had to report their country of employment. Data was collected from a number of different countries. The country a person works in has the potential to influence a person's spending behaviours regardless of their response group. For example, people from different countries may not spend the same amount on vacation, as found by [MoveHub](https://www.movehub.com/blog/worlds-biggest-travellers/).

We need to consider whether country has any significant effect our model. In our data, we have single observations for different countries, and a larger number of observations from Canada, South Africa and the US. A arguably logical solution to the handling of single country observations would be to group the countries by similarities. Seeing that Canada and the United States of America are neighbouring countries it we can group these two countries as `North America`.

South Africa, Nigeria and Botswana have a lot in common in terms of lifestyle, which means that we could group these observations as `Africa`. The other single observations should be omitted for this comparison, because it would require arbitrary assumptions for classifying these observations.

## Conclusion

It was found out that consumption goods showed some significance. This indicates that people who were classified as driven by wealth might tend to spend more on consumption goods than people who were not driven by wealth.

However, the model includes multiple comparisons. The p-values need to be adjusted in order to account for random significance.

Adjusting the p-values removes all significance from the logistic regression model. The lack of significance can be attributed to the lack of data. If more data was collected, the study would have had the potential to gain more power and make conclusive findings.

Refer [report](https://github.com/sarora/SocialSalaryStudy/blob/master/doc/proposal.md) for detailed explanation.


# Survey Study Design Reflection
The survey questions were constructed to account for all types of spending so that the respondent could better consider their proportional spending distribution. There are many subjective and psychological features that would contribute to someone's self-assessment of expected and base salary estimates which was accounted for when stating that we are looking at a person's drive for money, therefore their perceived attitude toward financial vocational incentives.

Clarifying the spending categories is a shortcoming of our study. There is a tradeoff between making our survey straightforward and being too transparent about the agenda behind the analysis with overly specific questions. There is some ambiguity behind the concept of social standards which we tried to account for in the vacation, hobbies, consumption and daily leisure categories, but we acknowledge that one could be partaking in conspicuous consumption while categorizing it as a living expense, such as paying a very high rent to live in the nicest neighborhood. The "Other" category could also be misleading because there could be some frivolous expenses that are not accounted for.

Self-assessments are not ideal since the participant is required to think objectively on the spot about their finances. This could inject a considerable source of bias, and would have required a more thorough assessment method than a survey.

It was good to use the point system to divide the spending because it forced the participant to consider each category of interest in proportion to the others. The improvement we would make is engineering a clearer divide between what is considered basic needs or not and comparing the expenditures to the local average spending percentages on necessities versus conspicuous spending.

---
<h6 align="center">
Created by

[Johannes Harmse](https://github.com/johannesharmse) &nbsp;&middot;&nbsp;
[Siddharth Arora](https://github.com/sarora) &nbsp;&middot;&nbsp;
[Veronique Mulholland](https://github.com/vmulholl)
</a></h4>
