# Functional Components & Class Components

## Functional Components Review

So far, we've describe two ways to create functional components in React. There's the "True Functional Component" method:

```javascript
// True Functional Component
const Example = () => {
  return(
    <div>
      //Block of JSX/HTML code goes here
    </div>
  );
};
```

And there's the "Functional Component as Constructor" method:

```javascript
// Functional Component as Constructor
const Example = () => {
  // Create a component
  const component = new React.Component()

  // Store state variables
  component.state = {}

  // Deal with an event
  function handleChange(event) {}

  // Deal with a lifecycle method
  component.componentDidMount = function() {} 

  // The component's return method
  component.render = () => {
    return(
      <div>
        //Block of JSX/HTML code goes here
      </div>
  )}

  // Return the component
  return component
}
```

> Don't worry if you haven't mastered all of this early in your React journey! You'll learn some of this in later lessons.

The Constructor method is especially useful when you need to store state variables; in fact, you can't store state in the True Functional Component format.

## Class-Based Components

The Constructor method is also, well, a shortcut. Usually React developers use a completely different method when a component needs to store state: Class-based Components. In this course, we've tried to simplify things and make all components functional; however in reality, class-based components are the ones that are used to store state.

So why did we say the Constructor method can store state? Well, the Constructor method is a functional workaround that creates a class-based component. You can read more about [Stateful Functional Components](https://medium.com/@baronmaximilianwilleford/react-without-this-39a76b8f2160), but we wanted to recognize how the Constructor method generates a class-based component.

A class-based component looks something like this:

```js
class Example extends React.Component {
  // Create a component with props, state, and event binding
  constructor(props) {
    super(props)
    this.state = {};
    this.handleChange = this.handleChange.bind(this);
  }

  // Deal with an event
  handleChange(event) {
    this.setState({});
  }

  // Deal with a lifecycle method
  componentDidMount() {
    // some lifecycle action here
  }

  // Render the component
  render() {
    return (
      <div>
        //Block of JSX/HTML code goes here
      </div>
    )
  }
}
```

> Here we've also shown how an event handler and a lifecycle method could be included in the definition of the `Example` component.

#### Aside: `this`

This way of writing components is different than the True Functional Component method, but it can get confusing especially when it comes to `this`. `this` is a part of JavaScript that enables a developer to write functions that refer to the part of the DOM that the function is bound to. Umm, what?

Well, let's say I have a bunch of buttons, each with a certain `id`, and I bind a function to each button that does an alert showing the `id` of the specific button that is pressed. When I press a button, I only want that button's `id` to be in the alert, not all of the `id`s of every button. `this` helps keep things straight, so something like `alert(this.id);` would only show the `id` of the button that was pressed, not all of the others. Got it?

## Matching a Class-Based Component to its Constructor Method

Let's compare these two ways of constructing components line-by-line to see how the class-based component maps to the functional constructor:

### Initiation

#### Class-Based

```js
class Example extends React.Component {

}
```

#### Functional Constructor

```js
const Example = () => {
  const component = new React.Component()

}
```

### Including props

#### Class-Based

```
constructor(props) {
  super(props)
}
```

#### Functional Constructor

```js
const Example = (props) => {
  const component = new React.Component()

}
```

### Including State

#### Class-Based

```
constructor() {
  this.state = {};
}
```

#### Functional Constructor

```js
component.state = {}
```

### Handling Events

#### Class-Based

```
constructor() {
  this.handleChange = this.handleChange.bind(this);
}

handleChange(event) {}
```

#### Functional Constructor

```js
function handleChange(event) {}
```

### Handling Lifecycle Events

#### Class-Based

```
componentDidMount() {}
```

#### Functional Constructor

```js
component.componentDidMount = function() {}
```

### Returning JSX

#### Class-Based

```
render() {
  return (
    <div>
      //Block of JSX/HTML code goes here
    </div>
  )
}
```

#### Functional Constructor

```js
component.render = function() {
  return (
    <div>
      //Block of JSX/HTML code goes here
    </div>
  )
}
```

### Wrap-Up

#### Class-Based

```

```

#### Functional Constructor

```js
return component;
```

## Wrap

So that's it! Now you can see how the class-based component has been re-written in the form of a constructor.

Again, out in the wild, developers will more often be using class-based components in cases where state and lifecycle methods are necessary for a component, but for this unit we've opted instead to write everything in one of two functional forms, either as a true functional component or as a functional constructor. The functional constructor produces the same result as the class-based component with a slightly less confusing syntax because it avoids the need for using `this` throughout.
