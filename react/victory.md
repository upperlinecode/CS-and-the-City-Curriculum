# Victory

## Learning Objectives

- SWBAT consult developer documentation to get started with a new library
- SWBAT reference developer documentation to troubleshoot
- SWBAT use Victory react.js components to visualize data

## Sequence

1. [Launch](#launch)
2. [Getting Started with Victory](#getting-started-with-victory)
3. [More Victory Examples](#more-victory-examples)
4. [Visual Design](#visual-design)
5. [Close](#close)

## Launch

What do you do when you want to include data visualizations in your React application? Maybe you'd google "react.js data visualization"? If you were to google that, hiding on the second page of results is a [React-based data visualization library called Victory](https://formidable.com/open-source/victory/).

Explore their [home page](https://formidable.com/open-source/victory/) and see what you think.

Now clone [this repository](https://github.com/upperlinecode/nyc_open_data_water_project), `cd` into the `nyc_open_data_water_project` folder, run `npm install` and `npm start`, and then preview the running application. Explore the code and see if you can determine how Victory was used to visualize the data in that app.

- How many data visualization components are there?
- What is the filename of the New York City Population data?
- Which Victory library components are imported for the Water Consumption visualization?

## Getting Started with Victory

By now you're familiar with _why_ you'd want to [visualize data](./data/visualization.md), but doing it will draw upon not just our ability to code but also our skills in visual design. Once you know how to make a visualization with Victory, then we'll discuss how to make a _good_ visualization with Victory.

Although there are quite a few other data visualization libraries out there (e.g. [d3.js](https://d3js.org/)), we've chosen to explore Victory because it is a natural fit when we're building with React.

As with any new library or software, the best place to get started learning about Victory is the developer documentation, specifically Victory's [Getting Started Guide](https://formidable.com/open-source/victory/docs).

Open the [Getting Started Guide](https://formidable.com/open-source/victory/docs) and take a quick look through the documentation; this is how the team at Victory suggest you begin to learn how to use Victory. Don't worry if it seems like there's a lot there; we're still going to help you make sense of it all.

> Note: Instead of reproducing the Victory Getting Started Guide, you will practice using the developer documentation to figure out how to work with Victory. This is how real developers would approach and implement a library like this.

Let's consult the Victory Getting Started Guide in order to build the data visualization below:

![Stacked Bar Graph](./img/victory-1.png)

1. (Guide Step 1) Initialize a new React project:
	a. Run `git clone git@github.com:FormidableLabs/victory-tutorial.git`.
	b. `cd` into the `victory-tutorial` folder.
	c. Overwrite the contents of the `client.js` file with what's in the guide.
	d. Run `npm install` and `npm start` to install the dependencies and spin up the basic project.
2. (Guide Step 2) Add Victory via `npm install victory` and `import` the whole library into your project. Check the documentation to see how they suggest doing this.
3. (Guide Step 3) Add the data below to your file:
```javascript
const data = [
  {quarter: 1, earnings: 13000},
  {quarter: 2, earnings: 16500},
  {quarter: 3, earnings: 14250},
  {quarter: 4, earnings: 19000}
];
```
4. (Guide Step 4a) Import the `VictoryBar` component from the Victory library, and use it (`<VictoryBar/>`) in your project. But wait, it doesn't refer to the data yet...
5. (Guide Step 4b) Add accessor props to the `<VictoryBar/>` component, including for `data`, `x`, and `y` values.
6. (Guide Step 5) Wrap the `<VictoryBar/>` component with a `<VictoryChart/>` component to provide axes, and don't forget to import `VictoryChart`, too.
7. (Guide Step 6) Import and add the `<VictoryAxis/>` component (x 2!), and set props to add `tickValues` and `tickFormatting`. Notice how you can also add `domainPadding` to the `<VictoryChart/>` component to better arrange the y-axis.
	- How does Victory make a distinction between the x-axis and the y-axis?
8. (Guide Step 7) Import and add the `<VictoryTheme/>` component, and add a `theme` prop to the `<VictoryChart/>` component.
9. (Guide Step 8) Import and add the `<VictoryStack/>` component, and update your component according to the Getting Started Guide to build the stacked bar chart shown above.

The Getting Started Guide also shows a Step 9 which overrides the default theme colors using a `colorScale` prop on the `<VictoryStack/>` component; we'll return to this later when we discuss visual design.

## More Victory Examples

In addition to the stacked bar graph component you just saw, there are examples of another 20+ visualizations you could implement in Victory. Check them out in Victory's [Visualization Gallery](https://formidable.com/open-source/victory/gallery/).

![Victory Gallery](./img/victory-gallery.png)

Click into one of the visualizations and explore the code that's used to produce it. Most importantly, look at the data and the structure of the data that is ingested. For instance, the Streamgraph visualization below is made up of multiple `<VictoryArea/>` components, each of which is built from a series of points with an `x`, `y`, and `y0` value.

![Streamgraph](./img/victory-2.png)

> The `y` and `y0` values define a range at a value for `x` which is then displayed on the Streamgraph. `y` corresponds to the max value, and `y0` corresponds to the min value.

Although the example uses the function `getStreamData()` below to generate random values, data could also come from some other source, e.g. a spreadsheet.

```javascript
getStreamData() {
  return _.range(7).map(i =>
    _.range(26).map(j => ({
      x: j,
      y: (10 - i) * _.random(10 - i, 20 - 2 * i),
      _y0: -1 * (10 - i) * _.random(10 - i, 20 - 2 * i)
    }))
  );
}
```

### Optional Exercise

Most of the data used by Victory comes in the form of `x`, `y` pairs. Given the simple example data below, which graph(s) do you think could be used to display the data?

```javascript
const lastYear = {[
  { x: 1, y: 2 },
  { x: 2, y: 3 },
  { x: 3, y: 5 },
  { x: 4, y: 4 },
  { x: 5, y: 7 }
]}

const thisYear = {[
  { x: 1, y: 3 },
  { x: 2, y: 5 },
  { x: 3, y: 4 },
  { x: 4, y: 6 },
  { x: 5, y: 3 }
]}

const nextYear = {[
  { x: 1, y: 4 },
  { x: 2, y: 7 },
  { x: 3, y: 3 },
  { x: 4, y: 4 },
  { x: 5, y: 5 }
]}
```

Now you're ready to get creative thinking about how different visualizations can be used to represent different kinds of data.

## Visual Design

> I'm realizing the more I think about this part, that it's VERY important to me that we model thinking through the visual design here.
>
> So like, it'd be easy to gloss over things like colors and font sizes in favor of showing every bell and whistle Victory has to offer.
>
> Let's prioritize the visual design over the full power of Victory, because I'd rather students know how to make one beautiful data viz, rather than 6 unhelpful / unreadable ones.

## Close

Some text here

#### Questions for students

- Some text here
