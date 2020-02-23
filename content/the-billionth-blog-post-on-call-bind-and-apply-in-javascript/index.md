---
title: "The billionth blog post on call, bind and apply in javascript"
description: "Yeah, this shit again. Javascript, you weirdo. What’s going on here?"
date: "2016-12-12T16:04:07.290Z"
categories: []
published: true
canonical_link: https://medium.com/@benschac/the-billionth-blog-post-on-call-bind-and-apply-in-javascript-d0599b65917e
redirect_from:
  - /the-billionth-blog-post-on-call-bind-and-apply-in-javascript-d0599b65917e
---

Yeah, this shit again. Javascript, you weirdo. What’s going on here?

It’s taken me quite a bit of time to really understand the topic. [This](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals) and [this](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/) are both great blog posts relating to the subject. [You Don’t Know JS](https://github.com/getify/You-Dont-Know-JS/tree/master/this%20%26%20object%20prototypes) by [Kyle](https://medium.com/u/5dccb9bb4625) has really beaten the concept into my thick skull. If you have time it’s worth reading the series. You won’t regret it. Also, you can buy the book on this and prototypes [here](https://ssearch.oreilly.com/?q=you+don%27t+know+js%3A+this+%26+object+prototypes). I don’t have enough nice thing’s to say about the series so far.

**One last thing:** I strongly recommend playing with this code in your console while and after reading this post. Implementation is a great way to understanding what you’re learning. Try something new. Break something. Get a funky error and figure out why you got it.

So, now I’m going to try and explain it to some other folks. I can solidify my knowledge a bit more and hopefully you’ll start to pick it up too!

First, we need to talk about `this`_._ I thought we are talking about call, bind and apply?! Yeah, we’ll get to that. But, `this` is what is changed when calling any of those functions. So, you gotta know a little bit about `this` first.

`This`  is also a weird, well misunderstood concept which in turn causes `.call()`, `.bind()` and `.apply()` to be pretty hard to wrap your head around.

### What’s this (From You Don’t Know JS):

> It is contextual based on the conditions of the function’s invocation. `this` binding has nothing to do with where a function is declared, but has instead everything to do with the manner in which the function is called.

> When a function is invoked, an activation record, otherwise known as an execution context, is created. This record contains information about where the function was called from (the call-stack), _how_ the function was invoked, what parameters were passed, etc. One of the properties of this record is the `this` reference which will be used for the duration of that function's execution.

Just for the record, it kills me summing up what this is by taking a quote from You Don’t Know JS. It’s really worth reading through the book and getting a better understanding of how the mechanism works. But, for now this will do.

Please give [this chapter](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md) a read if you have time. Like it’s titled. this All Makes sense now!

**Bonus:** Play around in your console a little bit. hit `command + alt + i` if you’re on a mac and type in `this`. You’ll get the global window object returned to you which you can play with. The DOM, localStorage and a whole bunch of really interesting stuff live there.

Call, bind and apply _explicitly_ set context to `this`. Let’s see how that works. We should probably cover _implicit_ context first so we can get an idea of what _explicit_ binding does (i.e `.call()`, `.bind()`, `.apply()`)

### Implicit context

Example #1

```
function hey() {
  console.log(this.a);
}

var obj = {
  a: 'yooooo',
  hey: hey
};

obj.hey();
// yooooo
```

So, obj is getting a reference to the function `hey()`. `hey`'s this is _implicitly_ set to the `obj`'s `this` . Bing, bam, boom. You done.

**Bonus:** Try chaining another object on with a value for `a` and see what happens. Something like `obj.obj2.hey()` interesting?!

Example #2 (When things don’t go as expected).

```
function hey() {
  console.log(this.a);
}

var obj = {
  a: 'yooooo',
  hey: hey
};

var heya = obj.hey;
var a = 'howdy';

heya();
// howdy
```

Can you guess what just happened here? `this` changed, that’s what happened. The function was invoked on a global variable `heya` . `this.a` globally was set to howdy. Yeah, we’ve been in another container called the global scope this whole time! Yeah, it can totally make your head spin too.

**_Note:_** If you want to avoid accidentally setting variables to the global scope, there’s something called strict mode. Just add a `"use strict";` to the top of your file and you get an error thrown your way! :D.

### Call

Alright, we’re ready (I think) to have the talk… Let’s start off with `.call()` (aka: `Function.prototype.call`).

_Call is explicit! It’ll force a function call on a particular object (and you won’t have to use a property reference like we did with_ `_obj.hey()_`_)._

`.call()` ‘s first argument takes an object and sets the function call to it’s `this` (EXPLICITLY). You’re telling that function’s this, HEY! YOU! We’ll be using the first object in your arguments on for your `this` .

```
function hey() {
  console.log(this.a);
}

var obj = {
  a: 'yooooo',
  hey: hey
};

hey.call(obj);
 // yooooo
```

`.call()` also has another parameter which accepts function arguments.

```
function hey(b) {
  console.log(this.a, "and b: " + b);
}

var obj = {
  a: 'yooooo',
  hey: hey
};

hey.call(obj, "ekkkkk");
//yooooo and b: ekkkkk
```

That’s it! You know `.call()`! Woooooo! One down, actually two down!

### Apply

It’s the same thing as `.call()` , yay! The only difference is that `.apply()` takes an array a second value.

```
function hey(b) {
  console.log(this.a, "and b: " + b);
}

var obj = {
  a: 'yooooo',
  hey: hey
};

hey.apply(obj, ["ekkkkk"]);
 // yooooo and b: ekkkkk
```

### Bind

`.bind()` basically does the same exact thing as `.call()` and `.apply()`. Shocking, I know. No, it’s different. C’mon, let’s talk about it. It’ll explicitly set `this` and return a new function using the this context given in the first parameter of `.bind()`.

Definition from [mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind):

> The `**bind()**` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

How it’s used from [mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)

> The simplest use of `bind()` is to make a function that, no matter how it is called, is called with a particular `this` value.

I had to read that over like 5 times to make any sense out of it. If you’re still not getting after reading this post that’s okay. Take a walk about the block. Read over the docs some more and come back. These things take sometime.

Example:

```
function hey(b) {
  console.log(this.a, "and b: " + b);
}

var obj = {
  a: 'yooooo',
  hey: hey
};

// returns a new function.
 var hi = hey.bind(obj, 'ekkkkk');
 
// envokes new function that .bind() returns.
 hi();
 // yooooo and b: ekkkkk
```

That’s it! You did it!

Look, there’s a whole bunch more to read on this subject. I barley scratched the surface here. The goal was to make these concepts a little more friendly which I hope I did.

I highly recommend [You Don’t Know JS](https://github.com/getify/You-Dont-Know-JS), specifically if you check out [chapter 2](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md) in this & Object Prototypes.

Interested in more short javascript stories?! Follow me!
