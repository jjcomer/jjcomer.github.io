---
layout: post
title: "Entity Oriented Programming"
date: 2011-11-06 12:02
comments: true
categories:
- Java
- Game Design 
---
A few friends and I have undertaken a game project, and I get to be in charge of the technical side of things. I immediately thought of using Clojure (since it is only the best language ever), but changed my mind as my main criteria was a easy to use game engine (I'm lazy). I ended up choosing to use the [Slick](http://slick.cokeandcode.com/) engine which is java-based. To supplement this Slick engine I have decided to use an entity based approach to programming the game. [Artemis](http://gamadu.com/artemis/) is an entity framework which was originally designed for use with Slick, but since it has no dependencies, could be used with anything.

The Artemis framework is based on a series of blog posts from [T=Machine](http://t-machine.org/index.php/2007/09/03/entity-systems-are-the-future-of-mmog-development-part-1/). The **TL;DR** of these blog posts is that an entity system in a gaming environment is very extensible and can be parallelised (the articles revolve around PS3 development, which needs done concurrently to take advantage of the hardware). Whilst I don't have any immediate needs to delve into concurrent game development, this approach has a real functional smell to it (reminiscent to that of fresh baked bread),  so it must be a good thing.

<!--more-->

All right lets look at what this really means:
### What is an entity?
At the heart of things an entity is just a GUID (or UUID) which is stored in a *world* object. The world is a global, unique (there can be multiple worlds, but they probably shouldn't talk to each other (queue some sort of parallel universe analogy)), repository of entities. Each entity is composed of components.
### What is a component?
A component represents a set of data which relates to a part of an entity. Components are not to have any logic inside of them, except for getters and setters for their fields. Components would represents the state of the entity, things like:

* Transform (this is the x and y co-ordinates of the entity)
* Spacial (this would be the image that represents the entity)
* Inventory

Components do not communicate directly with each other, communication/interaction is done using system.
###What is a system?
The world is composed of entities (which are composed of components) and systems. Systems are responsible for processing entities. An example would be a Collision System, which would process each entity which has a Transform component to see if it collides with another entity in the universe. When processing the entities are treated in a very abstract manner. The System specifies a filter (of components) for the entities it will handle, and then generically processes the result. Logic for how these interactions take place is implemented in the system (for example if a player collides with an enemy then damage should be applied), but if possible this should be implemented in the most generic way possible.

###What happens in the game loop?
The heartbeat of a game is the game loop. Now using the entity model, during the update and render phases, one only needs to trigger the processing of the appropriate systems and the entities of the world will be updated and drawn.

Now all I have to do is write the game ;)