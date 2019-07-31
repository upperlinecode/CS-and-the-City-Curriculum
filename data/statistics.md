# Statistics

## Learning Objectives

* SWBAT use statistical measurements (mean, median, mode, variance, quartiles) to interpret data.

## Sequence

1. [Intro](#intro)
2. [Mean, Median, Mode, Range](#mean-median-mode-range)
3. [Variance](#variance)
4. [Quartiles](#quartiles)
5. [Other Statistical Descriptions](#other-statistical-descriptions)
6. [Close](#close)

## Launch

Make a copy of the [NYC Subway Customer Journey Time Performance](https://docs.google.com/spreadsheets/d/1uSd7IMLpnMWYM0zrJJZLdXc_yVAD-dK62XRNRLl7U0Y/edit?usp=sharing) Google Sheet (Source: [dashboard.mta.info](http://dashboard.mta.info/))

> Note: This data considers end-to-end trips and any delays caused by the MTA. The data represents the percent of successful trips each month; a successful trip is defined as a traveler who arrives within 5 minutes of the expected trip duration (according to the MTA).

Explore the raw data in the "Customer Journey Time Performan" sheet. Answer as many of the following questions as you can based on the raw data:
- Which line has the best performance during peak times? during off-peak times?
- Which line has the worst performance during peak times? during off-peak times?
- Which line has had the broadest range of performance during peak times? during off-peak times?
- Which line has had the narrowest range of performance during peak times? during off-peak times?
- Which non-shuttle line, on average, is the best during peak times? during off-peak times?
- Across all lines, how often does a rider get to their destination within 5 minutes of their anticipated travel time during peak times? during off-peak times?
- For the 6, how often does a rider get to their destination within 5 minutes of their anticipated travel time during peak times? during off-peak times?

Did you find it difficult/frustrating/impossible to answer any of those questions? It's ok if you did. We're going to aggregate and manipulate the data so that we can begin to answer all of those questions.

## Mean, Median, Mode, and Range

You probably have already learned about mean (the average), median (the middle number), mode (the number occurring most often), and range (the max minus the min) in math class, so we won't cover those here. Instead, we're going to use those statistical measurements in Google Sheets to get a sense of our data.

First of all, when you have a set of data, you can quickly calculate each measurement in Google Sheets using a formula:

#### Mean
```
=AVERAGE(A:A) # calculates the mean of everything in column A
=AVERAGE(B2:B5) # calculates the mean of the values in the cells B2, B3, B4, B5
```

#### Median
```
=MEDIAN(A:A) # calculates the median of everything in column A
=MEDIAN(B2:B5) # calculates the median of the values in the cells B2, B3, B4, B5
```

#### Mode
```
=MODE(A:A) # calculates the mode of everything in column A
=MODE(B2:B5) # calculates the mode of the values in the cells B2, B3, B4, B5
```

#### Range
```
=MAX(A:A)-MIN(A:A) # calculates the range of everything in column A
=MAX(B2:B5)-MIN(B2:B5) # calculates the range of the values in the cells B2, B3, B4, B5
```




- revise with [Countdown clock data](https://toddwschneider.com/posts/nyc-subway-data-analysis/)
- [How 2 MTA Decisions pushed the subway to crisis](https://www.nytimes.com/interactive/2018/05/09/nyregion/subway-crisis-mta-decisions-signals-rules.html) - NY Times
- [How your commute has changed: NYC subway variability calculator](https://www.nytimes.com/interactive/2019/07/08/upshot/nyc-subway-variability-calculator.html?mtrref=www.google.com)

You may remember from previous math classes where you've been taught how to calculate the mean, median, and mode of a set of numbers. The focus of this lesson is not on the mathematics of how to do those calculations (and others), but instead on what those numbers represent. This less will give you a better understanding of how useful statistical measurements can be and how to ask whether or not they're the right way to summarize a set of data. 

## Mean, Median, Mode, Range

#### Review on calculations

Recall how to calculate these statistical values:

- Mean (also called the average): to calculate the mean, we add up all of the values in a set of data and then divide by the number of values in the set.
- Median: to calculate the median, we arrange all of the values in increasing order and count to the middle number.
- Mode: to calculate the mode, we arrange all of the values in increasing order and identify which value occurs most often.
- Range: to calculate the range, we subtract the smallest value in the dataset from the largest value.

#### Example

Consider a dataset of exam scores: [100, 86, 90, 93, 75, 40, 66, 98, 90, 79, 88]

- The mean is: (100 + 86 + 90 + 93 + 75 + 40 + 66 + 98 + 90 + 79 + 88)/11 = (905)/11 = 82.27
- Rearranging the values in increasing order: [40, 66, 75, 79, 86, 88, 90, 90, 93, 98, 100]
	- There are 11 total values, so the median is the 6th value: 86
	- The mode is the value that occurs most often: 90
	- The range is the largest value (100) minus the smallest value (40): 60

Think about why computers are particularly good at calculating the mean, median, mode, and range. Could you write a function that would calculate each statistical measurement?

### Understanding Distributions

You've probably been able to calculate the mean, median, mode, and range of a set of values using your calculator or even a computer, but what happens when the number of values in the data set goes from 11 (above) to 11 million? Do you think these statistical measurements are as meaningful?

Instead of boiling down 11 million numbers to one of these four statistical values, data scientists will often instead prefer to look at the distribution of the values to get a better sense of the data. Distributions are difficult to calculate by hand, but they are a graphical way to know whether the values in a data set are evenly spread around some central value, whether there are more greater values or lesser values (whether the data is skewed), or even whether the data is composed of multiple features that might be grouped around particular values. Distributions can be represented as column (bar) charts or line charts; column charts are used when there is a relatively small number of possible discrete values in the dataset, and line charts either to approximate many many more discrete values or when the data is continuous. In each case, the x-axis represents the value and the y-axis represents the number of times that value is in the data set, or that value's frequency.

Some distributions are bell-shaped; you may have heard of a Bell curve. Other distributions are shifted one way or another, e.g. a Boltzmann distribution. Still others have more than one hump; a distribution with two humps is called "bimodal". Other distributions may have values that are evenly distributed, and those are called "uniform" distributions.

Let's take the skewed-left distribution below. Visually, the mode is the easiest statistical measurement to determine from a graph; it's the high point because that represents the value that occurs most often in the data. The mean and median are a bit trickier and generally depend on the shape of the distribution. For the skewed-left distribution below, the value of the median is a bit higher than the value of the mode; to visually determine the median, imagine drawing a line that has equal area on the left and the right sides of the line. Lastly, the value of the mean is a bit higher than the value of the median because the few larger values have the effect of pulling the mean up relative to the median.

_Note: the range is a less relevant measurement when a distribution has a very long tail on either side (or both) since it can be difficult to determine a maximum and minimum value.

![Skewed Left Distribution](./images/mean-median-mode-on-skewed-right-curve.png)

Consider the distributions below:

#### Bell-Shaped Distribution
![Normal Distribution](./images/bell-shaped-histogram.jpg)

#### Skewed Left Distribution
![Skewed Left Distribution](./images/skewed-left-histogram.jpg)

#### Skewed Right Distribution
![Skewed Right Distribution](./images/skewed-right-histogram.jpg)

#### Bimodal Distribution
![Bimodal Distribution](./images/bimodal-histogram.jpg)

#### Uniform Distribution
![Uniform Distribution](./images/uniform-histogram.jpg)

For each distribution, can you guess-timate (guess + estimate):
- What is the value of the mode of each dataset?
- What is the value of the median of each dataset?
- What is the value of the mean of each dataset?
- What is the value of the range of each dataset?

Now consider these three datasets represented below by the bold, thin, and dotted lines:

![Uniform Distribution](./images/overlapping-normal-distributions.png)

For each distribution, can you guess-timate:
- What is the value of the mode of each dataset?
- What is the value of the median of each dataset?
- What is the value of the mean of each dataset?

As you can see, unfortunately just determining the mean, median, and mode is not sufficient to distinguish between these three datasets. For that, we need a new measurement: the variance.

## Variance

Without going too deep into the mathematics about distributions, you have seen (above) how some datasets look more spread out than others. The more spread out the values in a dataset are, the larger the variance of the dataset. The more closely aligned the values in a dataset are, the smaller the variance of the dataset.

Variance helps a data scientist gauge how uniform or distributed the values in a dataset are.

See if you can arrange the following datasets in terms of increasing variance. What conditions must be true in order to visually compare various datasets?

<table>
	<tr>
		<td><img src="./images/normal-1.png"></td>
		<td><img src="./images/normal-2.png"></td>
	</tr>
	<tr>
		<td align="center"><b>Distribution 1</b></td>
		<td align="center"><b>Distribution 2</b></td>
	</tr>
	<tr>
		<td><img src="./images/normal-3.png"></td>
		<td><img src="./images/normal-4.png"></td>
	</tr>
	<tr>
		<td align="center"><b>Distribution 3</b></td>
		<td align="center"><b>Distribution 4</b></td>
	</tr>
</table>

### Activity: Real-World Variance

Some text here

## Quartiles

We can build upon our understanding of variance and begin to quantify the shapes of distributions using quartiles. Quartiles are a way to dissect a distribution by splitting the data into four chunks where each chunk of the dataset has the same number of values within it.

How can you do that? We already know how to split a dataset into two equal chunks: that's the median. So to split a dataset into quartiles, you first find the median of a dataset, and then you find the median of each half. Doing this defines the boundaries of each quartile:

- The first quarter ranges from the minimum value in the dataset up to the median of the first half of the dataset (the first quartile).
- The second quarter ranges from the median of the first half of the dataset (the first quartile) up to the median of the whole dataset (the middle quartile).
- The third quarter ranges from the median of the whole dataset (the middle quartile) up to the median of the second half of the dataset (the third quartile).
- The fourth quarter ranges from the median of the second half (the third quartile) of the dataset up to the maximum value in the dataset.

### Activity: Dividing into Quartiles

Dissect each of the following datasets into quarters. What are the values of the first, second, and third quartiles?

- [10, 10, 11, 13, 16, 16, 18, 20]
- [1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 5, 5, 5, 5, 6, 6, 6, 7, 7, 7, 7, 8, 8, 9, 9, 9, 9, 9, 10]
- [-5, -5, -4, -4, -4, -3, -3, -2, -2, -1, -1, -1, -1, -1, 0, 0, 0, 0, 2, 4, 4, 4, 5]
- [6, 3, 4, 7, 2, 0, 0, 7, 6, 5, 3, 2, 1, 1, 3, 6, 7, 9, 0, 9, 5, 5, 4, 3, 2, 5, 4, 3, 2, 7, 6, 8, 5, 3, 4]

### Activity: Other Statistical Descriptions

So far we've learned a number of statistical measurements that enable a data scientist to better understand how large datasets are distributed:

- Mode
- Median
- Mean
- Variance
- Quartiles

There are many other statistical measurements used by data scientists, each of which has its own method of calculation and contextual meaning. Investigate one or more of the measurements below, and share what you find with a partner. In what circumstances is that measurement used? And how does it relate to what you've already learned?

- Root-Mean-Squared Average
- Standard Deviation
- Poisson Distribution
- Boltzmann Distribution
- Binomial Distribution
- Exponential Distribution
- [Other Probability Distributions](https://en.wikipedia.org/wiki/List_of_probability_distributions)

## Close

Statistics is an entire field of mathematics devoted to making sense of sets of values, and new measurements are necessary as the number of values increases dramatically.

In the next lesson, we'll learn how to use various tools to better understand complex numerical and non-numerical datasets.
