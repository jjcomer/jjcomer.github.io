---
layout: post
title: "There Has to Be State"
date: 2011-07-30 15:33
comments: true
categories: 
- Clojure
- State Machines
- TodoClj
---
It occurred to me after I posted the prototype state machine that I had missed an important piece, State. I know that state is a naughty word when discussing functional languages, but an application must have a state. The bad taste surrounding state in functional languages is in reference to mutability of variables, as opposed to the application remembering which file it is acting upon.

It should be completely possible to enclose the current state of the application into a parameter for the state machine. Each action method will accept and return the state of the application stored in a hash. I will post a prototype of said functionality later tonight, assuming I don't get too distracted or see a shiny object.

I have also created the first draft of the state machine (in diagram form).
{% img /images/TodoStateMachine.png %}

On a side note, it is hard to find a good free diagramming tool. After trying out a couple I ended up settling on [Google Docs](http://docs.google.com) and the Draw tool. I had pretty much endless storage, could make drawings as large as I wanted, and could export into all sorts of formats.