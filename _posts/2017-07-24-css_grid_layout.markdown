---
layout: post
title:  "Setting up grid layout (CSS Grid)"
date:   2017-07-23 23:59:11 -0400
---

So one of the first things I had to learn as I started to explore CSS Grid layout was how to define my layout. As the name obviously states, CSS grid layouts allows you to define an area as a grid, with rows and columns, that allows you to place items are specific locations.

To get started with a grid layout, you'd first have to define a container and use CSS to set its display property as grid. There you go, your grid container is all set up. Well, not so fast. After defining a grid, you may want to add columns or rows for placements within your grid. This can be accomplished using the `grid-template-columns` and `grid-template-rows` property. These properties allow you to set the amount columns/rows you want and their sizes. They accept standard measurement units such as percentages(%) or pixels(px) and even a new fractional unit (fr). 

Since showing is better than telling; If I wanted to setup a grid that had 4 columns and three rows, with the middle row being automatically sized, it would like as such:

```
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 50px auto 50px;
}
```

That's the basic premise of setting up a basic grid container. Notice that setting up a number of rows or columns is as simple as supplying a size value that amount of times. You can also use `repeat` to set this up for when you don't feel like typing it all out. to accomplish the same amount of columns as above you can simply write:

` grid-template-columns: repeat(4, 1fr)` 

This sums up the basics of setting up your grid layout.
