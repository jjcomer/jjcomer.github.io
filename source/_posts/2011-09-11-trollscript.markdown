---
layout: post
title: "Trollscript"
date: 2011-09-11 16:32
comments: true
categories:
- Clojure
- trollscript 
---
Well, I haven't been doing much in the way of coding over the last couple weeks, but today that changed. I came across [Tom Bell's ruby implementation](https://github.com/tombell/trollscript) of a trollscript interpreter, and figured that the clojure community needs an interpreter too. A couple hours later and I had whipped up my first version of a [trollscript interpreter](https://github.com/jjcomer/trollscript).

<!--more-->

##So what is trollscript you might ask...

Trollscript is a dialect of brainfuck (and by dialect I mean the symbols have just been swapped). The following is the Hello World example from Tom Bell's site:

    Trooloolooloolooloolooloolooloolollooooolooloolooloolooloolooooolooloolooloolooloolooloolooloooooloolooloooooloooloolooloololllllooooloololoooooololooolooloolooloolooloololoolooolooloololooooooloololooooloololooloolooloolooloolooloolooloolooloolooloololooooolooolooloololooollollollollollolllooollollollollollollollollloooooololooooolooll.

Which, as expected, produces:

    Hello World

The language has a 30,000 (this is arbitrary) byte data array which is read and written to in a tape like manner. To make my space usage a little more efficient the data array is implemented as a hash, which will only grow as it is accessed.

##The Commands

###Delimeters
* **Tro** all trollscripts begin with this
* **ll.** all trollscripts end with this

###Pointer movement
* **ooo** increments the data pointer
* **ool** decrements the data pointer
* **olo** increases the byte at the data pointer by one
* **oll** decreases the byte at the data pointer by one

###Input/Output
* **loo** output the char (byte) at the data pointer
* **lol** input one byte and write the value to the byte under the data pointer

###Control mechanisms
I implemented these as memoized functions, so they should be pretty quick.

*  **llo** if the byte under the data pointer is zero, increment the program counter to point to the instruction _after_ the matching **lll**
*  **lll** if the byte under the data pointer is non-zero, decrement the program counter to point to the instruction _after_ the matching **llo**

##The Code
{% gist 1210073 %}