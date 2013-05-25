---
layout: post
title: "TodoClj 1.0.0 Is Done"
date: 2011-08-09 21:14
comments: true
categories:
- TodoClj
- Clojure 
---
I have finished the first version of [TodoClj](https://github.com/jjcomer/TodoClj). Please check it out. Note that I have put almost no error checking into the parser, therefore things will crash if not perfect. Windows users should compile from source (to get version 1.0.1) since the ANSI codes used to colour the output do not render and the new version prevents colour from being rendered when run on Windows. If you have lein installed compiling is as easy as:
    lein uberjar

<!--more-->

##Usage
Usage pretty much emulates Todo.txt. The following commands assume you have created a batch/shell script called *Todo*.

###Batch File
    @echo off
    java -jar TodoClj.jar %*
###Add task
    $ Todo add "My new task"
    TODO: 'My new task' added on line 1
You can also define projects (+) and contexts (@) within a task by prefixing words with the corresponding symbol 
###List task
    $ Todo ls
    002:	Another task
    001:	My new task
You can also filter by adding the projects and/or contexts you wish to filter the list on
    $ Todo ls +myProject @someContext +anotherContext
###Complete a task
    $ Todo do 1
    $ Todo ls
    002:	Another task
    001:	X   My new task
###Add priority
    $ Todo pri 2 A
    $ Todo ls
    002:	(A) Another task
    001:	X    My new task
Priorities can range from A-Z
###Filter on priority
    $ Todo lsp A
    002:	(A) Another task
###Remove priority
    $ Todo depri 2
    $ Todo ls
    002:	Another task
    001:	X   My new task
###Remove completed tasks
    $ Todo clean
    $ Todo ls
    001:	Another task