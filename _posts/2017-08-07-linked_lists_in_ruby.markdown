---
layout: post
title:  "Linked Lists in Ruby"
date:   2017-08-07 03:44:48 +0000
---


In a recent practice question, I was met with the task of creating a linked list in ruby.  Being that I have encountered similar data structure problems before, I thought it'd be proactive to talk about linked lists for a bit.  The biggest challenge I've encountered pertaining to linked list in ruby is that most of the resources available online are writing code in C, as the data-structure has more necessity in languages with manual memory allocation. Due to this issue, I take it upon myself to shed some light on linked lists for my fellow ruby programmers.

Firstly, a linked list is a data structure that represents a sequence. It is a collection of nodes that each contain data as well as a pointer to the next element in the list.The reason linked lists are such a popular data structure is due to memory management. It allows elements (nodes) to be added at the beginning and end of the list without having to reallocate or reorganize the entire data structure.

In ruby arrays are mostly used in place of linked list. The downside of using an array is that whenever an element of the array is deleted, excluding the last element, every succeeding element as to be reindexed. The same is true for inserting an element at a specific index. The advantage, however, is that accessing specific elements in an array is relatively easy in comparison to a linked list. For example, to access a specific element in a ruby array, one would just have to call that index, whereas in a linked list you would be required to scan every element until you find that specific one.

Despite the disadvantages (and advantages),  Linked Lists are a data structure you are sure to encounter, especially during technical interviews. For that reason, it is important to explore the implementation of a linked list.

In ruby, you'd first want to define a node class, which is similar to the elements that would be placed in an array. In that class, you would want an attribute for the data, as well as a pointer which will lead to the succeeding element. A simple node in ruby would look like this:
