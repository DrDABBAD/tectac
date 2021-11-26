---
title: MongoDB Shell (mongosh)
date: 2020-09-10 00:00:00 +0300
description: # Add post description (optional)
img: ./js-1.png # Add image post (optional)
tags: [mongosh, Javascript] # add tag
---

Mongosh is a fully functional JavaScript and Node.js 14.x REPL.

## How to install mongosh

## How to connect to MongoDb database

## Running the REPL editor

## How does this differ from node

### Install MongoDB Driver

C:\Users\Your Name>npm install mongodb

In node project

var mongo = require('mongodb');

### Create a database

```js
var MongoClient = require('mongodb').MongoClient;
var url = "mongodb://localhost:27017/mydb";

MongoClient.connect(url, function(err, db) {
  if (err) throw err;
  console.log("Database created!");
  db.close();
});
```

run demo

C:\\Users\\Your Name>node create_mongo_db.js

## Resources

[Node Mongo with docker](https://medium.com/zenofai/how-to-build-a-node-js-and-mongodb-application-with-docker-containers-15e535baabf5)