---
layout: post
title:  "Adding an Express Server to Angular Project"
date:   2017-08-27 23:53:36 -0400
---


One of the most common stacks that accompany Angular as a web framework is the MEAN stack. MEAN simply stands for MongoDB, ExpressJS, Angular and NodeJS, and is a concept that came about a few years ago with the growing popularity of all those technologies, and the fact that you only needed to know one language, javascript, to get started.

### Setting up the backend

Assuming you already have an angular front-end set up, the first step is to install `express`. Express is a Nodejs framework used to write scalable APIs and server side code. This will handle your server and routing. In addition to express, we will also install `body-parser` and `mongojs` as a dependency, which is an express middleware that parses the JSON of a post request and stores it on `req.body`. In your console:

`npm install --save express body-parser mongojs `

Afterwards, create a  `server.js` file in the root of your application that will handle the server code and a folder (server) that will contain the files to handle our various endpoints in the application.
inside our server.js file, we must first get all our dependencies.

```
const express = require('express');
const path = require('path');
const http = require('http');
const bodyParser = require('body-parser');
```
Next, lets set up the file for handling our api routes. Insider our server folder, lets create a routes folder and within that an `api.js` file for handling our api routes. In our api file we need to set up our routes and database.

``` 
const express = require('express');
const router = express.Router(); //express router
const mongojs = require('mongojs');
const db = mongojs(connectionString, [collections]);

routet.get('/collention' (req, res) => {
  db.collection.find(err, collection){
if (err){res.send(err)}
res.json(collection);
}
});

module.exports = router

```
In this file, we used `mongojs` to connect to our database and set up a basic API route that returns a collection in our database. You can replace collection with any table in your database such as posts or todos. Back in our server file, we must send all  `api` requests to our api file we just created and all other requests to our index page

```
app.use('/api', api);

app.get('*', (req, res) => {
  res.sendFile(path.join(__dirname, 'dist/index.html'));
});

```

This sends all non `/api` requests to the index page in our build folder, which is commonly named `dist` or `www`. The final part of this is to then create the server on a specific port.

```
app.set('port', process.env.PORT || 3000);

app.listen(app.get('port'), 
()=> console.log('api running on port", app.get('port')) 
});
```
And with that, once we start our application it will output to the console the port that the api is running on.


