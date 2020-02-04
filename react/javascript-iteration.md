# Iteration with Javascript

## Learning Objectives

* SWBAT iterate over an array using a for loop
* SWBAT iterate over and array and return values using a map function
* SWBAT push objects into an empty array
* SWBAT iterate over an array and add elements to a webpage.

## Sequence

1. [Launch](#launch)
2. [Iteration with for loops](#iteration-with-for-loops)
3. [Iteration with map](#iteration-with-map)
3. [Iteration with forEach](#iteration-with-foreach)

## Launch

> Teacher note: This is generally really challenging, and may be worth breaking out into several days, one for each concept.

You might know that computers are incredibly fast at performing calculations. But it's hard to wrap ones head around just HOW fast they are. In one second your average desktop computer can perform over a billions calculations.

For most people, it would take over 300 years with no breaks to do what a modern computer can do in about one second.

The speed with which a computer can handle this type of tedious task is one major reason why people who dislike doing math problems often love writing computer programs - they can code out HOW the problem is done without having to go through the work of doing it.

#### Launch Challenges

* Print

## Iteration with `for` loops

As we saw from the launch, when we want a computer to repeat a task multiple times, the use of a **loop** make the task much easier and the code much more succinct. In this first section, we will explore how we can repeat a task multiple times using a `for` loop.

### The structure of a `for` loop

Each `for` loop has a set structure. Let's look at an example:

```javascript
for(let i = 0; i<5; i++){
  //DO SOMETHING
}
```

A `for` loop takes three statements separated by a semicolon. In short, it's easiest to think of these three statements as the **start where...**, **while...**, and **go up by...**. Reading these three statements for the above example, it would be "Start where i is 0, and keep going while i is less than 5, going up by 1 each time."

(If this is the first time students have seen `i++`, it may be worth mentioning that this is a really common syntax in many programming languages).

#### OPTIONAL: Under the hood of `for` loops

Here's a more precise look at exactly how these three statements are implemented. This is generally not helpful for first-time students.
* The first statement is the starting value of the loop - it's run only once, before the loop begins. The loop above begins with the number 0, but could start anywhere.
* The second statement is run *before* each iteration in the loop. The code block is only executed when this second statement evaluates to `True`.
* The third statement is run *after* each iteration in the loop. much we want to increment by every time the loops runs. In the above example, `i` will increase by 1 (`i++` is shorthand for `i = i + 1` or `i += 1`), but you could just as easily skip-count by 3s or any other number with something like `i = i + 3`.

#### Playtime

* Log out every number from 1-20
* Log out every number from 50-100
* Log out every even number up to 100
* Log out every multiple of 2 and every multiple of 3 up to 100
* Log out the sum of every number under 1000
* Log out the first 10 digits of the fibbonacci series.


#### Arrays for use with `for` loops

Here are some sample Arrays you can use with students.

These examples are most easily run in Repl.it, but you can also run them in a linked JavaScript file in an HTML document, which may reduce friction if you want to prioritize DOM manipulation through iteration as part of this lesson.

```javascript
const names = ["Yadira", "Kadiatou", "Isaiah", "Fancisco", "Darius"]
const nicknames = ["Deary", "Kadi-B", "Izzy", "Paco", "DRock"]
const ages = [22,28,27,33,29]
const favAnimals = ["Cat", "Ferret", "Dog", "Sloth", "Zebra"]
const birthLocations = ["Queens", "Bronx", "Manhattan", "Bronx", "Brooklyn"]
```

There is an array stored in the variable `names`. Let's say we wanted to greet each person in this array by saying "Hello, ____. So good to see you! Your hair looks amazing today."

#### Using a `for` loop with an array

Example 1a:
```javascript
for(let i = 0; i<names.length; i++){
  console.log("Hello, " + names[i] + ". So good to see you! Your hair looks amazing today.")
}
```

The property `array.length` is a built-in property that always contains the length of the array, so using `names.length` as our second statement means this code will work for any length of array.

In `friends.js` there is another array stored in the variable `nicknames`.
Challenge students to have the computer log out "____'s nickname is ____" for each person?

Example 1b:
```javascript
for(let i = 0; i<names.length; i++){
  console.log(names[i] +  "'s nickname is " + nicknames[i])
}
```

> Teachers note: Depending on where you think the students are in their understanding, you can either have them work independently on the previous example or directly show them the code. There will be plenty more practice in the upcoming lab.

Ask students why storing the name and the nickname in separate arrays is not the most useful data structure.

We can use a `for` loop to create an array *of objects*. Each object will represent one person, and have "Name" and "Nickname" keys for storing that person's specific values.

Here's what that might look like:

Example 1c:
```javascript
// Create a new array to store our more complex people objects
let people = []
for(let i = 0; i<names.length; i++){
  // Create a blank person object for each name
  let person = {}
  // Add that person's name as a key-value pair in the person object.
  person["Name"] = names[i]
  // Add that person's Nickname as a key-value pair in the person object.
  person["Nickname"] = nicknames[i]
  // Add the entire person object to the people array.
  people.push(person)
}
// Log out the final result.
console.log(people)
```

Now that we have our new `people` array, refactoring our original for loop can look a lot clearer.

Example 1d:
```javascript
for(let i = 0; i<people.length; i++){
  console.log(people[i]["Name"] +  "'s nickname is " + people[i]["Nickname"] )
}
```

## Iteration with map

`for` loops are awesome, but you may have noticed that only example 1c showed how to save the changes you make in a for loop, and in most situations, you want to save the output of a for loop for later use in other contexts.

Let's keep using our array of objects called `people` and see what it takes to SAVE (instead of console.log) the results of creating these quick nickname bios ("____'s nickname is ____").

```javascript
// Create a variable to save the results in. It will start empty:
let bios = []
// Iterate over the people, pushing each person's bio to to the bios array
for(let i = 0; i<people.length; i++){
  bios.push(people[i]["Name"] +  "'s nickname is " + people[i]["Nickname"])
}
// Log the results to see if it saved our info as expected.  
console.log(bios)
```

#### Save results faster with `.map()`

The `array.map()` method basically creates a parallel new array to the one you start with. It doesn't distort the original, and the new parallel array always comes out the same length as the original.

Let's once again try to refactor our code to console.log "____'s nickname is ____" using the map method instead.

Example 2a:
```javascript
let bios = people.map(person => {
  return(person["Name"] +  "'s nickname is " + person["Nickname"])
})
console.log(bios)
```

Here are the key differences:
* You can create the resulting array (`bios`) on the same line as you use the map function - this makes our code more streamlined.
* You can create a placeholder for each item in the original array. In this case, we're using the name `person` for readability, but it could be anything. This placeholder for each item is sometimes called the **iterator** or the **constant of iteration**, and it essentially is a more readable way of writing `people[i]`.
* Instead of using `bios.push()` to manually create an array the map method uses `return` to create it automatically.

#### A Simpler `.map()` Example

Most students need another example, as this is really confusing the first dozen times you see it.

The simplest example is probably to think of a list of numbers: `nums = [3,10,1,25]`
* Ask students to create the map of doubles: `doubles = [6, 20, 2, 50]`
* Ask students about the length of each of these arrays.
* Prompt someone to make the realization that a map of an array will always be the same length as the original.

Here's what that would look like in JavaScript:

```javascript
let nums = [3,10,1,25]

let doubles = nums.map(x => {
  return(2 * x)
})
console.log(doubles)
```

Reading this aloud sounds something like this:
* "Let doubles be a map of nums"
* "For every number (x) in the original, save/return 2 times that number"

Then trace this with specific data, scaffolding the question less and less each time:
* "When we're mapping over this array and we're at the first spot where x is 3, what should we return to the first spot of our map?"
* "When we're at the second spot, what should we return to the second spot?"
* "What will we return for the third spot?"


We can also use the map function to create new HTML elements. Instead of just printing each string to the console, let's create a list of elements we could add to our site.

Example 2b:
```javascript
let greetingElements = people.map(person => {
  return("<h5>" + person["Name"] +  "'s nickname is " + person["Nickname"] + "</h5>")
})
```

Once you have an array of greeting elements (or *any* HTML elements, really), getting those elements on screen can be done any number of ways.

#### Mini-Challenges

* Add two more keys to each object in the `people` array: one for a person's `age` and one for their favorite `animal`.
* Console.log "Hey! My name is ____ but my friends call me ____. I am ____ years old and my favorite animal is a _____" for each person.
* Use a map to save all of these longer bios in a variable.
* Use anotehr map to save these longer bios, but this time wrap them in `h3` tags.
* Stretch: Add another key to each person object in the `people` array for where they were born. Then, create a map of elements for each person with the following strings: "My name is ____ and I'm from ____." If they are from *your* borough, have it display something special. For example, one student from the Bronx had his program display that they are from "DA BOOGEY DOWN BRONX."

## Iteration with forEach

The last form of array iteration is perhaps the simplest and most readable, but it's also the least versatile. The `.forEach()` method works exactly the same as `.map()`, except instead of returning a copy of the original array, it returns nothing.

Why use it if it has *less* functionality than `.map()`? Generally, `.forEach()` triumphs with the most readable code.

With that in mind, be aware that since it uses a function (just like `.map()` does), sometimes certain syntax like `return` statements and local variables will behave differently than you might expect. If you're creating conditionals, algorithms, or other complex behavior, a standard `for` loop might accomplish that more simply and efficiently.

The best use cases for a `.forEach()` loop are when you're sure you want to DO something for every single item in an array (there's no stopping early, so it's not often the most efficient), and you also really don't care about saving the results.

#### ForEach examples

```javascript
people.forEach(person => {
  console.log(person["Name"] +  "'s nickname is " + person["Nickname"])
})
```

In this example, the syntax is identical to the map syntax. You have an array (`people`), an iterator (`person`), and since you only want to console log the results, you don't need to save them anywhere.

Another case where `.forEach()` is perhaps the best solution when adding event listeners to multiple similar items on an HTML page using JavaScript.

```javascript
// Select all elements on an HTML document with the class="clickMe"
const allClickButtons = document.querySelectorAll(".clickMe")

// Iterate over that array of buttons...
allClickButtons.forEach(clickButton => {
  // ...and add an event listener to each. That click event should trigger...
  clickButton.addEventListener("click", (e)=>{
    // ...this code block that logs out a message with that button's HTML ID.
    console.log(`You pressed the ${clickButton.id} button`)
  })
})
```

This example is also a bit complicated in that it nests two levels deep. The first arrow function is part of our `.forEach()` loop, and the second arrow function is the event listener callback. This example combines two powerful tools, and is probably the most authentic context in which you might see a this type of loop.

## Close

Ask students which syntax they like the best. Then review these use cases:

#### `for` loop iteration
* Can iterate over numerical ranges OR over arrays.
* Is the most similar to a wide variety of other languages.
* Is the most versatile (can be used to do everything that the others can)
* Can be exited/stopped at any point with the `break` keyword.
* Is often the hardest for beginners to read.
* May loop infinitely or not at all when one of your three statements is buggy.

#### `.map()` iteration
* Can only iterate over arrays.
* Best when you want to save your results.
* Is slightly more readable.
* Does not loop infinitely (unless you modify the original array).
* Is very difficult to exit/stop early.

#### `.forEach()` iteration
* Can only iterate over arrays. 
* Best when you do **not** care about saving your results.
* Is usually the most readable.
* Does not loop infinitely (unless you modify the original array).
* Is very difficult to exit/stop early.
