(this is a holding pen for extra content)

# Intro to Data Science

## What is "Data Science"?

If you've been tuned into the news, the job market, or even just looking at ads on the subway recently, you've probably come across the term "data science". Colleges and universities are offering degrees in data science, businesses are using data science to out-perform each other, and even the government at all levels (borough, city, state, federal, international) is using data science to make data-driven decisions.

But what is "data science"?

![Data Science Cartoon](./images/data-science.png)

**Data science** is an umbrella term that draws upon a number of fields including mathematics, statistics, computer science, and even sociology, journalism, and design. Depending on how the term is being used, it could mean anything from statistics to machine learning and artificial intelligence.

What distinguishes the different meanings of "data science" is really a question of what you're trying to do with data:

- Are you trying to better understand the data that you have? (That's **analytics**.)
- Are you trying to make decisions based upon the data you have? (That's probably **statistics**.)
- Do you have a lot of complex data and are trying to make sense of it? (That's **machine learning**.)

Data science as a field is put into practice depending on what you want to do with data:

- **Description**: You want to understand the data you have. _e.g. Subway trains arrive late to the station 24% of the time._
- **Prediction**: You want to guess what's going to happen in the future. _e.g. Next week, ridership will increase across the subway system by 9%._
- **Prescription**: You want to say what should be done as a result of your prediction about the future. _e.g. In order to meet the anticipated increase in demand, the MTA should add 3 trains per line per hour from 7am to 7pm._

## Optional Activity: Three Questions

Think about something you do most days. Maybe you ride the subway, maybe you go shopping, maybe you check social media, maybe you spend time with your family, maybe you go to the movies. See if you can come up with three questions you could investigate about that activity:

* The first question should be **descriptive** - the answer to this question should just describe the activity. _e.g. What percentage of my time do I spend playing video games every week?_
* The second question should be **predictive** - the answer to this question is related to some future state of the activity. _e.g. How much time can I expect to spend playing games next month?_
* The third question should be **prescriptive** - the answer to this question should recommend an action based on the answer to a prediction. _e.g. What other activities should I do instead of playing video games so often?_

#### Additional Reading on Data in Journalism

Explore these resources to see how journalists are talking about - and using - data.

- [WNYC Data News](https://www.wnyc.org/tags/data_news)
- [ProPublica](https://www.propublica.org/)

#### Additional Readings on Civic Data

These readings introduce the concept of civic data, and how cities are collecting an increasing amount of data about residents, municipal activities (housing, crime, transportation, etc.), and more.

- ["The City of the Future Is a Data-Collection Machine" (The Atlantic, Nov 21, 2018)](https://www.theatlantic.com/technology/archive/2018/11/google-sidewalk-labs/575551/)
- ["On Being a Civic Data Scientist" (Medium, Aug 11, 2017)](https://towardsdatascience.com/on-being-a-civic-data-scientist-774c15232695)
- ["History of NYC's open data" (Data-Smart City Solutions, Mar. 8, 2017)](https://datasmart.ash.harvard.edu/news/article/new-york-city-open-data-a-brief-history-991)
- [How City Council uses open data to create legislation (YouTube)](https://www.youtube.com/watch?v=mrVevDEFan8&list=PLgCe1KzF20iwjeJDnI4l9OxDZKEsA6R6l&index=4) (video)

## Activity: Types of Data

See how many types of data you can brainstorm in 5 minutes. For each type, also consider potential sources of that data.

_For example, geographic data might come from satellites, from locations of users on their smartphones, from city zoning data, etc._

> Note: Think broadly! Try to consider various types of quantitative (numerical), qualitiative (textual), and alternative (images, video, sound, etc.) data. You might also think about less traditional sources of data like anecdotal data, case studies, and/or aggregate data.

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