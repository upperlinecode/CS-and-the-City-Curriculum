# Storing Data with JSON & Firebase

## Learning Objectives

- SWBAT 

## Sequence

1. [Launch](#launch)
2. [JSON Review](#json-review)
3. [Firebase's Firestore](#firebase's-firestore)
4. [Setting Up Firestore](#storing-to-firestore)
4. [Storing to Firestore](#storing-to-firestore)
5. [Reading from Firestore](#reading-from-firestore)
6. [Updating in Firestore](#updating-in-firestore)
7. [Deleting from Firestore](#deleting-from-firestore)
8. [Close](#close)

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

- If you've already done the [API extension](./react-apis.md), you can imagine Firestore as setting up your own read/write API.

### CRUD: Create, Read, Update, Delete

There are 4 main operations a database needs to be able to do: create, read, update, and delete.

- Creating data means making a new record in the database.
- Reading data means finding a record in the database and getting that data.
- Updating data means finding one or more records in the database and changing them.
- Deleting data means finding one or more records in the database and removing them from the database.

## Setting Up Firestore

Although Firestore is fairly language agnostic and you can use it with many different programming languages, the remainder of this lesson will use Firestore with React.

And because we'll be using React, you should also review the lesson on [Lifecycle Methods](passing-state-lifecycle-methods.md#lifecycle-methods) if you need a refresher. As you'll recall, lifecycle methods are part of how React renders components to the DOM. Therefore, when a component is **Mounted** or **Updated**, it may be necessary to include or update the data associated with the component.

### Getting Started

Unfortunately, Google's Firestore documentation doesn't have a Getting Started Guide for (Facebook's) React, so a quick google for "react firestore web" and some poking around yielded several helpful posts about setting up Firestore and integrating it with React. If you'd rather follow along with one of those, check out this [Medium post about React + Firestore](https://medium.com/get-it-working/get-googles-firestore-working-with-react-c78f198d2364).

To get up and running with Firestore in React, we need to do the following things:

1. Install the `firebase` library to our development environment
2. Sign up for a Firebase account
3. Add a new Firebase project
4. Integrate Firebase into our React app
5. Set up a database and collection in Firestore

Before you get started, you can either integrate Firestore into one of your existing React projects, or you can `git clone` [this repo (need to add/build this)](#) and follow along there.

### 1. Install the `firebase` library to our development environment

To install the firebase library to our development environment, we just need to:

```javascript
npm install firebase
```

Easy! You should now see `firebase` and a version number in your `package.json` file.

```javascript
"firebase": "^7.4.0",
```

### 2. Sign up for a Firebase account

From the Firebase homepage [https://firebase.google.com](https://firebase.google.com), sign in using a Google account or sign up and make yourself a new Google account.

![Firebase - Add project]()

Once you're logged in, you'll see a page where you can "Add project".

### 3. Add a new Firebase project

![Firebase - Create project]()

Tap the "Add project" button to add a new Firebase project. Give your project a name, e.g. `stranger-things`, and then choose your region/country. Go ahead and agree to the checkbox prompts and tap "Create Project".

### 4. Integrate Firebase into our React app

![Firebase - Add to web app]()

Next tap the "Add Firebase to your web app" button (since our React app is web-based). Then copy the code between the `<script>` tags, e.g.:

```javascript
var config = {
   apiKey: "AIzfhrwkKhDBFHbntnKhTahHjkNK6FG875dSB6y",
   authDomain: "typecode-76g33.firebaseapp.com",
   databaseURL: "https://typecode-76g33.firebaseio.com",
   projectId: "typecode-76g33",
   storageBucket: "",
   messagingSenderId: "547432956432"
};

firebase.initializeApp(config);
```

Back in your React app, let's make a new Component, e.g. `Firestore.js`. In `Firestore.js`, add the necessary `import` and `export` statements, and paste the code you copied above between those.

> Note: you can also change `var` to `const`.

```javascript
import firebase from 'firebase';

const config = {
   apiKey: "AIzfhrwkKhDBFHbntnKhTahHjkNK6FG875dSB6y",
   authDomain: "typecode-76g33.firebaseapp.com",
   databaseURL: "https://typecode-76g33.firebaseio.com",
   projectId: "typecode-76g33",
   storageBucket: "",
   messagingSenderId: "547432956432"
};

firebase.initializeApp(config);

export default firebase;
```

> Note: Don't copy and paste these config variables, they are just an example. You should use the configuration from your Firebase account.

### 5. Set up a database and collection in Firestore

![Firestore - Create database]()

Head back to Firebase, and choose the "Database" option from the left menu. On that page, find the Firestore section and tap the "Create Database" button.

![Firestore - Database security settings]()

For now we'll start our development in "test mode" which means anyone can read or write from our database.

> Note: when moving an app out of development and into production, Firestore suggests converting this security setting to "locked mode". When you do this, you'll need to set the security settings for your app related to who can `read` and who can `write` to your app. For more on this, check out [Firestore's Documentation on Security](https://firebase.google.com/docs/firestore/security/get-started).

![Firestore - Create collection]()

Now that you have a database, you need to create a collection within that database where records can be stored. You can think of this like the different worksheets within an Excel or Google Sheets spreadsheet.

To create a collection, tap the "Add Collection" option and give your new collection a name, e.g. `users` or `data` - it can be anything, but we'll use this name later to indicate where we want to write data to.

![Firestore - Document ID]()

Once you've clicked "Next", you'll be asked if you want to create a Document ID. We suggest leaving this blank so Firestore will generate a unique ID for you. Below the Documnt ID, you'll be asked to create an initial document in order to initialize the collection; add one or more data fields, e.g. `name`, but it's ok if we want to add different fields later.

Now that we have a database with a collection and we've integrated our Firebase credentials into our React project, we're ready to start CRUD-ing!

## Storing to Firestore

### Option A: Direct Upload

Unfortunately, Firestore doesn't enable a direct upload of a JSON file, but if you're looking to do this there are some [straight-forward write-ups](https://levelup.gitconnected.com/firebase-import-json-to-firestore-ed6a4adc2b57) out there about how to do this.

@JOLSON: Should we make a simple tool/interface to do this? e.g. put in your credentials and point to a file and it'll do the upload?

### Option B: Collect Data from a React Form

## Reading from Firestore

Some text here

## Updating in Firestore

- mirroring CRUD a bit, but although it is a combination in principle, it's a different function (as opposed to being a combination of reading then writing)
- Jolson: To update a record, just combine Reading and Storing, with a step to modify it in between!

## Deleting from Firestore

Some text here

## Close

Some text here

#### Questions for students

- Some text here
