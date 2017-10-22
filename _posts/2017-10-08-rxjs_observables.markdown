---
layout: post
title:      "Rxjs Observables"
date:       2017-10-08 23:58:36 -0400
permalink:  rxjs_observables
---

Reactive-Extensions for JavaScript (or RxJS) introduces the concept of Observables to Angular. If you have been using version 1 of Angular then you are likely comfortable using Promises. And, while you might think that an Observable is just like a Promise you might be surprised (as I was) to learn that they are in fact very different.

First, Promises are eager and are executed immediately. Observables are not eager and are only executed when subscribed to.

Second, Promises are asynchronous. Observables can be either synchronous or asynchronous.

Third, Promises are expected to return only a single value (like a function). Observables can return zero, one or more (infinitely) values.

Let me get to the point. A subscription is created when we subscribe() to an observable. And it is important that we unsubscribe from any subscriptions that we create in our Angular components to avoid memory leaks
