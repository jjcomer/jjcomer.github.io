---
layout: post
title: "Tail Recursive State Machines"
date: 2011-07-28 20:21
comments: true
categories: 
- Clojure
- State Machines
- TodoClj
published: true
---
I was reading an article the other day which stated that a great method to use when learning a new language is to imitate software that you already use. In my attempt to fully grok Clojure I have decided to start small and imitate [todo.txt](http://todotxt.com/)

The first hurdle I always face when starting a new language is determining the basic architecture pattern to follow when writing an application. For some reason this is a topic which is not widely discussed or written about. Some languages, such as Objectuve-C,have a prescribed architecture which you are to follow, thereby making my difficulties moot. But clojure and the majority of other languages do not have this benefit. We are left to discover these patterns by ourselves.

Perhaps the intension is that one is supposed to trail and error and determine what works the best for themselves. Maybe the idea is that each application is different enough that there cannot be a default application pattern for a language. Web development seems to alleviate this problem by not dictating the pattern to the language, but instead to the framework with which one constructs their site. 

So, in light of this I am attempting to formulate an application pattern which I think will work with my thought patterns. I am intrigued by the concept of creating applications around the state machine model. The following code is a quick prototype I whipped up.

{% gist 1115436 %}

 The program loop represents the state machine which is the program. The looping is done with the trampoline command, which allows for tail-recursion optimization. This should be an easily extensible model. If states need to pass parameters, the parameters should be returned by the action function (action functions such as displayMenu) and then enclosed in the returning function. The only thing I am not overly happy with is the potential size of the program loop, but this should be something I can improve upon.