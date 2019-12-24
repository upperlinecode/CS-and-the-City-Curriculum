# Storing Data with JSON & Firebase

## Learning Objectives

- SWBAT set up a Firebase account
- SWBAT initialize a Firestore database
- SWBAT write data to Firestore
- SWBAT read data from Firestore
- SWBAT update data in Firestore
- SWBAT use Firestore as part of a React component

## Sequence

1. [Launch](#launch)
2. [JSON Review](#json-review)
3. [Firebase's Firestore](#firebase's-firestore)
   1. [CRUD: Create, Read, Update, Delete](#crud-create-read-update-delete)
4. [Setting Up Firestore](#storing-to-firestore)
   1. [Introduction to Databases](#introduction-to-databases)
   2. [Getting Started](#getting-started)
5. [Using Firestore](#using-firestore)
   1. [Writing/Adding Data to Firestore](#writingadding-data-to-firestore)
   2. [Reading from Firestore](#reading-from-firestore)
   3. [Updating in Firestore](#updating-in-firestore)
   4. [Deleting from Firestore](#deleting-from-firestore)
6. [Firestore in React](#firestore-in-react)
7. [Close](#close)

## Launch

Click on this link and see if you can figure out what this data describes: [https://data.cityofnewyork.us/resource/vfnx-vebw.json](https://data.cityofnewyork.us/resource/vfnx-vebw.json)

### Questions

- Do the property names give you any indication of what information the data captures?
- Come up with three questions you might try to interrogate using this data. 

## JSON Review

Examine this (slightly better formatted) sample of the data linked above:

```javascript
[
  {
    "x": "-73.9561344937861",
    "y": "40.7940823884086",
    "unique_squirrel_id": "37F-PM-1014-03",
    "hectare": "37F",
    "shift": "PM",
    "date": "10142018",
    "hectare_squirrel_number": "3",
    "combination_of_primary_and": "+",
    "running": false,
    "chasing": false,
    "climbing": false,
    "eating": false,
    "foraging": false,
    "kuks": false,
    "quaas": false,
    "moans": false,
    "tail_flags": false,
    "tail_twitches": false,
    "approaches": false,
    "indifferent": false,
    "runs_from": false,
    "geocoded_column": {
      "type": "Point",
      "coordinates": [
        -73.9561344937861,
        40.7940823884086
      ]
    },
    ":@computed_region_f5dn_yrer": "19",
    ":@computed_region_yeji_bk3q": "4",
    ":@computed_region_92fq_4b7q": "19",
    ":@computed_region_sbqj_enih": "13"
  },
  ...
]
```
> From the [2018 Central Park Squirrel Census - Squirrel Data](https://data.cityofnewyork.us/resource/vfnx-vebw.json).

By now you should be comfortable with JSON, but it's worth a refresher here before we jump into storing data on Firebase.

- JSON is usually made up of objects and arrays. Above is an array (the `[]`) of objects (the `{}`).
- Objects can themselves be made up of objects and arrays, e.g. `"geocoded_column"` is an object which contains the array `"coordinates"`.
- Most of the data you will see from NYC Open Data will have a fairly flat (non-nested) data architecture. This way of storing data can be useful because it enables a developer to easily address parts of records with dot notation, e.g. `record.running` is `false`, or to get a value nested in an object and then nested in an array: `record.geocoded_column.coordinates[0]` would yield `-73.9561344937861`.

## Firebase's Firestore

Databases enable users to store data in a centralized location so that data can be available to them irrespective of the device they use. Additionally, databases allow developers to centralize where and how data is stored so they can make sense of a broad set of information.

Firebase is a database solution from Google which has a lot of different products and features. Here, you'll be introduced to Firebase's [Firestore](https://firebase.google.com/docs/firestore) database. Firestore is an object store, meaning it can store each new bit of data in its own record. What's really revolutionary about Firestore, however, is that adding, updating, or deleting data can trigger an event that can be used by a developer to do something else; the real-time call-and-response has many useful applications.

> Read more about Firestore in their [documentation](https://firebase.google.com/docs/firestore).

- If you've already done the [API mini-unit](./react-apis.md), you can imagine Firestore as setting up your own read/write API.

### CRUD: Create, Read, Update, Delete

There are 4 main operations a database needs to be able to do: create, read, update, and delete.

- Creating data means making a new record in the database.
- Reading data means finding a record in the database and getting that data.
- Updating data means finding one or more records in the database and changing them.
- Deleting data means finding one or more records in the database and removing them from the database.

## Setting Up Firestore

Although Firestore is fairly language agnostic and you can use it with many different programming languages, the remainder of this lesson will use Firestore with React.

And because we'll be using React, you should also review the lesson on [Lifecycle Methods](passing-state-lifecycle-methods.md#lifecycle-methods) if you need a refresher. As you'll recall, lifecycle methods are part of how React renders components to the DOM. Therefore, when a component is **Mounted** or **Updated**, it may be necessary to include or update the data associated with the component.

### Introduction to Databases

A database is a place where data is stored and from which it can be retrieved. Although there are many different kinds of databases, Firestore uses a very flexible database model called a "Document Store".

The most granular unit of a document store is a "document". A document is a set of properties and values that together relate to a unit of data: an article, a user, a product, a place, etc. The document can expand to include as many or as few properties as it needs to, and very importantly, the properties do not all have to be defined when the document is first created. The properties of a document can have values that are any type of data, from strings or numbers to arrays, objects, sets, etc. And those values can also contain nested arrays and objects and can get quite complex. The beauty of the document store is how flexible the structure of a document can be.

Documents are grouped together in "collections", and although collections typically have documents representing similar data, they don't have to. Collections are most useful because they enable a developer or data scientist to know where to look for data.

Collections are grouped together and comprise the database.

### Getting Started

Check out this [step-by-step walkthrough to set up Firestore](json-firebase-setup.md) to get started. You should follow all of the steps to set up an account on Firebase and a first database in Firestore; that database should have at least one collection and at least one document in the collection.

At this point you should also have your `firebaseConfig` copied into your App in a file called `Firestore.js` and you should know the name of the collection you've created.

Now that we have a database with a collection and we've integrated our Firebase credentials into our React project, we're ready to start CRUD-ing!

## Using Firestore

It's best to think of Firestore as a place to store user data, user interactions, or user feedback. For example, Firestore is great at storing a user's account information, what a user has liked, or what a user had to say about something.

When developers think about collecting user data, it usually involves some type of user interaction, maybe a form the user fills out or a button the user clicks to indicate a rating or preference.

### Writing/Adding Data to Firestore

Writing to Firestore is quite simply done by:
- Indicating Firestore is the data's destination: `firebase.firestore()`
- Indicating what collection to write data to: `.collection("test")`
- Using the `.add()` function with the JSON object you want to store to the database

```javascript
// So you don't have to rewrite this each time you perform a database action
const db = firebase.firestore();

// Add JSON object to collection called "test" and store the response in userRef
let userRef = db.collection('test').add({
  fullname: 'First Last',
  email: 'email@domain.tld'
});
```

> Note: the response from Firestore when adding a new document will include the unique ID created by Firestore, e.g. `userRef.id`.

If you want to create your own `documentId` instead of letting Firestore create a unique ID for you, you can also use `.doc('documentId').set(data)` to add a new document with a `documentId` that you choose:

```javascript
let documentToAdd = db.collection('test').doc('first-last');
let addDoc = documentToAdd.set({
  fullname: 'First Last',
  email: 'email@domain.tld'
});
```

- For more on writing data to Firestore, see the [Firestore Documentation on Adding Data](https://firebase.google.com/docs/firestore/manage-data/add-data).

### Reading from Firestore

Reading data from Firestore uses a slightly different pattern than writing data because we need to know from which document we want to read data.

Given a `documentId`, we can read the document using:

```javascript
let documentToRead = db.collection('users').doc('documentId');
let getDoc = documentToRead.get();
```

While that gets the data, it doesn't do anything with the data or account for any errors in retrieving the data. To do something with the data we get, we can chain a `.then()` function and a `.catch()` function after `.get()`:

```javascript
let documentToRead = db.collection('users').doc('documentId');
let getDoc = documentToRead.get()
  .then(doc => {
    if (!doc.exists) {
      console.log('No such document!');
    } else {
      // Do something with the data here
      console.log('Document data:', doc.data());
    }
  })
  .catch(err => {
    console.log('Error getting document', err);
  });
```

- For more on writing data to Firestore, see the [Firestore Documentation on Reading Data](https://firebase.google.com/docs/firestore/query-data/get-data).

> Note: Firestore can also listen for real-time updates to data. For more on listening to data, see the [Firestore Documentation on Listening For Real-Time Updates](https://firebase.google.com/docs/firestore/query-data/listen).

### Updating in Firestore

Updating data in Firestore is a lot like adding or writing data, but instead of creating a new record we'll `.update()` the data for an existing one:

```javascript
let documentToUpdate = db.collection('users').doc('documentId');
let getDoc = documentToUpdate.update({'name':'Elizabeth Windsor'})
```

> Note: `.set()` will overwrite all data in a record while `.update()` will only change the indicated fields.

- For more on updating data in Firestore, see the [Firestore Documentation on Updating Data](https://firebase.google.com/docs/firestore/manage-data/add-data#update-data).

### Deleting from Firestore

To delete a document in Firestore, just indicate the `documentId` and use the `.delete()` method:

```javascript
let documentToDelete = db.collection('users').doc('documentId').delete();
```

You can also [delete particular fields in a Firestore document](https://firebase.google.com/docs/firestore/manage-data/delete-data#fields) using the `.update()` method and a JSON object in the form of `{fieldName: FieldValue.delete()}`.

- For more on deleting data in Firestore, see the [Firestore Documentation on Deleting Data](https://firebase.google.com/docs/firestore/manage-data/delete-data).

## Firestore in React

Below is a simple React component called `<User />` that stores a user's name and email address when they are submitted via a form. It demonstrates basic `.add()` functionality in Firestore. The component works like this:

1. There is a `<form>` element that handles an `onSubmit` event; when the `<form>` is submitted, it will perform the `addUser` method that is part of the component.
2. There are two `<input>`s in the `<form>`, one for the user's full name and one for the user's email address:
   1. Each `<input>` has an `onChange` event handler that fires each time the value of the `<input>` is changed. `onChange` performs the `updateInput` method that is part of the component.
   2. The `updateInput` method stores the value of the input in state, so each time the value of the input is changed, it is stored in state.
   3. Each `<input>` also displays the value stored in state as its value to ensure that the value of the input and the value stored in state are the same.
6. The `addUser` method:
   1. Prevents the default submit behavior which is to open a new tab/window.
   2. Sets the variable `db` to indicate the destination for where data will be written.
   3. Changes a setting for the database so a timestamp will be rendered along with the data.
   4. Adds new data to the database using the `.add()` method.
   5. Resets the state variables used to populate the inputs to be blank.

#### `User.js`

```javascript
import React from 'react';
import firebase from "./Firestore.js";

const User = () => {
  const component = new React.Component();
  component.state = {
    email: "",
    fullname: ""
  }

  component.updateInput = e => {
    component.setState({
      [e.target.name]: e.target.value
    });
  }

  component.addUser = e => {
    e.preventDefault();
    const db = firebase.firestore();
    db.settings({
      timestampsInSnapshots: true
    });
    const userRef = db.collection("test").add({
      fullname: component.state.fullname,
      email: component.state.email
    });  
    component.setState({
      fullname: "",
      email: ""
    });
  };
  
  component.render = () => {
    return (
      <form onSubmit={component.addUser}>
        <input
          type="text"
          name="fullname"
          placeholder="Full name"
          onChange={component.updateInput}
          value={component.state.fullname}
        />
        <input
          type="email"
          name="email"
          placeholder="Email"
          onChange={component.updateInput}
          value={component.state.email}
        />
        <button type="submit">Submit</button>
      </form>
    )
  }

  return component;
}
   
export default User;
```

#### `App.js`

```javascript
// Add import
import User from './components/User.js'

...

// Add User component to your app
<User />
```

#### No Direct Upload

Unfortunately, Firestore doesn't enable a direct upload of a JSON file, but if you're looking to do this there are some [straight-forward write-ups](https://levelup.gitconnected.com/firebase-import-json-to-firestore-ed6a4adc2b57) out there about how to do this in Firestore.

There are alternatives, however, including:
1. use a different Firebase product: the Real-time Database,
2. include static data locally in your app, or
3. use an API - see the [API mini-unit](react-apis.md) for more on this.

## Close

As you can see, Firestore is a powerful tool that can be used to create, read, update, and delete data in your application. It's worth spending some time thinking about how best to format the data you write to Firestore so you can readily [build visualizations](victory.md) or display feedback to users as a result of their interaction.
