# State (State, inline events)

## Learning Objectives

- SWBAT articulate why state is important in React
- SWBAT compose functional components that include state
- SWBAT call inline events that use or modify state

## Sequence

1. [Launch](#launch)
2. [State](#state)
3. [State in Functional Components](#state-in-functional-components)
4. [Inline Events](#inline-events)
5. [Close](#close)

## Launch

* You may want to launch by having students jump into the [finished example](https://three-button-state.herokuapp.com/) of the app that we can/will build as part of this lesson.
* Have students clone the [template](https://github.com/upperlinecode/three-button-react-lab) to code along.

So far we've seen how props can be used in React to pass data to functional components. Passing props enables us to design and code a component one time and then feed in property data in order to show different versions of that component.

However, once the component has been rendered with those props, it's still a static component. But when we think about web applications, we generally imagine user interactivity that allows us to change what we see on screen based on actions a user takes:

- Whether or not a user has liked a post.
- Whether or not a form has been filled in correctly.
- Whether or not a username has already been taken.
- How many of a given item a user has added to their shopping cart.
- Which theme a user prefers for viewing a website, especially for colorblindness or other accessibility reasons.

Props don't enable us to keep track of interactive data like this; props don't get changed or updated when a user interacts with a component in a particular way. To keep track of that, we need to understand a new concept in React: state.

## State

State is a set of stored properties (an `Object`) that can be used or referenced throughout an app, and when changes are made to the state object, those changes can cascade throughout an app.

```js
this.state = {
  status: "active",
  posts: [],
  comments: [],
  nightMode: true,
  style: {},
  date: new Date(),
  // etc.
}
```

This example includes a fairly complex state, which includes many different types of information and several different nested data structures. We'll start with mostly Numbers and Strings.

## State in Functional Components

State can be included as part of a component or it can be passed down from a parent to a child component. First we'll take a look at how state can be stored as part of a component, and later we'll look at how state can be shared among child components via state on a parent component (or a global state on the App component).

### Stateful Components must be Class Components

So far, we've primarily been using functional components (components written as functions) to build our React applications. If you look at most React developer documentation, you'll find that functional components cannot be used to store state. As a result, class-based components (components written as classes) are typically introduced at the same time as when state is introduced.

### Accessing State

Functional components can access the state object by using JSX. The code below would insert the value of the `status` property of the state object shown above in between the two `span` elements:

```html
<span>{this.state.status}</span>
```

### Updating State

State is an immutable (unchangeable) object, which means when we are interacting with it, we **never modify state directly**. Instead, we make a copy of state, update that copy, then set the copy to be the new version of state.

The state property `favoriteColor` might be `red`:

```js
this.state = {
  favoriteColor: "red",
  favoriteBand: "Janelle Monae"
}
```

But when we've changed our minds, and now our `favoriteColor` is `blue`, we need to use the `.setState()` method in order to update state. You can do this in two ways: you can either pass in a JavaScript object, or you can pass in an arrow function.

#### Option 1: Use a JavaScript Object
```js
this.setState({favoriteColor: "blue", favoriteFood: "sushi"});
```

When you set state by passing in a new dictionary, it will merge in any new key-value pairs, overwrite any existing key-value pairs that match the keys you passed, and leave alone earlier key-value pairs that don't match anything in the new dictionary. So the new state would look something like this:

```js
{
  favoriteColor: "blue",
  favoriteFood: "sushi",
  favoriteBand: "Janelle Monae"
}
```

#### Option 2: Use an arrow function 
```js
this.setState(state => {
  state.favoriteColor = "blue";
  state.favoriteFood = "sushi";
  return state;
});
```

> Make sure NEVER to directly modify state directly unless you're inside a setState arrow function as in option 2. The expression `this.state.favoriteColor = "Blue"` will cause unwanted behavior and will not trigger a re-render, which is the main reason we're using React.js in the first place.

## Inline Events

Because state is closely associated with interactivity, we need a way to listen for when a user interacts with elements in our app. HTML has a native set of "[event handlers](https://www.w3schools.com/js/js_events.asp)" that will execute a JavaScript function when a particular action happens. In React, there are similar, slightly different camel-cased versions of these same event handlers that are used in functional components to execute an action when a user interacts with that element. Here are some of the most useful.

| HTML | React | Action | Example |
| :---: | :---: | --- | --- |
| `onchange` | `onChange` | An HTML `<input>` element has been changed | A checkbox is checked<br>A checkbox is unchecked<br>A dropdown choice selected<br>Etc. |
| `onclick` | `onClick` | User clicks any HTML element ||
| `onmouseover` | `onMouseOver` | User cursors over any HTML element ||
| `onmouseout` | `onMouseOut` | User cursors away from any HTML element ||
| `onkeydown` | `onKeyDown` | User pushes a keyboard key ||

To use these in action, add them as attributes, and then use JSX to explain what function should be called when

```jsx
// Example of the onClick inline event callback without arguments:
<button onClick={()=>{this.handleClick()}}>Click me!</button>

// Example of the onClick inline event callback with arguments:
<button onClick={()=>{this.handleClick(arguments)}}>Click me!</button>

// Example of the most common notation - it's simpler but only allows the default EVENT arguments to be passed, rather than custom arguments.
<button onClick={this.handleClick}>Click me!</button>
```

The function `handleClick` is not a reserved or special name - it's just a commonly used name for functions that respond to click events. Separately, we'd need to define a function called `handleClick` (or whatever you choose to call the function) in order to control what happens when that click event occurs.

> Check out the [React Documentation for Event Handlers](https://reactjs.org/docs/handling-events.html)

### Changing State with an Inline Event

As you might have anticipated, inline events can be used to change state. Here's a [finished example](https://three-button-state.herokuapp.com/) of the app we can build with the code below. Have students clone the [template](https://github.com/upperlinecode/three-button-react-lab) to code along.

In the example below:

- There is a state property `button1` which is initially set to `On!`. The version in the template has state properties for all three buttons, and state can have as many or as few properties as you like.

```js
this.state = {
  button1: "On!"
}
```

- The `<button>` element has an `onClick` inline event that calls the `handleButton1` function

```js
render() {
  return(
    <div className="StateCard">
      <h2>Press some buttons!</h2>
      <div className="card-content">
        <div className="item">
          <button onClick={this.handleButton1}>
            Button 1
          </button>
          <p>Current status: {this.state.button1}</p>
        </div>
      </div>
    </div>
  );
}
```

- The `handleButton1` function updates the `button1` state to the opposite of its current value, turning the light on or off.

```js
handleButton1 = () => {
  if (this.state.button1 === "On!") {
    this.setState({button1: "Off..."})
  } else {
    this.setState({button1: "On!"})
  }
}
```

#### Challenges for students:
* Have the students match the `handleButton1` function definition written here to make button 1 work as in the example.
* Have students complete the same functionality for buttons 2 and 3. Help them pseudocode out the steps:
    1. Embed the current state of button 2 and button 3 in the status paragraph.
    2. Create `onClick` attributes for each of the `<button>` elements.
    3. Embed the functions `handleButton1` and `handleButton2` into those buttons.
    4. Code out functionality for `handleButton2` to increase the `this.state.button2` property by 1 each time. Be sure to use the `this.setState({property: value})` syntax.
    5. Code out functionality for `handleButton3` to change the `this.state.button3` property each time and say the sentence "You are cool!" one word at a time. Be sure to use the `this.setState({property: value})` syntax.
* Right now these buttons assume only a basic understanding of JavaScript, but there are some really wonderful advanced JavaScript functionalities that allow for much cooler functions. Brainstorm some more interesting behaviors for our app, and program out those event handlers.

## Close

We've seen how state is an object in which properties (related to the interactivity) of the app can be stored.

In the next lesson, we'll see how state can be passed between components, and we'll learn about how to optimize when components are created, for how long they live, when they know to update, and how to remove them from our app's memory.

#### Questions for students

- Consider an app you use regularly. Assume it's built using React: how are they using state to create a pleasant user experience?
- Thinking of the same app, what inline events do you think are being called to control the app's interactivity?
