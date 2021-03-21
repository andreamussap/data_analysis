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

## Scatter Plot Age vs Probability

Create a [Scatter Plot](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_scatter.htm) to visualize the average probability that an individual of a certain age might be excessively absent from work.

### Steps for Age vs Probability

1. Import the dataset in Tableau.
2. Open **Sheet1** and rename it to **Age vs Probability**.
3. Add `Age` to the **View**, and change it from an aggregated measure to [Dimension](https://help.tableau.com/current/pro/desktop/en-us/datafields_typesandroles.htm), so we can see the different ages for which we have data.
4. From the [Marks card](https://help.tableau.com/current/pro/desktop/en-gb/buildmanual_shelves.htm#marks-card), change the mark type to **Shape** to show the graphic as a scatter plot.
5. Add `Probability` to the **View**, and change its measure from **Sum** to **Average**.
6. **Format** the `Avg.Probability` axis to show the results as percentages, and **Edit** its range to `0 - 1`.

### Analysis for Age vs Probability

The graph shows multiple observations for every age (26, 28, 30 years old, and so on) for which we have data.

Most of the individuals in this dataset were 40 years old or younger.

The age group with the highest and lowest chance to be excessively absent from work are the **50** age group (`76%`) and the **48** age group (`7%`), respectively.

It doesn't seem that there is a correlation between age and absence from work. For example:

* The **28** age group is the youngest group, and it shows a `51%` probability of being excessively absent from work, whereas the second youngest group, **30**, has only `28%` chance of being excessively absent from work.
* While the probability of the oldest group, **58** age group, to be excessively absent from work is `68%`, the second oldest group, **53**, shows only a `10%` chance of being excessively absent from work.

You can hover-over every dot in the graphic and see the age and the average probability value it corresponds to. For example, the chance of a 31-years-old employee to be absent from work excessively is not too hight, it's `29%`.

![Age vs Probability](/tableau_BIDA/images/ageprobability.png)

### Link to Age vs Probability graphic

This is the directly link to the graphic in my Tableau Public profile -

<https://public.tableau.com/profile/andrea.mussap#!/vizhome/AbsenteeismFromWork/AgevsProbability>

## Reasons vs Probability

In this exercise we want to analyse if the reasons for absence (variables `reason_1`, `reason_2`, `reason_3`, `reason_4`) can be used to predict whether an individual will be excessively absent from work.

For the purpose of our analysis, we're going to need the data as **Dimensions**, so we've stated the exercise by changing all of them at once.

### Steps for Reasons vs Probability

1. Open a new **Sheet** and rename it to **Reasons vs Probability**.
2. Change all measures to dimensions at once. Right-click all variables (from **Age** to **Transportation Expense**) in the **Measure** section, and select **Convert to dimension**. After that, the fields were all moved to the **Dimensions** section.
3. Drag `Probability` to **Rows**, and change it to [Continuous](https://help.tableau.com/current/pro/desktop/en-gb/datafields_typesandroles.htm#blue-versus-green-fields).
4. From the **Marks card**, change the type of the graphic to **Shape**.
5. Drag the 4 `reasons` fields to **Columns**.
6. Change these 4 fields to **Continuous** as well.

    The `reasons` fields contain values with `0` and `1`:

    * `1`: An employee has been absent because of this particular reason.
    * `0`: An employee hasn't been absent because of this particular reason.

    Observing `0` or `1` along the horizontal axis indicates whether an individual has or has not been absent for each particular reason.

    At this point of the exercise, we can see that none of our 40 observations has been away from work because of **Reason 2**. Therefore, this field is not relevant for the analysis, and we can dropt it from the **View**.

    ![Age vs Probability](/tableau_BIDA/images/reasonprobability_R2.png)
7. Remove **Reason 2** field from the **View**.
    Another finding that we can see at this stage is that, if an employee is supposed to be absent due to a reason from group **Reason 1**, the probability that they will be excessively absent is above `50%`, and this is the complete opposite for group **Reason 4**, where the probability of an individual to be excessively absent is below `50%`.

    Looking at group **Reason 3**...
*This file is under development*
