---
title: "Picking up Angular 1.5.x"
description: "I guess the first question I usually get is why Angular 1? Isn’t that so 2015? What about Angular 2 and React? They’re super cool, right…"
date: "2016-11-02T03:35:29.122Z"
categories: []
published: true
canonical_link: https://medium.com/@benschac/picking-up-angular-1-5-x-d6808db89c49
redirect_from:
  - /picking-up-angular-1-5-x-d6808db89c49
---

![Rudy enthusiastically expressing his views on IoC & DI at the RNC](./asset-1.gif)

---

I guess the first question I usually get is why Angular 1? Isn’t that so 2015? What about Angular 2 and React? They’re super cool, right? Yes, they are! No doubts about it.

The reason I’m learning Angular 1 is simply for two reasons. 1. that’s where all of the jobs are, and will most likely remain for a while. 2. It’s a proven framework. When your online bank is using angular 1 you know that you can trust it’s at a pretty mature place. A nice thing is that it has a component system like Angular 2 in Angular 1.5.x. So, yeah. For the foreseeable future that’s where I’m going to stay.

What I’m doing to actually learn?

This [course](https://www.coursera.org/learn/single-page-web-apps-with-angularjs/) and building this [website](https://github.com/benschac/benjaminschachter-wpapi-personalsite).

---

Now, why do I like angular? That’s where the meat and potatoes are of this post. I’m going to guess the reasons I like angular are also the reasons why it’s so gosh darn popular. The biggie for me is the loose coupling through out the application that lets you reuse so much of what you’ve built as well as the modularity that gives way to organizing a project so it can really last for the long haul. When functionality is loosely coupled and organized well, unit testing becomes even easier.

Oh, built in and custom directives (and components) are pretty sweet too. Let’s not forget about that, folks.

### Loose coupling, Isolate scope, data binding, IoC (inversion of control)

I really really like inversion of control. Not only because it makes me sound smart, but because it’s super loose coupling making things really, really reusable. I’m going to show some examples in another post. But, you should give it a google or two. It’s really worth it. Promise.

### Context, Context, Context

This really applies to everything. When I say everything I’m referring to the application framework your learning to build and the process of learning itself. If you don’t understand the context and patterns in which the application works your going to waste a whole boat load of time spinning your wheels. I’m a huge fan of sticking with something until you understand what’s going on. Nothing is magic. Nothing. If you’re memorizing something you’re doing it wrong.

A good example of this is me in week three. I kinda just went through it willy-nilly. Because I really understood weeks one and two I thought I’d just get it. I didn’t. I got through homework 3 but week fours content I understood even less. The homework assignment was supposed to take 1.5 hours. I probably spent 8 hours on it and I’m still struggling.

So, I went back and watched videos I felt fuzzy on from week 3, which turned out to be around half of the content. Not only did I watch it, but I made a point to really understand it. Get the context of what the framework was doing and why it was doing it that way. Though it took me some more time it really didn’t. If I would’ve understood the context the first time around I would’ve saved myself this pain.

So, now ask me. What the hell is the transclude property and when/why/how would I want to use it? I’ll give you a hint. It has to do with passing/wrapping content from a directives parent controller and displaying it? Why, well angular directives should know nothing about other than the data interface for the controller that’s passing it data. Transclude-ing passes data from the parent controller and sticks it into your directive.

Okay, I told you what it is, whoopsy-doodle.

But for serious. Controllers, Directives, Components, Services, Providers and Factories are the bee’s knees.

### Testing

IoC makes testing your application’s code much, much easier. Controllers are responsible for one thing, services another, templates another and so on. Everyone does their specific job. Everyone gets their own unit test.

### Conclusion

While I’m only scratching the surface here these are some of the most valuable features that I’ve found while learning more about angular 1.5.x. I’m looking forward to gaining angular enlightenment. I hope you’ll join me on my journey.
