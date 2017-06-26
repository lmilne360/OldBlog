---
layout: post
title:  "Adding pages to your Jekyll Blog"
date:   2017-06-25 23:53:33 -0400
---


To my fellow web development students, perhaps you've reached a point where you're tired of your Jekyll generated blog looking like a carbon copy of everyone else's. Or perhaps you don't even have a Jekyll generated blog (the one that was set up by Flatiron), which in this post is not for you. For those in the former category, this brief post is aimed at you and will hopefully aide you in making your personal blog a bit more, well, personal.

To kick things off, let's go over what Jekyll is. Prior to customizing my blog, I've only heard about Jekyll but had no idea what it actually was. To spare you a similar embarrassment, Jekyll is, simply put, an open sourced static site generator written in Ruby. What this means is that instead of storing your content in a database, it takes said content and renders the markdown into a template that is ready to be served as a static ( plain HTML, no server side scripting necessary) site. 

Now that we know what Jekyll is, let's  move on to actually changing our blog. Considering that we already have a Jekyll generated blog, the first step to making changes is cloning the GitHub repository of the blog (if you haven't done so already) and going into the directory via command line. Next, I would recommend making another branch to play around on, we wouldn't want to mistakenly push incomplete changes to the master branch. On this new branch, you may then open up the directory in your preferred text editor and then run the local server to view live changes.

`jekyll serve --watch`

With the server running and watching for changes, we can alter our blog. Looking at our root directory you may see some directories such as `_includes`, `_layouts`, `_posts` and `_site`. We will not be working in these, but I'll sum it up for general knowledge. The  `_includes` directory will have reusable partials that be applied to your layouts which are stored, you guessed it, in the `_layout` directory. Your blog posts are stored in the `_posts`  folder in the format of `year-month-day-title.markup` with markup being either `html` or `md`. Every time your run ` jekyll build` your files and folders get compiled down into the `_site` folder, ready to be displayed.

Creating a new page on your Jekyll blog is fairly straight forward.  It is as simple as adding a new HTML file in your main directory. For example, to create a project page I would just create a `projects.html` file in the root directory. In that file, I'd then be sure to include the layout and any other necessities in the front matter. The front matter is basically a YAML block where you can set pre-defined variables such as layout, or custom variables of your own.  These variables must be assigned within a triple-dashed block. An example project page would look like this:

```
- - -
layout: default
title: Projects
- - -

 the rest of your content
```

This is pretty much it for adding pages to your blog. You can go even further and add custom layouts per pages or even separate styling. Just be sure to include a tag in the front matter and make sure the files are referenced correctly (your custom CSS file should be in the CSS folder and included in the header) within the page.
