# State (State, inline events)

## Learning Objectives

- SWBAT articulate why state is important in React
- SWBAT compose functional components that include state
- SWBAT call inline events that use or modify state

## Sequence

1. Launch
2. State
3. State in Functional Components
4. Inline Events
5. Close

## Launch

So far we've seen how props can be used in React to pass data to functional components. This enables us to write a component once and then feed in the property data in order to show different versions of the same component.

But what if we wanted to know:

- whether a checkbox is checked or not
- a selection the user makes on a form
- whether the user has selected a particular global configuration

Props don't enable us to keep track of interactive data like this; props don't get changed or updated when a user interacts in a particular way. To keep track of that, we need to understand a new concept in React: state.

## State

State is a set of stored properties (an `Object`) that can be used throughout an app:

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

Note: Any component can include state, but we'll mostly be using state in the `App` component and then "passing" state to any child components.

Functional components can access the state object by using ...

```js
// An example of accessing state
```

### Updating State

State is an immutable (unchangeable) object, which means when we are interacting with the state object, we don't modify it directly. Instead, we can essentially make a copy of state, update that copy, then set the copy to be the new version of state.

```js
// An example of updating state here
```

### Passing State as props

Often, we'll want to pass state from a parent component to a child component, and we do that by passing state as a prop (or set of props). By doing this, whenever the state is updated, the update will trickle down to child components and update those as well.

```js
// example of passing state as prop(s)
```

## Inline Events

Because state is closely associated with interactivity, we need a way to listen for when a user interacts with elements in our app. HTML has a native set of "[event handlers](https://www.w3schools.com/js/js_events.asp)" that will execute a JavaScript function when a particular action happens. In React, there are similar, slightly different camel-cased versions of these same event handlers that are used in functional components to execute an action when a user interacts with that element.

| HTML | React | Action |
|*---*|*---*|---|
| onchange | onChange | An HTML element has been changed |
| onclick | onClick | The user clicks an HTML element |
| onmouseover | onMouseOver | The user moves the mouse over an HTML element |
| onmouseout | onMouseOut | The user moves the mouse away from an HTML element |
| onkeydown | onKeyDown | The user pushes a keyboard key |

```js
// examples of inline event

// examples of inline event

```

> Check out the [React Documentation for Event Handlers](https://reactjs.org/docs/handling-events.html)

## Close

Some text here

#### Questions for students

> Some question
