---
layout: post
title: "My First Clojure Library"
date: 2011-08-06 07:56
comments: true
categories: 
- Clojure
- cljcolour
---
I just pushed my first Clojure library to [CloJars](https://clojars.org/cljcolour) called [cljcolour](https://github.com/jjcomer/cljcolour). In my attempt to emulate Todo.txt, I needed the ability to colour my terminal output. Apparently there is no built in way to do this (I'm not even sure if there is an easy way to do this in Java). A little googling later and I found ANSI escape characters for colouring text, and they are disgusting. With cljcolour it is now easy to add both fore and background colour to your text output.

I have only tested this on my mac, so no guarantees when it comes to windows. I have also noticed that the REPL will only apply one colour (either the fore or the background) to your string. Both colours do work when running your application from the command line.

###Usage
```clojure
    ;Probably the easiest usage is to create painters
    (def bee-painter (create-painter black yellow))
    (bee-painter "Hello World")
    
    ;You can also define fore and background combinations
    (def bee-colour (create-new-colour black yellow))
    (def bee-painter2 (create-painter bee-colour))
```

<!--more-->

###The Code
{% gist 1128886 %}