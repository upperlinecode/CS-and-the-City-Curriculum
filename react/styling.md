# Inline and Conditional Styling

## Learning Objectives

* SWBAT use JavaScript objects to style elements in a React project.
* SWBAT use conditional rendering to style a component based on props that are passed to it.

## Sequence

1. [Launch](#launch)
2. [Inline Styling](#inline-styling)
3. [Conditional Styling](#conditional-styling)
4. [Close](#close)

## Launch

`git clone` [this repository](https://github.com/upperlinecode/inline-and-conditional-style-lecture), `cd` into the repository folder, and then `npm install` and `npm start`.

Add some inline styling to the div with the className `App` in the `App.js` file. Try adding a blue background color.

> If students are unfamiliar with inline styling you can just have them copy the following code (which will produce an error):
```html
<div className="App" style="background-color: rgb(0,0,255)">
```

#### Questions for Students

* What did the error message say when you added this code?
* In your own words, what do you think this error message means?

![Error Message](./img/error.png)

## Inline Styling

It is possible to style your HTML using inline styling - just not the way we are used to. In this lecture we are going to explore how to add inline styling to an HTML element - the React way.

### Inline Styling is Different in React

As we saw from our opening, it is not possible to add inline style to an element using a string. Rather, the `style` attribute of an element will only accept a JavaScript object. Let's try adding a blue background again, this time by first creating an object and then applying the inline style using this object.

```javascript
function App() {
  let divStyle = {
    backgroundColor: "rgb(0,0,255)"
  }

  return (
    <div className="App" style = { divStyle }>
      <Navbar/>
      <TableHeader/>
    </div>
  );
}
```

First, we created an object called `divStyle` (you can name this whatever you want, it does not need to be called `divStyle`). Then we store the CSS property and style as an object key-value pair.

Once we have our object, we can style our `div` by passing this object to the `style` attribute of the element.

> It should be noted that you can style an element by passing an object directly into the style attribute (see below), but this can become hard to read/organize if multiple CSS properties are being applied to the element.
>
>```javascript
>function App() {
>  return (
>    <div className="App" style = {{ background: "rgb(0,0,255" }}>
>      <Navbar/>
>      <TableHeader/>
>    </div>
>  );
>}
>```

Let's add one style property to our object to make sure the whole screen has a background of blue.

```javascript
let divStyle = {
  backgroundColor: "rgb(0,0,255)",
  minHeight: "100vh"
}
```

You might have noticed that `minHeight` is traditionally `min-height` in CSS. In React, when styling an element with an object, any multi-word property with '-' characters converted to camelCase (the first word lowercase, and all subsequent words capitalized). For example, `box-shadow` would be `boxShadow` when used in a style object.

## Conditional Styling

What is the major benefit of inline styling in a React application? Conditional styling!

### Wins and Losses

In this lecture, we are going to make a website the displays data from each Knicks games in the 2018-2019 season. For each game, we will display which team the Knicks played, whether it was a home or away game, if they won or lost, the amount of points each team scored, and the overall win and loss record for the Knicks.

> Teachers: Feel free to use the game data from your school's teams for this lecture! The Knicks data is available in the repository but does not need to be used for this lecture.
> You should also feel free to encourage students to swap that data out with their favorite team, but be warned that variances in data might leave you debugging both the react code AND the sports scores data. 

To start, add a `TableRow` element to `App.js` with the following attributes/props.

```javascript
return (
  <div className="App" style = { style }>
    <Navbar/>
    <TableHeader/>
    <TableRow
      game={data[0]["Game"]}
      opponent={data[0]["Opponent"]}
      result={data[0]["Result"]}
      location={data[0]["Location"]}
      teamScore={data[0]["TeamScore"]}
      opponentScore={data[0]["OpponentScore"]}
      wins={data[0]["W"]}
      losses={data[0]["L"]}
    />
  </div>
);
```

You will notice that we used `data[0]` to populate the props of our `<TableRow />`. What does `data[0]` represent? How could we add the data from the second Knicks game to the website? How could we add the last game?

Then, we add some styling to `<TableRow />` with some inline styling as shown below.

```javascript
function TableRow(props) {
  let style = {
    backgroundColor: "rgb(240,240,240)"
  }

  return(
    <div className="table-rows" style={ style }>
      <div>{props.game}</div>
      <div>{props.opponent}</div>
      <div>{props.result}</div>
      <div>{props.location}</div>
      <div>{props.teamScore}</div>
      <div>{props.opponentScore}</div>
      <div>{props.wins}</div>
      <div>{props.losses}</div>
    </div>
  )
}
```

At this point, our web page looks OK. But, we can make it a bit more user-friendly if we indicate if the Knicks won or lost by changing the background to green if they won and red if they lost. This is where conditional rendering comes in. We can use `if`statements to check if the team won or lost. Then, on the condition they won we will change the background to green or red if they lost.

```javascript
function TableRow(props) {
  // Default to a very light greyscale value
  let rowStyle = {
    backgroundColor: "rgb(240,240,240)"
  }

  // Check the result to modify that property.
  if(props.result === "W"){
    rowStyle.backgroundColor = "rgb(0,255,0)"
  }
  else if(props.result === "L"){
    rowStyle.backgroundColor = "rgb(255,0,0)"
  }

  return(
    <div className="table-rows" style={ rowStyle }>
      <div>{props.game}</div>
      <div>{props.opponent}</div>
      <div>{props.result}</div>
      <div>{props.location}</div>
      <div>{props.teamScore}</div>
      <div>{props.opponentScore}</div>
      <div>{props.wins}</div>
      <div>{props.losses}</div>
    </div>
  )
}
```

As you can see, our first row should have a background color of green now.

#### Mini-Challenges

* Add another row with the data for the Knicks second game. Continue to add rows for the first 5 game.
* Create a conditional statement that make the font color yellow if the game was an away game. "@" is used represent an away game. (Note: you might need to make a new style object - like `scoreStyle` for the score)
* Create a conditional statement that makes the winning teams score bold.

## Close

Remember to gather student feedback on this lesson.

#### Questions for Students

* What are some ways you have seen conditional rendering used on a website before? How does this improve the experience of the website from the users perspective?
