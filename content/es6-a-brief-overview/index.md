---
title: "ES6 — A brief overview"
description: "So, I’m sure you’re hearing all about the new javascript standard and all of the fun and exciting features it’s going to bring to the…"
date: "2020-02-23T14:37:50.288Z"
categories: []
published: false
---

So, I’m sure you’re hearing all about the new javascript standard and all of the fun and exciting features it’s going to bring to the table.

  

### New ways to assign variables — Const, Let

Let’s start off with the more straight forward const. Const is a constant. Constants can’t be changed. Once you assign it, that’s it. Simple right? Also, constants are usually written in all uppercase.

```
const HELLO = 'Hey, Y'all'; 
```

Now, let is a little bit different. Let [lexically scopes](http://whatis.techtarget.com/definition/lexical-scoping-static-scoping) and gets rid of hoisting. That’s how I like to think of it anyways. But what’s a lexical scope? Great question!

ES5 — Example (feel free to play with this and run it in your browser).

```
// old school JavaScript
var variable = 5;

{
  console.log('inside', variable); // 5
  var variable = 10;
}

console.log('outside', variable); // 10

variable = variable*2;

console.log('changed', variable); // 20
```

What’s going on here? Block level var variable = 10 is able to change the global scoped var variable to 10. This kind of variable change can cause some pesky bugs and lots of hair pulling down the road.

```
// modern JavaScript
let variable = 5;

{
  console.log('inside', variable); // error
  let variable = 10;
}

console.log('outside', variable); // 5

variable = variable*2;

console.log('changed', variable); // 10
```

With let, it’s lexically bound so the code in the {} doesn’t know about the let variable = 5; which causes an error. Global let variable =5; stays five and we all move forward with our lives. :D

Lexically scoping variables with let also takes care of some other annoying issues with javascript. Like working with closures. What do you think you’d get out of the first index of this array that just pushed a function with i?

```
'use strict'
let arr = [];
for(var i = 0; i < 2; i++) {

 arr.push(function() { return i; });
}

console.log(arr[0]());
// 2;
```

Not 0! You’ll get two because this function will create a closure over i and it’ll only resolve once the for loop is complete, setting i to 2 in every function.

```
'use strict'
let arr = [];
for(let i = 0; i < 2; i++) {

arr.push(function() { return i; });
}

console.log(arr[0]());
// 0;
```

Now, we get 0 as expected, what’s going on here?! Let is giving each iteration it’s own i variable to close over. While this might hurt performance a little, it makes working with closures, much, much easier.
