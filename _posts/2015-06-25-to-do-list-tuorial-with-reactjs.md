---
layout: post
title:  "ToDo List Tutorial with ReactJS"
date: 2015-06-25 14:51:10
tags: tutorial react js
---


This course was an introduction to React Js and associated technologies. It started off with a very broad overview and some simple examples of how to build components using Bootstrap.

####App Demo
<span class="image fit no-overlay">
![Todo List with React](/images/todo.gif)
</span>

**src** [/udemy.com/learn-and-understand-reactjs][src]

It covered correct tooling including using Gulp build tasks. Gulp plugins used included:

* gutil - for Gulp logging
* vinyl-source-stream - for tidier Gulp streams
* browserify - for require JS dependencies
* watchify - for watching files
* reactify - for compiling JSX
* notifier - for growl-like error notifications
* server - for serving our app
* concat - for concatenating files
* sass - for compiling sass
* watch - for watching files for changes

The major project of the course was to build a simple Todo list that integrated with FireBase for data storage.

We used ReactFire & Firebase Node Modules for comunication API between our app & Firebase.

[src]: https://www.udemy.com/learn-and-understand-reactjs/#/
