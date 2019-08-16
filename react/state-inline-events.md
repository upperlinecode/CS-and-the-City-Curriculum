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

State can be included as part of a component or it can be passed from a parent to a child component. First we'll take a look at how state can be stored as part of a component, and later we'll look at how state can be passed between child components via state on a parent component (or a global state on the App component).

### But First, a Note on Components with State

So far, we've primarily been using functional components (components written as functions) to build our React applications. If you look at most React developer documentation, you'll find that functional components cannot be used to store state. As a result, class-based components (components written as classes) are typically introduced at the same time as when state is introduced.

In these lessons, however, we have been using (and will continue to use) [a workaround that enables us to write a functional component](https://medium.com/@baronmaximilianwilleford/react-without-this-39a76b8f2160) which has the effect of creating a class-based component that can store state. It's less memory efficient, but is a little easier conceptually for students than digging immediately into the concept of "this", which changes meaning when written at different levels of code.

The tl;dr here is that we'll be using functional components to store state even though that isn't normally how React is written.

> To go a bit more in-depth, see [how the constructor method compares to the class-based method](class-to-function-component.md).

### Accessing State

Functional components can access the state object by using JSX. The code below would insert the value of the `status` property of the state object shown above in between the two `span` elements:

```html
<span>{component.state.status}</span>
```

### Updating State

State is an immutable (unchangeable) object, which means when we are interacting with the state object, we don't modify it directly. Instead, we make a copy of state, update that copy, then set the copy to be the new version of state.

The state property `favoriteColor` might be `red`:

```js
component.state = {
  favoriteColor: "red",
  favoriteBand: "Wham!"
}
```

But when we've changed our minds, and now our `favoriteColor` is `blue`, we need to use the `.setState()` method in order to update state:

```js
component.setState({"favoriteColor": "blue"});
```

> Make sure NEVER to directly modify state. The expression `component.state.favoriteColor = "Blue"` will cause unwanted behavior and will not trigger a re-render, which is the main reason we're using React.js in the first place.

NOTE: If you want to store more complex data in the State object (like arrays, or other objects), you may need to make a copy of state before modifying it.

```js
// Make a copy of the array of shoes stored in state.
let newList = Array.from(component.state.shoes)
// Modify that list.
newList.append("Jordans")
// Overwrite the old list with the new one.
component.setState({shoes: newList})
```

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

```html
// Example of the onClick inline event without arguments:
<button onClick={()=>{component.handleClick()}}>Click me!</button>

// Example of the onClick inline event with arguments:
<button onClick={()=>{component.handleClick(arguments)}}>Click me!</button>

// NOTE: may also see this notation - it's simpler but only allows the default event arguments to be passed.
<button onClick={component.handleClick}>Click me!</button>
```

The function `handleClick` is not a reserved or special name - it's just a commonly used name for functions that respond to click events. Separately, we'd need to define a function called `handleClick` (or whatever you choose to call the function) in order to control what happens when that click event occurs.

> Check out the [React Documentation for Event Handlers](https://reactjs.org/docs/handling-events.html)

### Changing State with an Inline Event

As you might have anticipated, inline events can be used to change state. Here's a [finished example](https://three-button-state.herokuapp.com/) of the app we can build with the code below. Have students clone the [template](https://github.com/upperlinecode/three-button-react-lab) to code along.

In the example below:

- There is a state property `button1` which is initially set to `On!`. The version in the template has state properties for all three buttons, and state can have as many or as few properties as you like.

```js
component.state = {
  button1: "On!"
}
```

- The `<button>` element has an `onClick` inline event that calls the `handleButton1` function

```js
component.render = () => {
  return(
    <div className="StateCard">
      <h2>Press some buttons!</h2>
      <div className="card-content">
        <div className="item">
          <button onClick={()=>{component.handleButton1()}}>
            Button 1
          </button>
          <p>Current status: {component.state.button1}</p>
        </div>
      </div>
    </div>
  )
}
```

- The `handleButton1` function updates the `button1` state to the opposite of its current value, turning the light on or off.

```js
component.handleButton1 = () => {
  if (component.state.button1 === "On!") {
    component.setState({button1: "Off..."})
  } else {
    component.setState({button1: "On!"})
  }
}
```

#### Challenges for students:
* Have the students match the `handleButton1` function definition written here to make button 1 work as in the example.
* Have students complete the same functionality for buttons 2 and 3. Help them pseudocode out the steps:
    1. Embed the current state of button 2 and button 3 in the status paragraph.
    2. Create `onClick` attributes for each of the `<button>` elements.
    3. Embed the functions `handleButton1` and `handleButton2` into those buttons.
    4. Code out functionality for `handleButton2` to increase the `component.state.button2` property by 1 each time. Be sure to use the `component.setState({property: value})` syntax.
    5. Code out functionality for `handleButton3` to change the `component.state.button3` property each time and say the sentence "You are cool!" one word at a time. Be sure to use the `component.setState({property: value})` syntax.
* Right now these buttons assume only a basic understanding of JavaScript, but there are some really wonderful advanced JavaScript functionalities that allow for much cooler functions. Brainstorm some more interesting behaviors for our app, and program out those event handlers.

## Close

We've seen how state is an object in which properties (related to the interactivity) of the app can be stored.

In the next lesson, we'll see how state can be passed between components, and we'll learn about how to optimize when components are created, for how long they live, when they know to update, and how to remove them from our app's memory.

#### Questions for students

- Consider an app you use regularly. Assume it's built using React: how are they using state to create a pleasant user experience?
- Thinking of the same app, what inline events do you think are being called to control the app's interactivity?
