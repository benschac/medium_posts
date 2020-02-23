---
title: "D3 React Components"
description: "There’s a whole gambit of different ways to integrate third-party libraries with React. D3 is one of those popular libraries. D3 handles…"
date: "2020-02-23T14:34:29.093Z"
categories: []
published: false
---

There’s a whole gambit of different ways to integrate third-party libraries with React. [D3](https://d3js.org/) is one of those popular libraries. D3 handles data visualizations which I wanted to work on for a [side-project](https://github.com/benschac/goal_buddy) I’ve been building. There are many really wonderful React data visualization components out there. I wanted to build my own to learn more about D3 and understand how some of these other folks are building their data-visualization components.

The D3 component here is used to give a visual reference to the timer functionality in my application. It’s an Arc (circle) that fills in as time passes. You’ll see a bunch of references to timing functions though out my code.

I found a nice example of an Arc here to base the component off of [http://bl.ocks.org/mbostock/5100636](http://bl.ocks.org/mbostock/5100636) 

Here’s a link to the final Component: [https://codesandbox.io/s/j2ymm9o9rw](https://codesandbox.io/s/j2ymm9o9rw)

  

One thing that’s interesting about both React and D3 is that they both render elements to the DOM. I did a bit of googling and ultimately decided to have D3 render the SVG’s to the DOM and React take care of the data flow.

 This choice was made for a couple of reasons:

-   React and Redux are already managing the data of the entire application already. We have some nice lifecycle hooks that we can utilize from React’s class component that’ll give us the ability to update our SVG that’s being rendered with D3.
-   D3’s job is to abstract the lower level details of the data-visualizations SVG. If we know where and how the data is coming in from React, we can create a hook into our D3 script to handle different actions that our React component will pass.

### The Base Class

When thinking about the D3 script, there were 3 different things it did. Created the SVG and rendered it to the DOM, updated that SVG when it got new data, and removed old elements from the DOM that were not longer being used and out of date.

With that in mind, three methods came to mind.

-   Create
-   Update
-   Destroy

A Javascript class is the underlying data structure to organize this functionality.

Using the instance variable `this.arc` made getting access to the d3 object way easier and method chain possible in different methods. Now, when we need to pass data to our SVG to render we have some nice base functionality organized.

### The React Component

When the component mounts, the SVG is created using the `.create` method. When the component gets new props, it’ll use the `.update` method on the base class. When there’s a reset or the component is removed from the DOM, the SVG is removed.

Additionally, we use a [ref](https://reactjs.org/docs/refs-and-the-dom.html) to grab the element off the DOM. We use a ref because we want to make sure we have a DOM element to grab and pass to D3.

Specifically the ref docs tell us:

```
There are a few good use cases for refs:

Managing focus, text selection, or media playback.

Triggering imperative animations.

Integrating with third-party DOM libraries.

Avoid using refs for anything that can be done declaratively.
```

Our React component is instantiating the base D3 class, and creating the arch on mount. 

  

Each one of our hooks are used in React’s lifecycle components. When our component gets data, it’ll pass it to D3 to render.

I hope this was helpful, I chose to go the route of creating my own component because I wanted to improve my knowledge of D3 and figure out ways to integrate it with React.

Till next time,

Benjamin
