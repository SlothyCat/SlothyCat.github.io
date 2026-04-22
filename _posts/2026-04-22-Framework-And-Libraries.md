---
title: "Framework VS Library"
date: 2026-04-22 15:36:00 +0800
categories: [SWE]
tags: [SWE]
image:
  path: assets/images/library.jpg
  alt: Is Framework a kind of library?
---

# Introduction
I have been working on a game called 'Soulless Knight' for my CS3217 module on SWE and because of its nature of keeping things extendible and decoupled, it took a lot of work and the idea 'framework' kept appearing in my mind. Am I building a highly decoupled game thats on a framework? And also, I am still not quite clear of the difference between framework and library. Which is what made me start writing this post in the middle of the Security+ content.

[Repo](https://github.com/cs3217-2526/group-project-dungeonCrawler) <br>
[Game Manual](https://cs3217-2526.github.io/group-project-dungeonCrawler/game-manual/overview) <br>
[Developer Guide](https://cs3217-2526.github.io/group-project-dungeonCrawler/dev-guide/overview)


# What I thought the difference was...
Framework is something you can use and build upon. Like a blueprint of something generic, and then you customise it based on your needs! Library is also something that you use for your needs but its just some functions going in the background right... Wait, then aren't both of them kinda similar... HUHHHH 

![Alt text](/assets/images/cat_shocked.jpg)

# So what is the difference actually?

The ownership of control.

## Framework
The key idea here is the **Inversion of Control**. Frameworks are in control here, users fill in code that fits into their structure. 

Think about writing a React Component, we have to follow their way of implementation right? But the rendering and other logic is done by React.

## Library
**You have the control**. Import the functions as tools for your own script. These functions fit into your code. The exact opposite of framework.

## An analogy I got from Claude..
A useful analogy: building a house.
- A library is like a power drill — you pick it up, use it for a specific job, put it down.
- A framework is like a construction contract — you fill in the blueprints it expects, and it handles the build process around your inputs.

# Final Thoughts
So back to the original question that I had from the start, is my Soulless Knight a highly decoupled game on top of a nameless framework?

Kinda.

It is *not a clean framework on its own* because a framework should have its own boundary and it should not know anything about the game while the game knows everything about the framework.
- Backend Protocols and HUDSystem contain game concepts like HealthComponent
- Framework would just pass raw data primitives around
- System has game decisions like choosing to render enemy health but not player health on head
- No module boundary, right now all of them are just folders of same module

If we were to make it into a real game framework, we would have the following..

### ECSKit (the framework)
Contains: World, Entity, Component, ComponentStorage, System, SystemManager, RenderingBackend...

### dungeonCrawler (Soulless Knight, the game that imports ECSKit)
Contains: Various Components, Systems and Adapters

So cool stuffs, we are kinda close to a Framework unintentionally and I hope to maybe try building some sort of a framework one day! Fun stuff to try

![Alt text](/assets/images/cat_monk.jpg)