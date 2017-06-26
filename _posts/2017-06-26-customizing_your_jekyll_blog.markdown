---
layout: post
title:  "Customizing your jekyll blog"
date:   2017-06-26 03:53:32 +0000
---


The more time I spent working with Jekyll, the more I appreciated the simplicity of the command line build process. Using separate programs to compile the code, optimise the images, upload the files and so on suddenly seemed so inefficient compared to typing in a simple command.

The perfect example: Before building and uploading my site, I want to check the images and compress them if possible. This ImageOptim adddon for the command line lets you do that by simply typing something like imageoptim --directory assets/img.

You don't want to end up with 10 different commands you have to remember and type in to publish your blog so we're simply gonna create our own. This, once again, is surprisingly easy. All you have to do is create a text file, name it something like publish-blog (no file extension necessary) and add your list of commands:
