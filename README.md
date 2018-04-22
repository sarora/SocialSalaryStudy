# Social Standards and Salary Inclinations Study

## Summary Links

| Deliverables      | Description |
|------------------|-------------|
| [EDA Report](doc/sss_report.pdf)   | Final Report PDF |
| [EDA RMD](doc/sss_report.Rmd)   |  Final Report ran in Rmd |
|[Analysis Workflow](src/analysis_workflow.Rmd)|Exploratory Data Analysis|
| [Milestone 1 Commit](https://github.ubc.ca/ubc-mds-2017/SocialSalaryStudy/commit/a6699731ac3e9b740a113a2781e720f03c44dac5) | Final commit before release |
| [Release v2.0](https://github.ubc.ca/ubc-mds-2017/SocialSalaryStudy/releases/tag/v2.0) |Milestone 1 release |
| [Survey Monkey Link](https://www.surveymonkey.com/r/2MS6758) | Survey link |
| [Proposal and Questions](https://github.ubc.ca/ubc-mds-2017/SocialSalaryStudy/blob/vmulholl/doc/proposal.md) | Questions from survey (in case the survey has been completed and cannot be accessed) |



## Hypothesis

<h4 align="center"> Is a person's social standards correlated with a person's expected salary? </a></h4>

<br>

## Overview

The goal of this study is to determine whether a person's social standards are correlated with a person's expected salary. The idea behind the hypothesis is that people who have higher social standards expect a higher salary. The opposite can also be argued - does a person's expected salary determine a person's social standards? This study does not aim to determine which variables are explanatory or a response, but rather to determine whether a strong correlation exists between social standards and expected salary. We found it reasonable to assume that a person who is driven by money would expect to earn more than the average person who has the same skillset and experience.

## Methodology

The test statistic will be attempting to identify if there is a strong correlation between social standards and a person's salary expectations. A positive correlation would be expected between the continuous numerical measurement of social standards and the normalized continuous expected salary range. Social standards and expected salaries are expected to both form t-distributions given the survey responses. A linear regression model seems to be an appropriate choice for the study, since our response variable (expected salary) is a continuous range and the explanatory variables related to social standards are expected to have a linear relationship with expected salary.

### Survey

The hypothesis test requires data collection. A survey is the best practical way of collecting the required data for this study. The questions for the study needs to be well formulated to ensure that the correct data is collected to reach a conclusion. The questions for this survey will contribute to determining either a person's social standards or expected salary. To avoid response bias the survey questions should not reveal what the hypothesis is that is being tested.

For the purpose of this study, social standards will be defined as a person's inclination for a high relative consumption on leisure activities and non-essential expenditure. Our hypothesis relies on the theory that prevailing social conditions will influences one's relationship with money which would translate in whether increase in income is the priority.

Our survey has captured the salary of what a participant thinks an average person with their skills and experience should earn, as well as the salary that the participant expects to receive in 1 year's time. Taking inflation and other micro-factors into account, a participant's expected salary in a year's time shouldn't be much higher than the average person with the same skills and experience.

The participant's salary was stored in their unique currency. The survey was answered by people from various countries with different currencies. This means that we cannot compare the captured salary values between participants. An easy way of standardising these values is to handle the salary values as a ratio of expected salary over average salary. The ratio should be consistent across different currencies.

## Analysis Overview

The study is interested in the ratio distribution above. Is there any correlation between the above ratio and social standards? The premise of the study was to develop a metric that would indicate the inclination of individuals to see financial gain as the main driver for success and determine if there is a relationship with the way their income is spent. Three variables were collected that pertain to our model's dependent variable which include:

| Dependent Features       | Description                                                                |
|--------------------------|----------------------------------------------------------------------------|
| `salary_base`            | An indicator meant to be a subjective baseline of what salary a <br> person of their expertise would earn.      |
| `salary_expect`          | The expected salary combined with the base salary provides a relative <br> indicator to the respondents pursuit of monetary gains. |
| `no_increase_acceptance` | A binary metric serves as a safety check against false positives, that is respondents <br> that may have over-exagerated  their expected salary skewing <br> the impression of interest in monetary gain while in reality being content with their current situation.  |
| `ratio`                  | This is a calculated metric that simplifies handling respondent's country selection.                                  |

The survey also captured the percentages of the main expenses of each participant. Each participant had to assign percentages that adds up to 100%. The different expense categories were strategically chosen which are believed to relate to a person's social standards. For example, it is believed that a person who spends a large percentage on vacations and daily leisure most likely has higher social standards than a person who contributes most of their salary to savings. The hypothesis is that a person with higher social standards will have a higher salary ratio as described above.

It is difficult to visualize the interaction between expenses, salary ratio and job satisfaction versus salary increase preference. It seems more logical and of statistical importance to fit comparitive models and observe whether the confounder variable adds any value to the model. The salary ratio is a continuous variable and from our ratio probability distribution earlier, we saw that the standard deviation is fairly normally distributed around the mean after removing outliers. For this reason a linear regression model seems like a sensible model to fit to our data.

We want to determine whether the preference for job satisfaction interacts with with our explanatory variables. The explanatory variables in our case are the expense categories. We need to compare an additive linear model with a model that considers job satisfaction as a variable that interacts with our expense categories. The following joy plot displays the distribution of participant spendings.


---
<h6 align="center">
Created by

[Johannes Harmse](https://github.com/johannesharmse) &nbsp;&middot;&nbsp;
[Siddharth Arora](https://github.com/sarora) &nbsp;&middot;&nbsp;
[Veronique Mulholland](https://github.com/vmulholl)
</a></h4>
