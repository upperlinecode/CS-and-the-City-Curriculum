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

> Note: Any component can include state, but we'll mostly be using state in the `App` component and then "passing" state to any child components.

### Accessing State

Functional components can access the state object by using ...

```js
// An example of accessing state
```

### Updating State

State is an immutable (unchangeable) object, which means when we are interacting with the state object, we don't modify it directly. Instead, we can essentially make a copy of state, update that copy, then set the copy to be the new version of state.

```js
// An example of updating state here
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

```js
// examples of inline event

// examples of inline event

```

> Check out the [React Documentation for Event Handlers](https://reactjs.org/docs/handling-events.html)

### Changing State with an Inline Event

As you might have anticipated, inline events can be used to change state.

In the example below:

- there is a state property `isChecked` which is initially set to `false`.
- the `checked` property of the `<input>` is set based on the `isChecked` state
- the `<input>` also has an inline event, `onChange` which calls the `handleClick` function
- the `handleClick` function updates the `isChecked` state to the opposite of its current value
- the update to the `isChecked` state then causes the checkbox to change its `checked` property to appear as a checked box

```js
// example of checkbox changing state with handleClick event handler
```

## Close

We've seen how state is an object in which properties (related to the interactivity) of the app can be stored.

In the next lesson, we'll see how state can be passed between components, and we'll learn about how to optimize when components are created, for how long they live, when they know to update, and how to remove them from our app's memory.

#### Questions for students

- Consider an app you use regularly. Assume it's built using React: how are they using state to create a pleasant user experience?
- Thinking of the same app, what inline events do you think are being called to control the app's interactivity?
