---
title: "Coursera Angular.js Week 1"
description: "Hi There!"
date: "2016-11-02T04:00:13.867Z"
categories: []
published: true
canonical_link: https://medium.com/@benschac/coursera-angular-js-week-1-2ee0d094934d
redirect_from:
  - /coursera-angular-js-week-1-2ee0d094934d
---

Hi There!

I’m writing this partially to promote [Coursera’s](https://www.coursera.org) [Angular 1.5.X course](https://www.coursera.org/learn/single-page-web-apps-with-angularjs/) but really this more of a log to further cement what I’ve learned (and show it off a little too :D).

Before I start, I’d highly recommend [learning how to learn](https://www.coursera.org/learn/learning-how-to-learn) (which is also on Coursera). If there’s one take away I have from this course it’s all about context and listening to your body. If you’re grabbing the core context of what you’re trying to pick up you’re not going to truly grasp the skills you’re trying to learn. Memorizing is hard, figuring out how and why things work is fun.

So, why [Angular 1.5](https://angularjs.org/).x? That’s a great question. Well, [a lot of companies](https://www.eduonix.com/blog/web-programming-tutorials/top-15-websites-and-apps-built-with-angularjs/) use it and have invested in it for the last couple of years. Angular 2 is still extremely new. While there are going to be jobs for Angular 2, it’s not going to nearly be what the Angular 1 market is for quite sometime. Why not react? or Ember? Well, that’s a whole other blog post that I’ll have to write some other time.

Also, angular 1.5.x has a component feature that’s similar to the structure of components that angular 2 uses and will get you in the habit of building in a component based architecture environment. More on that in week 4.

### What’s MVVM?

Model View, ViewModel is the design pattern Angular follows. What this structure does is organizes our code into something more maintainable in the long run by modularizing functionality and separating concerns.

-   Model: Is where all of the raw data is stored.

ViewModel: Is the connective glue between the View and the Model.

> The ViewModel is the representation of the state of the view. It’s the model, that is, the data that represents the view. It’s kind of the back side of the model. It holds the data that’s displayed in the view, and in response to events, in other words, it does the presentation logic. If there’s any business logic like processing of some data, it usually calls other functionality to get that done. — [Yaakov](https://www.coursera.org/learn/single-page-web-apps-with-angularjs/lecture/zL8Sf/lecture-3-model-view-viewmodel-mvvm)

View: That’s where the data is actually shown to the user.

### Dependency Injection: Inversion of control (IoC, don’t call us, we’ll call you)

Basically, the idea is that the system can take a module as a parameter and then pass dependent methods around the application. The underlying theme here is that your passing a service (which we’ll get into in another blog post, promise (we’ll also get into those too, heh)) to a client, rather than the client constructing it.

The cool thing about this type of application is the client doesn’t need to now anything about the services it’s injecting. It just needs to know about the interface it’s using. **Loose coupling is the name of the game here. The more we can re-use the better.**

So, there’s much, much more cool stuff to come. I excluded a lot of content here. Why? Well this is really just an overview of the more important concepts that angular uses that I want to make sure I understand. While everything is super important these are also tid-bits that I need to brush-up myself too.

Thanks for reading!

Cheers!
