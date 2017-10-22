---
layout: post
title:      "Intro to Gulpjs"
date:       2017-10-22 22:16:04 +0000
permalink:  intro_to_gulpjs
---


Gulp.js is a Node.js based build and task automation tool.

Gulp.js has been adopted by developers because of its stream based approach of getting the tasks done rather than the configuration based approach followed by Grunt.js.

Stream based approach made developers to write less lines of code because of its pipelining feature which makes it faster.

Gulp.js can be installed on all OS: Various linux distros including CentOS, Ubuntu, Redhat, Debian, etc, Windows, MacOS.

We can automate and do various tasks using gulp. The following are few examples of what Gulp can do.

Minifying the css, js and images.
Automating pre-processor tasks like SASS and LESS.
Automated browser re-loading on changes to file.
Linting your js, css and html to ensure the standards.
Setting up a local web server.



### Installing Gulp

Open your terminal/command line and install gulp using the following command. Here we are installing gulp globally so that we can run it from anywhere on the system.

```
npm install gulp -g
```

### Create package.json using npm init

For adding gulp and required plugin modules from the npm repository as dev dependencies to the project, we will have to create “package.json” file.

We are keeping it as dev dependency because the plug-in which we a going to use is required on developer system only for development purpose. In other words, it is not going to be deployed on production server.

Here, “package.json” file tells npm what to be installed, when “npm install” command is run, by keeping in this directory.

This file keeps these dependencies listed in it which can be ported to other location/system/server and just by giving one command “npm install” you will get all the required packages listed in it installed and ready to be used.

You can use npm to create this file just by typing the following command while inside your project folder.

`npm init`
