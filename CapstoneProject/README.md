# Home Credit Default Risk

<img src="/CapstoneProject/reports/figures/home credit logo.jpeg" width="500"/>

## Introduction

This repository contains **predictive analytics competition** hosted at Kaggle:
[Home Credit Default Risk](https://www.kaggle.com/competitions/home-credit-default-risk/overview)


## Table of Contents
The repository includes following series of contents.

- Busienss Statement
- Data Description
- ERD (Entity Relation Diagram)
- Final Presentation
- Takeways from Project
    - Assumptions
    - Analytic Findings & Business Actions
    - Improvement & Recommendation

## Business Statement

**Business Problem:** What is the problem?  Why is it a problem?
>  Most of individuals' payment capacities are likely to be assessed with his or her banked history & credit usage histories. This method prevents unbanked population who hasn't obtain credit hitory yet from starting or activating their financial loan activities. Therefore, [Home Credit](https://www.homecredit.net/) is the company who is dedicated to provide lines of credit (loans) to the unbanked population.

**Benefit of a solution**. How will the business benefit from a solution?
> Building stable prediction model to identify credible candidates leads to a stable & controllable financial system for Home Credit, which increases the number of personal loaners who hasn't the financial history yet. Also it would result in providing a positive and safe borrowing experience for underserved people.

**Success Metrics.** How will stakeholders judge whether the project was a success?
> Success Metrics are evaluated on area under the ROC curve (AUC) between the predicted probability and the observed target.

**Analytics Approach.** What is the general character of the analytics approach to solving the problem? Will a supervised or unsupervised approach be used?  If supervised, is the problem regression or classification?  What is the target variable?
> This project makes use of supervised approach with classification model to predict which application has a repayment abilities based on the previous application histories. The target variable is encoded either 0 or 1, which indicates client with payment difficulties.

**Scope:** What will be delivered and what will be out of scope? What might be added later?
> In scope: In this project, the list of applications which is capable of repayment will be given for the deliverables.
> Out of scope: Hasn't identified yet.

**Details:** Who is going to execute the project? When will the project be finished? Are there important project milestones?
> [Richard Lim](https://www.linkedin.com/in/datarichard/) is going to excute this project as a capstone project. the project milestone (calendar) is listed as table below.



| Assignment  | Type        | Time frame  | Description |
| ----------- | ----------- | ----------- | ----------- |
| Github | Individual | Week 2 | Set up your individual Github repo.  This is where you will develop your personal analytics portfolio and--potentially--collaborate with others in your group.
| Business Problem Statement | Individual |	Week 3 |	Write a short statement framing the business and analytic problems for the Home Credit project.
| EDA Notebook | Individual	| Weeks 4-6 | Create an individual notebook documenting your data exploration and cleaning.
| Modeling Notebook	| Group | Weeks 7-11 | Create a group notebook documenting the modeling process.
| Presentation | Group | Weeks  12-16 |	Present your group's analytic results. 
| Github Analytics Portfolio | Individual |	End of course |	This is a collection of all your individual project-related work, from business problem framing to modeling.

## Data Description

**application_{train|test}.csv**

> This is the main table, broken into two files for Train (with TARGET) and Test (without TARGET). Static data for all applications. One row represents one loan in our data sample.

**bureau.csv**

> All client's previous credits provided by other financial institutions that were reported to Credit Bureau (for clients who have a loan in our sample).
For every loan in our sample, there are as many rows as number of credits the client had in Credit Bureau before the application date.

**bureau_balance.csv**

> Monthly balances of previous credits in Credit Bureau. This table has one row for each month of history of every previous credit reported to Credit Bureau – i.e the table has (#loans in sample * # of relative previous credits * # of months where we have some history observable for the previous credits) rows.

**POS_CASH_balance.csv**

> Monthly balance snapshots of previous POS (point of sales) and cash loans that the applicant had with Home Credit.
This table has one row for each month of history of every previous credit in Home Credit (consumer credit and cash loans) related to loans in our sample – i.e. the table has (#loans in sample * # of relative previous credits * # of months in which we have some history observable for the previous credits) rows.

**credit_card_balance.csv**

> Monthly balance snapshots of previous credit cards that the applicant has with Home Credit.
This table has one row for each month of history of every previous credit in Home Credit (consumer credit and cash loans) related to loans in our sample – i.e. the table has (#loans in sample * # of relative previous credit cards * # of months where we have some history observable for the previous credit card) rows.

**previous_application.csv**

> All previous applications for Home Credit loans of clients who have loans in our sample.
There is one row for each previous application related to loans in our data sample.

**installments_payments.csv**

> Repayment history for the previously disbursed credits in Home Credit related to the loans in our sample.
There is a) one row for every payment that was made plus b) one row each for missed payment.
One row is equivalent to one payment of one installment OR one installment corresponding to one payment of one previous Home Credit credit related to loans in our sample.

**HomeCredit_columns_description.csv**

> This file contains descriptions for the columns in the various data files.

## ERD (Entity Relation Diagram)

<img src="/CapstoneProject/reports/figures/ ERD.png" width="1000"/>

## EDA

[EDA Notebook](notebooks/EDA/EDA.ipynb): The objective of EDA notebook is to explore the dataset application_{train|test}.csv, which contains the list of application informations which are capable of repayment or not.

- **Target Variable**: Highly imbalanced distribution between target variable. (92% vs 8%)

<img src ="/CapstoneProject/reports/figures/target.png" width = "500"/>

- **Univariate Analysis**: Discovered employment data anomalies reflecting tenure over 1000 years.


- **Bivariate Analysis**: Among defaulted loans, 93% are cash loans, 70% do not have car ownership, 83% lack higher education, and 25% work as laborers.


## Modeling

[Modeling Notebook](notebooks/Models/modeling.ipynb)

<img src ="/CapstoneProject/reports/figures/modeling 1.png" width = "500"/>
<img src ="/CapstoneProject/reports/figures/modeling 2.png" width = "500"/>



## Final Presentation

[Presentation Slides](https://docs.google.com/presentation/d/17kRmJPFf52FRPcKRbrFky9ByK_sRgah7M09jPqaFZ0s/edit?usp=sharing)

## Takeways from Project

### Assumption

- One row represents one loan application in our data.
- No economic depression or seasonal patterns exist in the data.
- Clients defaulting harms the financial stability of Home Credit. 

### Analytic Findings & Business Actions

- Individuals with longer period of social activities tend to exhibit better credit behavior than those with shorter period of time.
- Among defaulted loans, 93% are cash loans, 70% do not have car ownership, 83% lack higher education, and 25% work as laborers.

### Improvement & Recommendation

- Historical data helps improve the quality of decision somehow, even though preprocessing & cleansing must be preceded to make it a gold.
- Deploying a model monitoring framework that utilizes machine learning operations (MLOps) to ensure models adapt over time, maintaining high accuracy and relevance in a changing market.
- Home Credit has the opportunity to tailor loan offers and outreach strategies to appeal to low-risk customers, including individuals with higher education, homeownership, and a limited number of Credit Bureau inquiries within a year.