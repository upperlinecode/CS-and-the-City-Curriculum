# CSS Grid

## Sequence

1. [Grid Template](#grid-template)
2. [Span](#span)
3. [Resources](#resources)

NOTE: The CSS Grid properties aren't recognized by all IDEs, but they are correctly rendered by most browsers. If you see errors in front of CSS Grid properties, test it before assuming it's wrong. Those errors may be in error themselves.

## Grid Template

Give students the code housed [here](https://github.com/upperlinecode/css-grid-walkthrough)


```css
#grid {
  display: grid;
}
```

Ask students:
* How many columns are in this "grid"?
* How many rows?
* How many items total are there?
* How wide is the column? (We're going for answers like "100%" or "fullscreen")
* How tall are the rows? (This is a good opportunity to look at the computed styles)

#### Columns

Add to the previous the code, but DO NOT PREVIEW until students have made predictions:

```css
#grid {
  display: grid;
  grid-gap: 8px;
  grid-template-columns: 250px auto 175px;
}
```

Have students predict:
* How many columns will there be?
* How big will the first column be?
* How big will the last column be?
* How big will the middle column be?
* How many rows will there be?

Preview the project, and then give students these other units of measurement and see if they can predict what will happen:
* `grid-template-columns: 30% 40% 30%;`
* `grid-template-columns: 1fr 1fr 1fr;`
* `grid-template-columns: 1fr 3fr 1fr;`
* `grid-template-columns: 35vw 30vw 35vw;`

So we have five units of measurement: pixels, fractions, percentages, viewport widths, and auto. All are useful. The trickiest distinction is percent vs. vw. **Percent** will be sized in proportion to the container - so if your gird is specifically only 80% of your screen because you're using a wrapper, percentages may make sense. **vw** is a measurement equal to 1% of the viewer's window, so it's really useful for when you're explicitly trying to create an edge-to-edge display. **vh** stands (of course) for viewport height, and since that's more widely varied based on the user's display, it's really helpful.

For horizontal measurements, the fr (fraction) unit ends up being the most useful.  

#### Rows

Challenge students:

> We've made a template for our columns. What do you think you'd do if you wanted to make a template for the rows too? Challenge yourself to do this by making the second row 250px, but the other rows just 100px.

Clearest solution:

```css
#grid {
  display: grid;
  grid-gap: 8px;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 250px 100px 100px;
}
```

#### Playtime
Challenge students to build each of the following:
1. A 6x2 grid
2. A 2x6 grid
3. A 3x4 grid where the second row is larger than the others


## Span

Reset the grid to a simpler form so that everyone's on the same page.

```css
#grid {
    display: grid;
    grid-gap: 8px;
    grid-template-columns: 1fr 2fr 1fr;
}
```

The coolest thing we can do is specifically size one cell to act differently from the other cells in the grid. For example, we can tell one item to be wider by spanning across multiple columns. Span is only one of several ways you can do this (you can also use gridlines as explicit start and stop values), but span is the most straightforward.


Here's how we make the ruby div span across two columns (and therefore be twice as wide). We're using an ID selector, which is actually already how we've been selecting and styling the grid. It lets us grab just ONE thing:

```css
#ruby {
  grid-column: span 2;
}
```

Challenge students:
* Turn the Ruby into a full header. (make it span 3 columns)
* Make the JavaScript div into a sidebar. (make it span several rows - 5 works)
* Pick a div and make it span across the entire bottom like a footer.
* Make another div span two rows *and* two columns.

Some solutions:

```css
#ruby {
  grid-column: span 3;
}

#js {
  grid-row: span 5;
}

#go {
  grid-column: span 3;
}
```

## Teaching Tip: Grids Unplugged

Students struggle to understand just how responsive grid is, and how many different ways it can be used to effectively (and ineffectively) lay content out on pages. The very highest leverage activity you can do before launching students into grid is to examine a site that uses grid and annotate the page.

Grid is one of many concepts where it may *feel* okay to jump in without pseudocoding first since it's so visual, but it's actually one of the places where each minute spent planning can shave 10 minutes off the time it takes to implement a design.

## Resources

Introduce students to some reference material to help them keep their cool. We're building an Upperline-specific CSS Grid cheat sheet that covers these exact same concepts, but in the meantime, direct students [here](https://css-tricks.com/snippets/css/complete-guide-grid/).

### Example pages that use grid in interesting ways

+ [CSS Grid Periodic Table](https://codepen.io/dudleystorey/full/rmWMXY/)
+ [Magazine Layout](https://codepen.io/hbuchel/pen/qOxGzW/)
