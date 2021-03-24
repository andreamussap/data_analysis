# Data Visualization

I've finished the [The Business Intelligence Analyst Course](https://www.udemy.com/course/the-business-intelligence-analyst-course-2018/), and I've created this project to consolidate part of my learnings.

In this project, I'm using the dataset `Absenteeism_predictions.csv`, which was provided by the course, to visualize the probability of employees to be absent from work excessively, that is, for more than 3 hours.

The structure of the dataset is as follows:

* 40 observations
* 11 variables
* 2 columns created by a logistic regression model, as follows:
  * **Probability** - Contains float values, which represent the probability that an individual is expected to be absent from work excessively.
  * **Prediction** - Binary field: `1` if the model predicted that an individual will be excessively absent from work; `0` if not.

## Objective

My idea for this project was to create a tutorial describing the high-level steps that you can follow to create the viz, and then the analysis based on the resulting graphic.

I've embedded links to Tableau documentation throughout the text as a reference to help to explain some concepts.

## Scatter Plot Age vs Probability

Create a [Scatter Plot](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_scatter.htm) to visualize the average probability that an individual of a certain age might be excessively absent from work.

1. Import the dataset in Tableau.
2. Open **Sheet1** and rename it to **Age vs Probability**.
3. Add `Age` to the **View**, and change it from an aggregated measure to [Dimension](https://help.tableau.com/current/pro/desktop/en-us/datafields_typesandroles.htm), so we can see the different groups of ages for which we have data.
4. From the [Marks card](https://help.tableau.com/current/pro/desktop/en-gb/buildmanual_shelves.htm#marks-card), change the mark type to **Shape** to show the graphic as a scatter plot.
5. Add `Probability` to the **View**, and change its measure from **Sum** to **Average**.
6. Right-click the vertical axis, `Avg.Probability`, select **Format > Scale > Numbers** and select **Percentages** with `0` decimal places.
7. Right-click the vertical axis again, select **Edit > Range > Fixed**, and make the range to `0 - 1`.

### Analysis for Age vs Probability

The graph shows multiple observations for every age (26, 28, 30 years old, and so on) for which we have data.

Most of the individuals in this dataset were 40 years old or younger.

The age group with the highest and lowest chance to be excessively absent from work are the **50** age group (`76%`) and the **48** age group (`7%`), respectively.

It doesn't seem that there is a correlation between age and absence from work. For example:

* The **28** age group is the youngest group, and it shows a `51%` probability of being excessively absent from work, whereas the second youngest group, **30**, has only `28%` chance of being excessively absent from work.
* While the probability of the oldest group, **58** age group, to be excessively absent from work is `68%`, the second oldest group, **53**, shows only a `10%` chance of being excessively absent from work.

You can hover-over every dot in the graphic and see the age and the average probability value it corresponds to. For example, the chance of a 31-years-old employee to be absent from work excessively is not too hight, it's `29%`.

![Age vs Probability](/tableau_BIDA/images/ageprobability.png)

You can see the interactive graphic in [my Tableau Public profile](https://tabsoft.co/2OVxq6r).

## Reasons vs Probability

In this exercise we want to analyse if the reasons for absence (variables `reason_1`, `reason_2`, `reason_3`, `reason_4`) can be used to predict whether an individual will be excessively absent from work.

1. Open a new **Sheet** and rename it to **Reasons vs Probability**.
2. Change all measures to dimensions at once. Right-click all variables in the **Measure** section, and select **Convert to dimension**. After that, the fields were all moved to the **Dimensions** section.
3. Drag `Probability` to **Rows**, and change it to [Continuous](https://help.tableau.com/current/pro/desktop/en-gb/datafields_typesandroles.htm#blue-versus-green-fields).
4. From the **Marks card**, change the type of the graphic to **Shape**.
5. Drag the four `reasons` fields to **Columns**.
6. Change these four fields to **Continuous** as well.

    The `reasons` fields are binary fields, which contain values `0` and `1`:

    * `1`: An employee has been absent because of this particular reason.
    * `0`: An employee hasn't been absent because of this particular reason.

    Observing `0` or `1` along the horizontal axis indicates whether an individual has or has not been absent for each particular reason.

    At this point of the exercise, we can see that none of our 40 observations has been away from work because of **Reason 2**. Therefore, this field is not relevant for the analysis, and we can dropt it from the **View**.

    ![Age vs Probability](/tableau_BIDA/images/reasonprobability_R2.png)
7. Remove **Reason 2** field from the **View**.

There are some more information that we can draw out at this stage:

* If an employee is supposed to be absent due to a reason from group **Reason 1**, the probability that they will be excessively absent is above `50%`, and this is the opposite for group **Reason 4**, where the probability of an individual to be excessively absent is below `50%`.
* Looking at group **Reason 3**, we can see very few occurrences of `1`, meaning that very few individuals were absent because of this reason. So, similarly to **Reason 2** this class doesn't seem to be relevant to the analysis.

### Qualitative analysis for classes 1 and 4

To extend our analysis and try to add a qualitative interpretation to the results of classes **Reason 1** and **Reason 4**, we'll need to refer to the [Data Transformation](../python_BIDA#variable-reason-for-absence) part of this project where the diseases were grouped.

We can see that **Reason 1** represents very serious diseases (for example, mental disorders, respiratory issues), so it's expected that people from this class will be absent for long periods, which matches what we see in the graphic, that the probability of people in this group to be excessively absent is higher than `50%`.

The reasoning for **Reason 4** is equivalent: since this is the group of light reasons for absence (for example, physiotherapy, dental consultation), it's expect that people in this group won't be absent for long periods. Therefore, it seems that the model correctly predicted that the probability of individuals in this group to be excessively absent is mostly lower than `50%`.

You can see the interactive graphic in [my Tableau Public profile](https://tabsoft.co/2OVxq6r).

## Transportation Expense and Children

In this exercise We would like to see the probability that a person will be excessively absent from work in relation to the transportation expense they must cover each month, as well as to the number of children they have.

1. Open a new **Sheet** and rename it to **Transportation Expense and Children**.
2. Drag `Probability` to **Rows**, and change its content to **Continuous** values.
3. Select **Shape** from the **Marks** dropdown list, so we can see a scatter plot.
4. Format its numbers to **Percentage** and make its **Range** to `0 - 1`.
5. Drag `Transportation` to **Columns**, and change its content to **Continuous** values.

    At this point, we can infer from the graphic what seems to be a [positive correlation](https://bit.ly/3vRyUPO) between transportation expense and the time that a person is excessively absent from work. We also can see that most of the individuals expend less than USD 240 in transportation.

    ![Transportation Expense](/tableau_BIDA/images/Transp_prob.png)
6. Drag `Children` to **Size** in the **Marks cards**.
    The filter **Children** is shown at the right, and the size of the circles in the graphic change accordingly with the number of children.
7. Drag `Children` to **Color** in the **Marks cards**.

### Qualitative analysis for Transportation Expense and Children

During the steps to build the viz, we've noticed a possible positive correlation between `Transportation expense` and the time that a person is excessively absent from work. After that, we've added the `Children` filter so we can combine the two features to draw out some more insights.

![Transportation Expense and Children](/tableau_BIDA/images/TranspChild_probab.png)

If we filter `Children` by **0**, meaning individuals with no children, we can see that they don't exhibit a high probability of being excessively absent. Moreover, aside from the data point `Expense: 268`, all the other have low transportation expense.

Changing now to individuals with **3** children, the graphic shows just one data point. This doesn't seem representative and relevant for the analysis, so we can exclude it from the visualization.

Next, let's check just individuals with **1** child. The graphic shows that most of the data is clustered around the average transportation spending, between $220 and $240. As for the probability of excessive absence, it varies across the observations. Filtering now just by **2**, we can say that the same conclusion applies.

So, analyzing both groups together, the data shows that most individuals spend less than $240 on transportation, and that the probability of excessive absence varies across the observations.

![Transportation Expense and Children](/tableau_BIDA/images/TranspChild12_probab.png)

You can see the interactive graphic in [my Tableau Public profile](https://tabsoft.co/3lJZDJk).
