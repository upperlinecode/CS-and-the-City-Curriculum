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

![Victory Example 1](./img/victory-example-1.png)
![Victory Example 2](./img/victory-example-2.png)

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

In addition to the stacked bar graph component you just saw, there are examples of another 20+ visualizations you could implement in Victory's [Visualization Gallery](https://formidable.com/open-source/victory/gallery/).

> These examples are constructed from the 14 Victory components (as per the Victory Documentation section "Charts"), several containers, and various effects. Each item is documented in case you'd like to use that type of graph.

![Victory Gallery](./img/victory-gallery.png)

Click into one of the visualizations and explore the code that's used to produce it. Most importantly, look at the data and the structure of the data that is ingested. For instance, the Streamgraph visualization below is made up of multiple `<VictoryArea/>` components, each of which is built from a series of points with an `x`, `y`, and `y0` value.

![Streamgraph](./img/victory-2.png)

> The `y` and `y0` values define a range at a value for `x` which is then displayed on the Streamgraph. `y` corresponds to the max value, and `y0` corresponds to the min value.

Although the example uses the function `getStreamData()` below to generate random values, data could also come from some other source, e.g. a spreadsheet or an API.

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

### Building a Beautiful Visualization: Color

Luckily, Victory comes with several built-in color palettes that make our lives a lot easier when we're trying to choose colors for our visualizations. Buried [deep in the documentation](https://formidable.com/open-source/victory/docs/victory-stack#colorscale) is a description of how to use the `colorScale` prop to quickly colorize a component like a `<VictoryStack/>`, `<VictoryPie/>`, or `<VictoryGroup/>`:

> The colorScale prop is an optional prop that defines a color scale to be applied to the children of the component. This prop should be given as an array of CSS colors, or as a string corresponding to one of the built in color scales: "grayscale", "qualitative", "heatmap", "warm", "cool", "red", "green", "blue".

| ![Warm Colors](./img/victory-warm.png) | ![Cool Colors](./img/victory-cool.png) | ![Qualitative Colors](./img/victory-qualitative.png) | ![Grayscale Colors](./img/victory-grayscale.png) |
|:---:|:---:|:---:|:---:|
| "warm" | "cool" | "qualitative" | "grayscale" |

Ask any designer, and they'll tell you that color is a critical player in visual communication because color brings with it meaning based in societal contexts. Color theory is a whole field of study on its own, and although we can't say everything about it here, it's worth mentioning a few key ideas.

1. In the West, red things tend to be hot or have a negative connotation; blue things tend to be cold; green things tend to have a positive connotation.
2. Less dense (or lighter) colors are used to represent lower concentrations, while dense (or dark) colors are used to represent high concentrations.
3. Humans are notoriously bad at deciphering data encoded as variations in color, so it's best to use color as a signifier, but not a source of comparison (i.e. "Which is bluer?" is a tough question for us to answer).
4. Some people are color-blind, so make sure to choose colors that are different in color, tint, and shade and don't rely on color differences to get your point across.

When choosing colors and color palettes, you want to think about the message you're trying to communicate with the data. When not used properly, color can confuse a data visualization more than it can help it. The best way to avoid this confusion is to show the visualization to someone else and see whether they understand the meaning of the colors. If not, you may want to change them.

### Building a Beautiful Visualization: Text & Fonts

In addition to color, one of the biggest areas in which a visualization can be improved is by the addition of text. However, sometimes text can also overwhelm a visualization if there are too many labels, labels that are too long, or labels that take up too much space or attention in the visualization.

Victory has some built-in default parameters for styling of labels (axis labels and data labels), but sometimes you need to tweak those defaults. To do so, you can edit [Victory's default theme](https://formidable.com/open-source/victory/guides/themes) or [build your own theme](https://formidable.com/open-source/victory/docs/victory-theme).

Explore the [Live Code](https://formidable.com/open-source/victory/guides/themes) in Victory's documentation to see how you could implement a theme that works well for the visualizations you make.

## Close

Although we jumped into using Victory for data visualization with React, it's worth noting that it's sometimes easier to ideate a data visualization with pencil and paper before ever touching a line of code. This way you can ensure that the time you spend corraling data leads to a worthwhile end.

Using a library like Victory makes it very easy to quickly spin up data visualizations. Equally important, the ability to source data - including live or real-time data - and visualize it can be a critical factor when relying on data and data visualizations to make good decisions.

#### Questions for Students

- Think about the 
