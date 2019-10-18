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
4. [Close](#close)

## Launch

You might know that computers are incredibly fast at performing calculations. But it's hard to wrap ones head around just HOW fast they are. In one second your average desktop computer can perform over a billions calculations. It would take you over 300 years with no breaks for you to do what a computer can do in one second!

Due to the speed at which computers can calculate, they are very good at performing specialized tasks - such as searching for primes numbers. The Great Internet Mersenne Prime Search is a project that looks for larger and larger prime numbers using distributed computer networks around the world. While checking for Mersenne Primes (which can be done using the formula 2^n - 1) can be a complex task, can you write sudo code for how you would program a computer to find every even number less than 10? Less than 1,000? Less than 100,000,000?

#### Questions for Students

* Share your sudo code with a partner - did they use a similar method? How are they similar? How are they different?
* Did your sudo code change for when you were checking the numbers less than 10 to when you were checking the numbers less than 100,000,000? If so, how did it change?

## Iteration with `for` loops

As we saw from the launch, when we want a computer to repeat a task multiple times, the use of a **loop** make the task much easier and the code much more succinct. In this first section, we will explore how we can repeat a task multiple times using a `for` loop.

### The structure of a `for` loop

Each `for` loop has a set structure. Let's look at an example:

```javascript
for(let i = 0; i<5; i++){
  //DO SOMETHING
}
```

A `for` loop takes **three** arguments separated by a semicolon. The first argument is the starting value of the loop. This loop will begin with the number 0 (thinking of our launch, if we were checking what numbers are even you might want to start at a higher number, such as 1).

The second argument tells the computer when to stop. In this example, after what number will the loop stop running?

The third argument is how much we want to increment by every time the loops runs. In this example, `i` will increase by 1 (`i++` is shorthand for `i = i + 1` or `i += 1`).

#### Questions for Students

* Write a for loop that starts at 0, ends at 20, and increments by 1
* Write a for loop that starts at 10, ends at 100, and increments by 20.
* Stretch: Write a for loop that starts at 100, end at 10, and decreases by 5

### Practice with `for` loops

> Some data has already been stored for you in the [`friends.js`](javascript-iteration/friends.js) file. It's also copied here:

```javascript 
const names = ["Yhadira", "Kadiatou", "Isiah", "Yadelin", "Darius"]
const nicknames = ["Deary", "Kadi-B", "Izzy", "Loki", "Yaddy", "DRock"]
const age = [22,28,27,33,29]
const favAnimal = ["Cat", "Ferret", "Dog", "Sloth", "Zebra"]
const born = ["Queens", "Bronx", "Manhattan", "Bronx", "Brooklyn"]
```

In `friends.js` there is an array stored in the variable `names`. Let's say we wanted to greet each person in this array by saying "Hello, ____. So good to see you! Your hair looks amazing today."

How could we do this using a `for` loop?

Example 1a:
```javascript
for(let i = 0; i<names.length; i++){
  console.log("Hello, " + names[i] + ". So good to see you! Your hair looks amazing today.")
}
```
> To check if the code is working, tell students to open index.html in their browsers and check the console.

Remember, arrays start at index 0, so we want to start at 0 and run the whole length of the array. `array.length` returns the length of the array, which is why we used that as our second argument.

In `friends.js` there is another array stored in the variable `nickname`. How can we have the computer console.log "____'s nickname is ____" for each person?

Example 1b:
```javascript
for(let i = 0; i<names.length; i++){
  console.log(names[i] +  "'s nickname is " + nicknames[i])
}
```

> Teachers note: Depending on where you think the students are in their understanding, you can either have them work independently on the previous example or directly show them the code. There will be plenty more practice in the upcoming lab.

You might be thinking "storing the name and the nickname in separate arrays is not the most useful data structure." You'd be right. What if we wanted to create an array of objects that had "Name" and "Nickname" keys for storing these values for each person. How could zip these two arrays into a single object using a `for` loop?

Example 1c:
```javascript
let people = []
for(let i = 0; i<names.length; i++){
  let person = {}
  person["Name"] = names[i]
  person["Nickname"] = nicknames[i]
  people.push(person)
}
console.log(people)
```

You might notice we used `people.push` in this for loop. `array.push` adds a new element to end of the existing array. We use it here to add each `person` object to our `people` array.

Now that we have our new `people` array, how can we refactor our previous code to console.log "____'s nickname is ____" for each person?

Example 1d:
```javascript
for(let i = 0; i<people.length; i++){
  console.log(people["Name"] +  "'s nickname is " + people["Nickname"] )
}
```

## Iteration with map

`for` loops are useful in some situations, but using the `array.map()` method has many benefits when looping through an array.

### Why map?

The `array.map()` method has two major benefits when looping through arrays. First, the map method returns a new array and leaves the original array unaffected. Second, it leads to cleaner, more readable code.

Let's once again try to refactor our code to console.log "____'s nickname is ____" using the map method.

Example 2a:
```javascript
let bios = people.map(bio => {
    return (bio["Name"] +  "'s nickname is " + bio["Nickname"])
  })
console.log(bios)
```

In this example, the map method returns a new array and leaves the original `people` array unaffected.

We can also use the map function to create new HTML elements. Instead of just printing each string to the console, let's add these strings to our website.

Example 2b:
```javascript
let greetings = document.querySelector("#greetings")
people.map(bio => {
    return (greetings += "<h5>" + bio["Name"] +  "'s nickname is " + bio["Nickname"] + "</h5>")
  })
```

Viola! By using loops we are harnessing the power of what computers do best - performing repetitive tasks very quickly!

#### Mini-Challenges

* Add two more keys to each object in the `people` array. These should store each persons age and favorite animal.
* Console.log "Hey! My name is ____ but my friends call me ____. I am ____ years old and my favorite animal is a _____" for each person.
* Add the sentence above to the webpage by changing the innerHTML of div with the id of `introductions`.
* Stretch: Add another key to each person object in the `people` array for where they were born. Then, add the following sentence to the webpage for each person: "My name is ____ and I'm from ____." If they are from your borough, have it display something special. For example, one student from the Bronx had his program display that they are from "DA BOOGEY DOWN BRONX."

## Close

Remember to gather student feedback on this lesson. In addition to the standard close, consider priming students for feedback with the following questions.

#### Questions for Students

* In your own words, what is the difference between for loops and the map method?
* In what situations would we prefer a `for` loop? In what situations would we prefer the `.map()` method?
