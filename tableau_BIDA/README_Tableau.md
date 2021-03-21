# Udemy course - Data Visualization

I've finished the [The Business Intelligence Analyst Course](https://www.udemy.com/course/the-business-intelligence-analyst-course-2018/), and I've created this project to consolidate part of my learnings.

In this project, I'm using the dataset `Absenteeism_predictions.csv`, which was provided by the course, to visualize the probability of employees to be absent from work excessively, that is, for more than 3 hours.

The structure of the dataset is as follows:

* 40 observations
* 11 variables
* 2 columns created by a logistic regression model, as follows:
  * **Probability** - Contains float values, which represent the probability that an individual is expected to be absent from work excessively.
  * **Prediction** - Binary field: `1` if the model predicted that an individual will be excessively absent from work; `0` if not.

For each visualization, I'm going to describe the high-level steps I've performed to create the viz, and some analysis from the result.

I've embedded links to Tableau documentation throughout the text as a reference to help to explain some concepts.

## Scatter Plot Age Vs Probability

Created a [Scatter Plot](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_scatter.htm) to visualize the average probability that an individual of a certain age might be excessively absent from work

### Steps for Age Vs Probability

1. Import the dataset in Tableau.
2. Open **Sheet1** and rename it to **Age Vs Probability**.
3. Add `Age` to the **View**, and change it from an aggregated measure to [Dimension](https://help.tableau.com/current/pro/desktop/en-us/datafields_typesandroles.htm), so we can see the different ages for which we have data.
4. From the [Marks card](https://help.tableau.com/current/pro/desktop/en-gb/buildmanual_shelves.htm#marks-card), change the mark type to **Shape** to show the graphic as a scatter plot.
5. Add `Probability` to the **View**, and change its measure from **Sum** to **Average**.
6. **Format** the `Avg.Probability` axis to show the results as percentages, and **Edit** its range to `0 - 1`.

### Analysis for Age Vs Probability

The graph shows multiple observations for every age (26, 28, 30, and so on) for which we have data.

Most of the individuals in this dataset were 40 years old or younger.

The age group with the highest and lowest chance to be excessively absent from work are the **50** age group (`76%`) and the **48** age group (`7%`) respectively.

It doesn't seem that there is a correlation between age and absence from work. For example:

* The **28** age group is the youngest group, and it shows a `51%` probability of being excessively absent from work, whereas the second youngest group, **30**, has only `28%` chance of being excessively absent from work.
* While the probability of the oldest group, **58** age group, to be excessively absent from work is `68%`, the second oldest group, **53**, shows only a `10%` chance of being excessively absent from work.

You can hover-over every dot and see the age and the average probability value it corresponds to. For example, the chance of an employee, who is 31-years-old, to be absent from work excessively is not too hight, it's `29%`.

![Age Vs Probability](/images/Data_learningpathH1000_202103.png)

### Link to Age Vs Probability graphic

This is the directly link to the graphic in my Tableau Public profile -

<https://public.tableau.com/profile/andrea.mussap#!/vizhome/AbsenteeismFromWork/AgeVsProbability>
