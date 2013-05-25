---
layout: post
title: "Found Some Time to File Parse"
date: 2011-08-02 21:22
comments: true
categories: 
---
I was able to find some time tonight to do a little programming. The following code snippit will parse the Todo.txt file. I kept the structure of the file down to a minimum.
{% codeblock %}
T The First Task
D and The Second Task
{% endcodeblock %}
The first letter of the line will represent the status of the task (*T* being still Todo and *D* being Done). The code will read the entire file in and "hackishly" convert the line in to a vector. The first item is assumed to be either a *T* or a *D* and the remainder of the vector is the description, and is interposed with spaces to be a readable string.
{% include_code TodoClj Clojure/coreV1.clj %}