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

By now you should be comfortable with JSON, but it's worth a refresher here before we jump into storing data on Firebase.

- JSON is usually made up of objects and arrays. Above is an array (the `[]`) of objects (the `{}`).
- Objects can themselves be made up of objects and arrays, e.g. `"geocoded_column"` is an object which contains the array `"coordinates"`.
- Most of the data you will see from NYC Open Data will have a fairly flat (non-nested) data architecture. This way of storing data can be useful because it enables a developer to easily address parts of records with dot notation, e.g. `record.running` is `false`, or to get a value nested in an object and then nested in an array: `record.geocoded_column.coordinates[0]` would yield `-73.9561344937861`.

> This data is from the [2018 Central Park Squirrel Census - Squirrel Data](https://data.cityofnewyork.us/resource/vfnx-vebw.json).

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

- Point to Firebase documentation throughout

Although Firestore is fairly language agnostic and you can use it with many different programming languages, the remainder of this lesson will use Firestore with React.

And because we'll be using React, you should also review the lesson on [Lifecycle Methods](passing-state-lifecycle-methods.md#lifecycle-methods) if you need a refresher. As you'll recall, lifecycle methods are part of how React renders components to the DOM. Therefore, when a component is **Mounted** or **Updated**, it may be necessary to include or update the data associated with the component.

## Storing to Firestore

Some text here

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
