---
layout: post
title: "Now With More State"
date: 2011-07-30 21:44
comments: true
categories: 
- Clojure
- State Machines
- TodoClj
---
So I managed to sit down tonight and add state passing to the state machine. It now appears to be time to add support for doing **actual** things.

As I was writing the *init* function I was questioning what options will truly be required. I may want to cache the file contents in memory, which can be kept in the state hash. We shall see!

{% gist 1116199 %}

Hopefully tomorrow I will have some time to sit down and add in at least the create.