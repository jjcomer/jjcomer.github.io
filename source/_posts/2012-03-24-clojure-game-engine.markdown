---
layout: post
title: "Clojure Game Engine"
date: 2012-03-24 13:17
comments: true
categories:
- Clojure
- Game Design
---

I recently attended an undergraduate thesis presentation where one of
the students created a javascript game engine from scratch. This got
me to thinking, what would a Clojure game engine look like. I have
played around with other Java gaming engines, such as
[Slick](http://slick.cokeandcode.com/). Slick is a really easy engine
to work with and lets you immediately focus on developing the game, not
contorting the engine to work for your game. Since Slick is so great,
why not just write a Clojure wrapper for it? The problem rests in
Slick's heavy dependence on the OOP paradigm. A wrapper would end up
causing the programmer to "fight" Clojure at every turn as we sneak
objects and, even worse, mutability into the engine. My goal is to have a
game engine which embraces the ideals of Clojure.


The design which I have been building in my head is an entity-oriented
engine (which I wrote about in a previous
[post](/blog/2011/11/06/entity-oriented-programming/)). A world
reference will be a bag for all the entities in the game. Entities
would only contain their state, and their categorizations. For example
you could have a player entity, and also have an entity for each
projectile currently alive in the game. An interesting idea would be
to make each processor of entities a different thread. This would
impose the problem of not being able to deterministically order their
execution, but the idea of creating a game based on independent
modules seems intriguing. My goal is to create a highly concurrent
gaming engine. A cool resource to check out is Rich Hickey's famous
[ant demo](https://gist.github.com/1494094) which was used to demo
Clojure's concurrency in the early days of the language. It is pretty mind blowing how much simulation
is packed into so little code (the whole thing is 300 lines, with
comments and license).


The rendering and world updating will be done by two (maybe more)
agents. Clojure's wonderful STM will trivially (maybe easy is the
better terminology :)) allow these tasks to be
independent. I haven't yet chosen what the renderer is going to be
yet, but this will be a 2D engine, so for the minimal amount of effort
it will probably end up being the
[Light Weight Java Game Library](http://www.lwjgl.org/), which Slick
uses underneath. The unfortunate part of this is that LWJGL requires
the use of native libraries. An alternative option would be to also
include Swing support, thus making the engine support cross platforms easily. I will
have to research to see if the Canvas in Swing is performant enough.


This is all just thought development now, but I have the whole summer
ahead of me. Maybe this will make a good project :)
