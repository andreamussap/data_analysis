# Data Transformation

I've finished the [The Business Intelligence Analyst Course](https://www.udemy.com/course/the-business-intelligence-analyst-course-2018/), and I've created this project to consolidate my learnings.

## Objective

The main goal of this project is to use my learnings in [pandas](https://pandas.pydata.org/), a Python Data Analysis library, to create an end-to-end script, which can be used to apply transformations to a dataset.

## Out of Scope

This is *not* a Data Science project, this is a Data Engineering project instead.

## Tools

I've used the following tooling in this project:

* Anaconda Navigator 1.10.0
* Python 3.7
* Python's library `pandas`
* Jupyter notebook 6.1.4

### Jupyter notebook

This was the first time I've used Jupyter notebook, and I've found it quite straightforward. Specially when you know Markdown already you can write markup tags along with your `code` to describe your work more beautifully.

## Dataset

The original `Absenteeism at work.csv` dataset is available from the [UCI Machine Learning Repository, Absenteeism at work Data Set](https://archive.ics.uci.edu/ml/datasets/Absenteeism+at+work). My course, however, has provided the dataset with some modifications, which were fit for the lessons.

## Activities

The main activities in this project are the exploratory data analysis (EDA) and the actual transformation of the dataset.

### 1. Exploratory Data Analysis (EDA)

I've started with an EDA of the data to try to identify obvious errors, missing values, outliers, find relations among the variables, and try to come up with some earlier assumptions.

### 2. Data Transformation

I've performed transformations, such as:

* Drop variables
* Add variables
* Concat variables
* Reorder columns
* Rename columns
* Separate the data into categories

## Variable Reason for Absence

The transformation of variable `Reason for Absence` was an interesting task because we've learnt how to work with [dummy variables](https://www.jigsawacademy.com/blogs/data-science/dummy-variable-trap/). We looked at the list of reasons for absence with a qualitative analysis focus, and we've grouped the 28 reasons in four classes.

* Group 1 - reasons 1-14. They're all related to various serious diseases.
* Group 2 - reasons 15-17. Reasons related to to pregnancy and giving birth.
* Group 3 - reasons 18-21. About poisoning or other reasons not  elsewhere categorized.
* Group 4 - reasons 22 to the end. Categorized as light reasons.

We did this because the values in `Reason for absence` represent categories, but in further lessons, we will make a quantitative analysis with this column. So, we needed to add a numerical meaning to this variable.

To accomplish that, we've created a temporary data frame, `reason_columns`, and we've used the `.get_dummies()` [panda's method](https://pandas.pydata.org/pandas-docs/version/1.0.3/reference/api/pandas.get_dummies.html) to create the dummy variables.

Then, from the `reason_columns` df, we created the four classes, or groups. And finally, we [concatenated](https://pandas.pydata.org/docs/user_guide/merging.html#concatenating-objects) the four new columns to our data frame, and we dropped the original `Reason for absence` column.

### Multicollinearity

When we created the `reason_columns` data frame with the dummy variables we've used the `drop_first` panda's option to avoid multicollinearity.

Although multicollinearity is out of the scope of the course, I did some research on my own and here my understanding about it:

*Multicollinearity occurs when independent variables are correlated (Note: all 28 variables (reasons for absence) are independent one from another), and it affects the result of the regression analysis, causing the results of its tests to be misleading. To avoid this problem, also known as 'dummy variable trap', we must create K-1 dummy variables, being K the amount of categorical variables we have.*

## Resources

The following are the resources available in this project:

* **absenteeism_final_project.ipynb** - The notebook with code for the transformations.
* **dataset_raw/Absenteeism_data.csv** - Dataset used in this exercise.
