---
title: "Learning Redux, what I wish I knew when I started"
description: "I’m just going to jump right into it. I should’ve started by reading the documentation first. Why didn’t I? I like videos series and…"
date: "2020-02-23T14:34:40.494Z"
categories: []
published: false
---

I’m just going to jump right into it. I should’ve started by reading the documentation first. Why didn’t I? I like videos series and reading tutorials because I was afraid of documentation. While they’re good, nothing beats referencing documentation and understanding it on your own. I did watch and build the learning redux video series. I’d caution you to stay away from it at this point in time. It uses some old class syntax and react-router 2. If I was going to watch a video I should’ve watched the egghead videos first. 

Now after watching all of the videos (twice over) I’d recommend doing the tutorial in the docs first before doing anything and getting it up and running in a create-react-app generated environment. You should know what’s going on enough where you can explain to someone else what exactly is going on. You should also be able to implement some other crud operations too. I did edit and delete on mine. But, I’m sure you can find some feature you’d like to build.

I’d watch the egghead video next. Mainly because Dan goes into detail about how everything works and will implement core features then abstract them out or use another library like connect. It’s kinda hard to see the forest from the trees going this route where you make the same application in the tutorial in the docs. But, if you understand how it works in the tutorial you’ll see why and how he refactors the code into what’s in the tutorial

 Yes, you should code along with him.

Redux is super hard to wrap your head around. Take it easy. It’ll come after a while.

Redux’s Readme file is also pretty sweet and gives a very good 10,000ft view of what exactly Redux does.

```
The whole state of your app is stored in an object tree inside a single store.
The only way to change the state tree is to emit an action, an object describing what happened.
To specify how the actions transform the state tree, you write pure reducers.
```

I think it really clicked for me when I got container components and wrote them. Passing data as props to presentation components, abstracting dispatch into callback functions, importing action creators.
