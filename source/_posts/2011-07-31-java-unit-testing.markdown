---
layout: post
title: "Java Unit Testing"
date: 2011-07-31 08:47
comments: true
categories: 
- Java
- Unit Testing
- Reflection
---
I was digging around in a project I helped created for my intro Software Engineering class, and came across some useful helper methods I wrote for unit testing.

These methods allow you to call private methods and get/set the values of private class variables. In order to call the private members, I needed to use reflection, which as you can see is horrible in Java. Luckily I was able to write the methods using generics so they can very easily be reused. The downside is that this code will not compile using the standard oracle Java 1.6 (see the [bug report](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6302954)). This bug was supposed to be fixed in Java 7, but I haven't tested it yet. In the mean time there is no problem compiling the code using the OpenJDK.

{% gist 1116726 %}