# Data In Argument & Decision Making

## Learning Objectives

* SWBAT explore data used in news and in rhetoric.
* SWBAT differentate between data and information.
* SWBAT recognize how data can be used to control human behavior.
* SWBAT differentiate kinds of data and different uses for data.

## Sequence

1. [Intro to Data Science](#intro-to-data-science)
2. [The Misuse of Data](#the-misuse-of-data)
3. [Data Literacy](#data-literacy)
4. [Close](#close)

## Intro to Data Science

### What is "Data Science"?

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

### Optional Activity: Three Questions

Think about something you do most days. Maybe you ride the subway, maybe you go shopping, maybe you check social media, maybe you spend time with your family, maybe you go to the movies. See if you can come up with three questions you could investigate about that activity:

* The first question should be **descriptive** - the answer to this question should just describe the activity. _e.g. What percentage of my time do I spend playing video games every week?_
* The second question should be **predictive** - the answer to this question is related to some future state of the activity. _e.g. How much time can I expect to spend playing games next month?_
* The third question should be **prescriptive** - the answer to this question should recommend an action based on the answer to a prediction. _e.g. What other activities should I do instead of playing video games so often?_

#### Additional Reading

Explore these resources to see how journalists are talking about - and using - data.

- [WNYC Data News](https://www.wnyc.org/tags/data_news)
- [ProPublica](https://www.propublica.org/)

### Data vs. Information

When you've talked about data in the past, you may have used the words **data** and **information** interchangeably. Although they are quite similar, these two words have an important distinction:

- **Data** is comprised of the raw measurements, observations, or responses that would be collected from tools like feedback surveys, mechanical sensors, or even digital logs. Data can also be simple facts and figures that result from those raw measurements.
- **Information** is data that has been processed, interpreted, organized, structured or presented in a way that makes the data meaningful or useful. Information carries with it a point-of-view or an opinion because a human has made decisions about its meaning.

In addition to **data** and **information**, the term **insight** often accompanies a discussion about data. **Insight** is the understanding we get from data and information and usually relates to the decision-making capabilities that result from processing data into information.

#### Additional Reading

These readings introduce the concept of civic data, and how cities are collecting an increasing amount of data about residents, municipal activities (housing, crime, transportation, etc.), and more.

- ["The City of the Future Is a Data-Collection Machine" (The Atlantic, Nov 21, 2018)](https://www.theatlantic.com/technology/archive/2018/11/google-sidewalk-labs/575551/)
- ["On Being a Civic Data Scientist" (Medium, Aug 11, 2017)](https://towardsdatascience.com/on-being-a-civic-data-scientist-774c15232695)
- ["History of NYC's open data" (Data-Smart City Solutions, Mar. 8, 2017)](https://datasmart.ash.harvard.edu/news/article/new-york-city-open-data-a-brief-history-991)
- [How City Council uses open data to create legislation (YouTube)](https://www.youtube.com/watch?v=mrVevDEFan8&list=PLgCe1KzF20iwjeJDnI4l9OxDZKEsA6R6l&index=4) (video)

## The Misuse of Data

Data does not exist in a neutral vacuum. Throughout history, data has been used both positively and negatively. At its worst, data has been a justification for discrimination ([GI Bill and black WWII veterans](https://www.history.com/news/gi-bill-black-wwii-veterans-benefits)), a means by which to forcibly separate people ([WWII internment of Japanese Americans](https://www.washingtonpost.com/news/retropolis/wp/2018/04/03/secret-use-of-census-info-helped-send-japanese-americans-to-internment-camps-in-wwii/?noredirect=on&utm_term=.f5e994f73a5d)), and a basis for all sorts of racist, sexist, xenophobic, and classist ills. Still today we see data being used to justify humanitarian crises around the world.

The [intentional disregard of data](https://www.washingtonpost.com/opinions/unauthorized-immigrants-are-overwhelmingly-law-abiding-but-it-wont-stop-trump/2019/06/02/5f4f696a-8193-11e9-bce7-40b4105f7ca0_story.html) poses a threat equal to the use of data for nefarious purposes, especially when that disregard is coupled with political or business interests. Perhaps the critical issue of our time where data has been misused by being _unused_ is climate change. Despite scientific consensus about the correlation between atmospheric carbon dioxide concentration and global temperature, politicians continue to ignore and deny the data, its interpretation, and its effects upon our planet.

#### How can data be misused?

Below are several ways data can be (or has been) misused. Can you think of any others?

- Data can be ignored. (see climate change example above)
- Data can be selectively filtered to support an argument. By not including all available data, a conclusion can be skewed in favor of a pre-determined outcome.
- Data can be used to round up, segregate, or otherwise disenfranchise a group of people. Census data is often cited as a means by which the government can assert control over specific sub-groups of the population.
- Data can be mis-interpreted. Too often the public lacks the skills to interpret data for themselves, so people accept the interpretation they are provided.
- Data can be used to violate privacy. Even though data providers claim data has been anonymized, sometimes there is still enough to find out exactly who someone is.

#### A Simple Case Study

Imagine a bank that is trying to decide whether or not to give someone a loan. In addition to deciding whether or not to grant a loan, the bank can also set the interest rate at which the customer should pay back the loan.

In order to make the loan application easier, the bank has made an app for smart phones through which the application is filled out. Once the app has been installed on a user's phone, the app also requests access to the user's music libraries (iTunes, Spotify, Pandora, etc.). The bank knows that most users will not read the fine print in the Terms & Conditions of their app, and since most users will just want to get a loan, they'll agree to whatever the bank wants them to.

**Can you think of ways data about a user's music listening might impact the decisions a bank would make about a loan?** Take a moment to brainstorm with a partner.

Do you think the bank could tell what sex, race, or class a user is just by the music they listen to? Maybe they would think the user is _probably_ Dominican if they listen to bachata; maybe they would think the user is _probably_ black if they listen to particular artists; maybe they would think the user is _probably_ wealthy if they listen to a lot of classical music. Accessing a user's music listening history might indicate information about the user that the bank couldn't otherwise ask in order to discriminate against loan applicants.

- What other data exists on your phone that might be misused to violate your privacy?

#### Additional information

These videos detail innovations in anti-discrimination technology:

- [Discrimination innovation 2018](https://www.youtube.com/watch?v=dSeCV5Tad7I&list=PLgCe1KzF20ix9S_6L41iCChJDv20MX4fu&index=16) (video)
- [Discrimination innovation 2017](https://www.youtube.com/watch?v=9U1Ka5DJXTU&list=PLgCe1KzF20ixjsDCjbyFMgdgwv_3yBHmf&index=17) (video)

### "Fake News"

The rise of partisan journalism has led to claims of "fake news" throughout the socio-political spectrum. "Fake news" has permeated elections, has destroyed careers, and is too-often used to deny any story someone disagrees with, whether the story is based in fact or not. But in reality, "fake news" is a symptom of the metrics by which **user engagement** is measured: clicks, views, and shares.

As information has become commoditized, the techniques used by content-providers, marketers, and media outlets have been co-opted to guide users to tantalizingly wrong information. The headline writing style made popular by websites like Upworthy - "You're not going to believe what happened next..." - which, once recognized as immensely effective at driving people to click and engage, was then used to sensationalize and polarize people's beliefs.

### Optional Activity: Identifying "Fake News"

How can you distinguish real news from "fake news"?

Take a few minutes to consider how you can tell whether a news story is real or "fake". Write down at least 5 questions you would use to interrogate any news story and how the answers to those questions might lead you to label the story as real or "fake".

Find a news article online from a satirical news outlet such as [The Onion](https://www.theonion.com/), [The Daily Mash](https://www.thedailymash.co.uk/), [The Borowitz Report](https://www.newyorker.com/humor/borowitz-report), [Private Eye](https://www.private-eye.co.uk/), or [ClickHole](https://www.clickhole.com/).

Use your 5 questions to decide whether the news story is real or "fake". How well did your questions do at identifying "fake news"?

#### Additional Reading

- ["The Misinformation Age" (PBS, Apr 22, 2019)](https://www.pbs.org/video/the-misinformation-age-0xqnez/)
- [PBS Newshour: Stories on "Misinformation"](https://www.pbs.org/newshour/search-results?q=misinformation)
- ["Who, what, when, where, why do hyperpartisan news sites exist?" (PBS Newshour)](https://www.pbs.org/newshour/extra/daily-videos/who-what-when-where-why-do-hyperpartisan-news-sites-exist/)
- [Lesson plan: How teens deal with the spread of misinformation](https://www.pbs.org/newshour/extra/lessons-plans/lesson-plan-student-reporting-labs-explores-how-youth-deal-with-misinformation/)
- [PBS Newshour: Tag: "Fake news"](https://www.pbs.org/newshour/extra/tag/fake-news/)

## Data Literacy

As you continue to grapple with distinguishing real news from "fake news", you'll realize that you're building an intuition for how to read and understand data. That data might be numerical, but it also might be textual, contextual, or even visual. The ability to digest and synthesize information is core to what is known as "data literacy". Data literacy also includes the ability to critique data and information as well as a visual acuity to interpret data-based graphics such as data visualizations.

- Why should data literacy matter to you?
- How will data literacy help you better judge arguments?
- Who do you think ought to be "data literate"? Why?
- How can data literacy help you protect yourself online?

#### Additional Reading

- [The Firefox Data Privacy Promise](https://blog.mozilla.org/firefox/firefox-data-privacy-promise/)

### Activity: Types of Data

See how many types of data you can brainstorm in 5 minutes. For each type, also consider potential sources of that data.

_For example, geographic data might come from satellites, from locations of users on their smartphones, from city zoning data, etc._

> Note: Think broadly! Try to consider various types of quantitative (numerical), qualitiative (textual), and alternative (images, video, sound, etc.) data. You might also think about less traditional sources of data like anecdotal data, case studies, and/or aggregate data.

## Close

We've seen a lot about how data is all around us and how that data can be used and misused. Next time we'll dig into how bias affects data science:

- decisions about what data we collect
- interpretation of data and information creation
- communication of analytical results
- possible actions to take resulting from analysis
