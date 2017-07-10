---
layout: post
title:  "Storing data in local storage"
date:   2017-07-10 01:51:23 +0000
---


One of the cool things about web development is the multiple ways of storing data. While a database is the most common method of storage,  sometimes you need to store information on a users' client instead of on the server itself. This is when other storages, such as cookies and local storage, comes into play. 

Since we'll be exploring local storage in this post, I figure I should first explain what it is. So local storage is an HTML5 object that allows users to store application data inside their web browser. Before local storage, client-side information used to be stored in cookies which were less secured and, after a buildup, slowed internet performance. With the onset of local storage, websites now had a larger, more secure way of storing user information without affecting performance.

So how does one use local Storage? Storing data in local storage is ridiculously simple. First, local storage can be accessed via the localStorage object in JavaScript. This object comes with two methods that make setting and getting data easy. The first of these methods is the `setItem()` method which, as you can guess, allows a user to save an item to local storage. The `setItem()` method takes two arguments, the first is the key for the information you're trying to store and the second being the value. Think of it as being the name of the data and the actual data itself.  

`localStorage.setItem('favoriteflavor', 'vanilla'); `

Receiving data from the local storage object is just as simple. The `setItem()` method takes one argument, the key of the data you're trying to access, and returns the value. Getting your favorite ice cream flavor from local storage is as simple as:

`localStorage.getItem('favoriteflavor');`

There's one aspect of local storage that's quite the annoyance. That is that you can only store data as strings. If you were to try to store an object in local storage, it would just be stored as an `[obect object]` string instead of an actual object. Thankfully, there's a simple workaround to this issue. By using the native `JSON.stringify()` method, one can convert their javascript object into a JSON string which the local storage readily accepts. When you're ready to retrieve the data, you'd simply call `JSON.parse()` to convert the JSON string back into a javascript object or value.

For visualization, let's say we had an  object for our favorite ice-cream flavor:

`var flavor = {name: "vanilla", fave: true }`

To store this object in local storage, we'd pass a stringified version into the local storage `setItem()` method:

`localStorage.setItem('favoriteflavor', JSON.stringify(flavor));`

This will safely convert our object into a JSON string and store it. Retrieving our object would then look like this:

` var flavor =  JSON.parse( localStorage.getItem('favoriteflavor') );`

That concludes the simple rundown of storing and retrieving information from local storage.

