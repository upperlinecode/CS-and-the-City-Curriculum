# Surviving the Titanic

![RMS Titanic](./images/titanic.png)

## Setup

In this lab, you'll explore historical data about passengers on the _RMS Titanic_. Your goal is to determine the factor(s) that led to passengers' survival (or death).

- Make a copy of the <a href="https://docs.google.com/spreadsheets/d/17PncyppLXjKyGZFgcSfgkWIulJ-rsZv2suqQ_bsSKE4/edit?usp=sharing" target="_blank_">Titanic Data Google Sheet</a>

> The file contains a `README` sheet with definitions for the variables. Consult the `README` for abbreviations (e.g. C, Q, S) and Booleans (survival: 0 = No, 1 = Yes).

## Predictions

You've probably heard the expressions "Women and children first!" and "A captain always goes down with the ship!", but are these things actually true? In addition to whether or not a passenger survived, the data will also tell us information like each passenger's sex, their age, the size of their party/group/family, and how much money they paid for their ticket. Before you look at the data too closely, what do you predict?

1. Did most women survive? Did they fare better than men?
2. Did most children survive? Did they fare better than the adults?
3. Did wealthy passengers fare better than passengers who paid less for their tickets?
4. Which demographic do you think had the highest survival rate? (e.g. Old, poor men? Young wealthy women?)
5. Which demographic do you think had a the lowest survival rate?

## Questions

1. Using the Filter view of the data, who were the oldest and youngest recorded passengers on the _Titanic_? What was the cost of each of their tickets? and from which port did they leave?
2. Using the Filter view of the data, list the members of the biggest family on the voyage. (Hint: use the `SibSp` and `ParCh` counts.)
3. In what cabin(s) did the passengers stay who had paid the highest fare? How much did they pay? and from which port did they leave?
4. Use a Pivot Table to count how many passengers survived vs. died on the _Titanic_. Is there anything surprising about the result?
5. Use a Pivot Table to count how many passengers left from each of the ports of embarkation. Where did the majority of passengers get onto the _Titanic_?
6. Use a Pivot Table to count how many passengers from each port of embarkation survived vs. died. Describe any pattern(s) you see in the result.
7. Modify your Pivot Table to count how many passengers from each class survived vs. died. How does this result confirm or contradict your intuition?
8.  What was the average age for a _Titanic_ survivor as compared to a _Titanic_ victim? The maximum ages? The minimum ages? What do those results indicate?
9. What was the average fare for a _Titanic_ survivor as compared to a _Titanic_ victim? What does the result indicate?
10. Based on the data, what factors had the greatest impact on whether or not a passenger survived the _Titanic_? Which factors correlate with others vs. which factors are independent?
