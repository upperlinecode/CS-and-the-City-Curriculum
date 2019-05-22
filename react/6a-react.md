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

So far we've seen how props can be used in React to pass data to functional components. Passing props enables us to design and code a component one time and then feed in property data in order to show different versions of that component.

But what if we wanted to know:

- whether a checkbox is checked or not
- a selection the user makes on a form
- whether the user has selected a particular global configuration

Props don't enable us to keep track of interactive data like this; props don't get changed or updated when a user interacts with a component in a particular way. To keep track of that, we need to understand a new concept in React: state.

## State

State is a set of stored properties (an `Object`) that can be used or referenced throughout an app, and when changes are made to the state object, those changes can cascade throughout an app.

```js
this.state = {
  posts: [],
  comments: [],
  nightMode: true,
  style: {},
  date: new Date(),
  // etc.
}
```

## State in Functional Components

State can be included as part of a component or it can be passed from a parent to a child component. First we'll take a look at how state can be stored as part of a component, and later we'll look at how state can be passed between child components via state on a parent component (or a global state on the App component).

### But First, a Note on Components with State

So far, we've primarily been using functional components (components written as functions) to build our React applications. If you look at most React developer documentation, you'll find that functional components cannot be used to store state. As a result, class-based components (components written as classes) are typically introduced at the same time as when state is introduced.

In these lessons, however, we have been using (and will continue to use) [a workaround that enables us to write a functional component](https://medium.com/@baronmaximilianwilleford/react-without-this-39a76b8f2160) which has the effect of creating a class-based component that can store state. If you're interested, here's a [line-by-line map]() of how the functional constructor is converted to a class-based constructor.

The tl;dr here is that we'll be using functional components to store state even though that isn't normally how React is written.

### Accessing State

Functional components can access the state object by using JSX. The code below would insert the value of the `text` property of state in between the two `span` elements:

```html
<span>{component.state.text}</span>
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
/* incomplete way to update state */
component.setState({"favoriteColor": "blue"});
```

This way works well when we only have one property in state. But since we have more than one property, we'd lose the state of our `favoriteBand` if we did it this way.

Instead, we need to first make a copy of the current state, then update that copy, then store that copy as the new state:

```js
/* complete way to update state */
// first make a duplicate of the current state
let newState = component.state;

// update the duplicate
newState.favoriteColor = "blue";

// store the modified duplicate as the new state
component.setState(newState);
```

## Inline Events

Because state is closely associated with interactivity, we need a way to listen for when a user interacts with elements in our app. HTML has a native set of "[event handlers](https://www.w3schools.com/js/js_events.asp)" that will execute a JavaScript function when a particular action happens. In React, there are similar, slightly different camel-cased versions of these same event handlers that are used in functional components to execute an action when a user interacts with that element.

| HTML | React | Action | Example |
| :---: | :---: | --- | --- |
| `onchange` | `onChange` | An HTML element has been changed | A checkbox is checked<br>A checkbox is unchecked<br>A dropdown choice selected<br>Etc. |
| `onclick` | `onClick` | User clicks an HTML element ||
| `onmouseover` | `onMouseOver` | User cursors over an HTML element ||
| `onmouseout` | `onMouseOut` | User cursors away from an HTML element ||
| `onkeydown` | `onKeyDown` | User pushes a keyboard key ||

```html
// example of the onClick inline event
<input type="button" onClick={handleClick} value="Click me!" />

// example of the onChange inline event
<select onChange={handleChange}>
  <!-- options -->
</select>
```

Separately, we'd need to define a function called `handleClick` or `handleChange` (or whatever you called the function) in order to control what happens when that click or change occurs. 

> Check out the [React Documentation for Event Handlers](https://reactjs.org/docs/handling-events.html)

### Changing State with an Inline Event

As you might have anticipated, inline events can be used to change state.

In the example below:

- there is a state property `isChecked` which is initially set to `false`.
- the `<input>` has an `onChange` inline event that calls the `handleClick` function
- the `handleClick` function updates the `isChecked` state to the opposite of its current value while the checkbox is being un/checked

```js
function Checkbox() {
  const component = new React.Component();
  component.state = {
    "isChecked": false
  }
  
  function handleClick(event) {
    var state = component.state;
    state.isChecked = !component.state.isChecked;
    component.setState(state);
  }

  component.render = function() {
    return (
      <input type="checkbox" onChange={handleClick} />
    )
  }
  return component;
}

export default Checkbox
```

## Close

We've seen how state is an object in which properties (related to the interactivity) of the app can be stored.

In the next lesson, we'll see how state can be passed between components, and we'll learn about how to optimize when components are created, for how long they live, when they know to update, and how to remove them from our app's memory.

#### Questions for students

- Consider an app you use regularly. Assume it's built using React: how are they using state to create a pleasant user experience?
- Thinking of the same app, what inline events do you think are being called to control the app's interactivity?
