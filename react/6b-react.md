# State (Lifecycle methods, passing state among elements)

## Learning Objectives

- SWBAT pass state between components using props
- SWBAT explain when to use various lifecycle methods
- SWBAT add a lifecycle method to a functional component

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
// passing all state
<Component state={component.state} />

// passing select state properties
<Component foo={component.state.foo} bar={component.state.bar}/>
```

Importantly, any time we need a function to be able to access the parent state, we write that function as part of the parent component and pass the function to the child as a prop. This ensures that the child component has access to both the parent state and the function necessary to use or modify the state.

```js
function App() {
  const component = new React.Component();
  component.state = {
  	ItemA: 0,
  	ItemB: 0,
  	ItemC: 0
  }

  // Here we define a function that is passed to a component below...
  const someFunction = () => {
    // code that uses or modifies state
  }
  
  component.render = () => {
    return (
      <div>
      	// And we pass the someFunction function to each component as a prop
        <Item type="ItemA" price="1" buy={someFunction} />
        <Item type="ItemB" price="2" buy={someFunction} />
        <Item type="ItemC" price="3" buy={someFunction} />
      </div>
    )
  }

  return component;
}
```

Then, the child component can call the function that was passed as a prop using an inline event. Here, we need to pass `props` as a parameter of the `Item` function:

```js
function Item(props) {
  return(
    <div className="item" onClick={props.buy}>
      <p>Buy a {props.type}!</p>
    </div>
  )
}
```

This way of writing the function works, but we're missing an opportunity to pass it additional data in the form of some of the other props that were also passed to the component. What if we want to pass `props.type` to the `props.buy` function? We need to rewrite the function in the inline event as an anonymous function and pass it the necessary data:

```js
function Item(props) {
  return(
    <div className="item" onClick={() => {props.buy(props.type)}}>
      <p>Buy a {props.type}!</p>
    </div>
  )
}
```

We also need to rewrite `someFunction` to take advantage of the new parameter:

```js
const someFunction = (item) => {
  // code that uses or modifies state and includes the data passed to the function
}
```

### Passing State as props: Walk-through

> Clone [this repository](https://github.com/upperlinecode/react-pass-state) as a starting point for a walk-through where we'll see how to use props. Then `npm install` and `npm start`.

1. As you've seen, we could add an inline event to the `<Product />` component, such as:

```
<div className="product" onClick={() => {alert("I just bought an item!")}}>
  <p>Click me to buy a {props.type}!</p>
</div>
```

And this works well enough, but it's not great.

> Note: we need to write the function as an anonymous function to prevent it from running when the page is rendered.

2. Instead, maybe we'd want to abstract the inline function into a definition of the function (`const buy...`) and then an implementation of the function (`onClick={buy}`) like this:

```js
// define the function ...
const buyProduct = () => {
  alert("Hi!")
}

// ... then use the function inline
return(
  <div className="product" onClick={buyProduct}>
    <p>Click me to buy a {props.type}!</p>
  </div>
)
```

But that's still very limited: it's not going to allow the `<Product />` component to interact with its parent's state. To accomplish that, we need to define the function in the parent and pass it as a prop to the child component.

3. Let's remove the function definition and inline event from `Product.js`. Then, let's add an inline event called `buyProduct` to each of the `<Product />` components in `App.js`, each of which calls a function called `purchase`:

```js
  ...
  <Product type="Laptop" price="999.00" buyProduct={purchase} />
  <Product type="Mechanical Pencil" price="0.25" buyProduct={purchase} />
  <Product type="College Ruled Loose Leaf" price="2.75" buyProduct={purchase} />
  ...
```

4. We then need to define the `purchase` function in `App.js`:

```js
const purchase = () => {
  alert("I just bought an item!");
}
```

So far we are passing the function to the component, but it doesn't yet know when to use the function. 

5. Now we need to go back into `Product.js` and again use an inline event in order to implement the function for the child component. Recall that we need to refer to the function as `props.buyProduct` in order to access the function passed as a prop:

```js
<div className="product" onClick={props.buyProduct}>
  <p>Click me to buy a {props.type}!</p>
</div>
```

And this is great! If you click on the product, it should fire an alert that says "I just bought an item!". But wouldn't it be nice to indicate which item was just bought?

6. To do that, we'll need to rewrite the function in the `onClick` to be part of an anonymous function so we can pass `props.type` into `props.buyProduct`:

```js
<div className="product" onClick={() => {props.buyProduct(props.type)}}>
  <p>Click me to buy a {props.type}!</p>
</div>
```

7. We'll also need to rewrite the `purchase` function to incorporate passing in the parameter `item` and using it for our alert:

```js
const purchase = (item) => {
  alert("I just bought a " + item + "!");
}
```

> Try to expand the alert message to include the price for which the item was bought.

#### Mini-Challenges

8. We have a function that is being passed via props to a component, but we haven't yet used it to modify state. We can do this by updating the `purchase` function, as we've done before.

Try adding a new property called `cart` to the state object where `cart` is an array, `[]`. Each time a product is purchased, see if you can add an object to state using the `Array.push()` method.

9. Display the contents of the `cart` array (stored in the state component) in the `<Summary />` component.

> Note: we're already passing the entire state object to the `<Summary />` component as a prop called `globalState`. Think of how you might use `.map()` to iterate over the `cart`.

10. Showing every purchase is ok for line-item detail, but try to show aggregate counts of each purchased item in the `<Summary />`.


## Lifecycle Methods (optional)

Sometimes a developer will want to control how components are added (mounted), how and when they are updated based on changes to props and state, and how they are removed (unmounted) from an app. Instead of relying on React to always know when to mount, update, and unmount components, we can use lifecycle methods to instruct React exactly how a component should act throughout its existence.

![Common React Lifecycle Methods](../img/react-lifecycle-methods.png)

> View an interactive version of this diagram on [projects.wojtekmaj.pl](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/).

The **most common** lifecycle methods are:

### Mounting

| Lifecycle Method | Description | Most useful for ... |
| :---: | --- | --- |
| `componentDidMount` | What to do once your component is there | Executing an API call for data that will be used to populate the component's props |

### Updating

| Lifecycle Method | Description | Most useful for ... |
| :---: | --- | --- |
| `componentDidUpdate` | What to do when a component gets new props or new state | Making a change only when particular props or state is changed |

### Unmounting

| Lifecycle Method | Description | Most useful for ... |
| :---: | --- | --- |
| `componentWillUnmount` | To control what happens before a component is removed | Cleaning up after a component |

> Check the [React Developer Documentation](https://reactjs.org/docs/react-component.html) for a full list of supported (and unsupported) lifecycle methods.

### Using Lifecycle Methods

Lifecycle methods are at your disposal as a developer, however you very often won't use any of them.

We will, however, revisit them when we get to making API calls. Using the `componentDidMount` method will enable our app to wait to render a component that depends on data until we've fetched that data.

## Close

At this point you should be familiar with how (and why) props can be used to pass state and functions that modify state from parent components to child components. The next several labs will give you additional practice passing state from parents to children and using state in child components.

#### Questions for students

- Why do you think React was written so child components don't pass their state to their parent?
- When do you think it's best for a component to have its own state vs. using the parent (or global) state?
