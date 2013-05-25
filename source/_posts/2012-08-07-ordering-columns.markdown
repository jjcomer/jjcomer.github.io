---
layout: post
title: "Ordering Columns"
date: 2012-08-07 21:39
comments: true
categories:
- Clojure
---
One of my favourite things about Clojure, is constantly discovering
new, and usually shorter ways of re-writing code. An example I
discovered today has to do with maintaining a particular ordering in
a map. When creating html lists using hiccup one needs to make sure
the columns of the table all line up. This can be difficult when
using a map since the ordering of a map is not defined.

Fear no longer, today I discovered **sorted-map-by**. This creates a
map which maintains an order as defined by a comparator. So here is the easy way I came up with to keep a map in a
particular ordering:

{% gist 3290950 %}
