---
layout: post
title:  "CSS Grid Template Areas"
date:   2017-07-30 23:50:25 -0400
---


Previously, we've defined how to set up a grid layout using `grid-template-rows` and `grid-template-columns`. The children of a grid container are called grid items. They can be positioned in the different parts of the grid using the placement properties `grid-row-start`, `grid-row-end`, `grid-column-start`, and `grid-column-end`. But in most cases, you’ll be using the shorthands `grid-row` and `grid-column` with a value of the row or column number where you want to place the item.

Using the numbering methods we’ve described so far works just fine, but Grid Template Areas can make defining layouts even more intuitive.

Specifically, they allow us to name areas on the grid. With those areas named, we can reference them (instead of line numbers) to position our items. Let’s stick to our current demo for the moment and use it to make ourselves a rough page layout comprising:

header
main content
sidebar
footer

We define these areas on our grid container, almost as though we’re drawing them out:

```
.grid-1 {
    grid-template-areas:    "header header header"
                                     "main main sidebar"
                                     "footer footer footer";
}
```

Now we turn our attention to the items, ditching the grid-column and grid-row rules in favor of grid-area:

```
.item-1 {
  background: #b03532;
  grid-area: header;
}
.item-2 {
  background: #33a8a5;
  grid-area: main;
}
.item-3 {
  background: #30997a;
  grid-area: sidebar;
}
.item-4 {
  background: #6a478f;
  grid-area: footer;
}

```
Our first item is slotted into the header, spanning across all three header columns. Our second item is assigned the main content area, the third becomes our sidebar, and the fourth our footer. And these needn’t follow the source order either–.item-4 could just as easily be positioned in the header area.

As you can see, this makes laying out a page much easier.
