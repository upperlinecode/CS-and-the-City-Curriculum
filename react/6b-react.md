# State (Lifecycle methods, passing state among elements)

## Learning Objectives

- SWBAT 
- SWBAT
- SWBAT

## Sequence

1. [Launch](#launch)
2. [Passing State Among Elements](#passing-state-among-elements)
3. [Lifecycle Methods](#lifecycle-methods)
4. [Close](#close)

## Launch

In the last lesson, we learned about state in functional components and how inline events can be used to modify state.

#### Questions for students

Think back over the last few things you've learned about React:

- How would you make it so that a child component is affected by a change in state of a parent component?

## Passing State Among Elements

### Passing State as props

Often, we'll want to pass state from a parent component to a child component, and we do that by passing state as a prop (or set of props). Whenever the parent state is updated, the update will trickle down to child components via props and update the child as well.

```js
// example of passing state as prop(s)
```

## Lifecycle Methods

Description of why lifecycle methods are needed...

As of React v16.3, the lifecycle methods are:

- `componentWillMount`: what to do when your component is about to mount; most useful for setting the configuration of the component that will be added soon.
- `componentDidMount`: what to do once your component is there; most useful for executing an API call for data that will be used to populate the component's props.
- `componentWillReceiveProps`: what to do when a components gets a bunch of new props; most useful to act on a particular prop change.
- `shouldComponentUpdate`: to control how a component should decide whether or not to update; most useful for controlling when a component re-renders.
- `componentWillUpdate`: similar to `componentWillReceiveProps` but used when also using `shouldComponentUpdate`.
- `componentDidUpdate`: what to do when a component gets new props or new state; most useful for making a change only when particular props or state is changed.
- `componentWillUnmount`: to control what happens before a component is removed; most useful for cleaning up after a component.

### Using Lifecycle Methods

Some text about using lifecycle methods

```js
// example of how to modify a functional component to include a lifecycle method
```

### Sub-content 2

Some text

#### Mini-Challenges

- Challenge 1
- Challenge 2

## Close

Some text here

#### Questions for students

> Some question
