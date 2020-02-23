---
title: "Here’s What I learned Re-Factoring a 950 line React Component"
description: "There’s a good joke about an engineer going to a factory to fix a complex industrial engine. No one has the slightest idea about what to…"
date: "2020-02-23T14:37:18.719Z"
categories: []
published: false
---

There’s a good joke about an engineer going to a factory to fix a complex industrial engine. No one has the slightest idea about what to do, how it works or what steps they cold take to fix it. It needs to get fixed.

They call in an expert. She takes a look, around the system for about 10 minutes. Doesn’t touch a thing. Ever so slightly she turns a screw, moves a lever and pow! The engine roaring back to life. Just like that, 10 minutes!

She hands the owner a bill for $20,000. He’s Flabbergasted and then asks, How does 10 minutes of your time amount to this price?

It’s 20 years of experience + 10 minutes. That 20 years of context made it possible for her to fix the problem in 10 minutes. Something that no one there could do for weeks.

#### Writing two lines of code is easy, understanding how complex systems and data flow works is hard.

  

### Finding The Root Cause Of The Problem 

How can we figure out what’s wrong if we don’t understand what’s going on in the first place? If our base understanding of the problem is fuzzy, we’re going to be doing a whole bunch of wheel spinning.
