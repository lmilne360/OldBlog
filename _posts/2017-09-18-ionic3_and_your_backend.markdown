---
layout: post
title:  "Ionic3 and Your Backend"
date:   2017-09-18 03:30:02 +0000
---


I often see questions like “How do I use PHP/MySQL in Ionic?” or “Does Ionic work with X backend?” – these are reasonable questions, but it indicates a big misconception as to how integrating a backend with Ionic works. The technology that is used on the backend is completely irrelevant, as the backend and the Ionic front end exist in totally independent spaces.

Ionic does not integrate directly with your backend, it just communicates with it. In order to enable Ionic to integrate with a backend, your backend will need to implement some kind of API that the Ionic application can make HTTP requests to.
