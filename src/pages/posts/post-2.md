---
layout: ../../layouts/MainLayout.astro
title: Debouncing
description: Hello and welcome to my blog. Today, we are going to write a debounce function from scratch and I will explain the code line by line.
---

#### Date: May 14, 2023

Hello and welcome to my blog. Today, we are going to write a debounce function from scratch and I will explain the code line by line.

## Definition

Debouncing is a technique used to optimize asynchronous operations, such as fetch calls to APIs and scroll events. In simple terms, debouncing delays the processing of an event.

## Input Element without Debouncing

The following code demonstrates an input element without debouncing:

![Simple Input](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2z8h7qf8qhh92h3j14vc.gif)

For every user input (keyup/keydown) event, the event listener ("onClick") calls the event handler function (in our case, the handleChange function). For a small application, this won't cause any performance delays, but for large data websites like Flipkart and Meesho, the repeated function call can cause performance delays.

## Optimization

To optimize the input element, we can implement the following changes:

1. Instead of setting the event value on every change, we can delay the process of setting the event value by a certain waiting time (in milliseconds).
2. Inside the handleChange function, we are setting the input value on every user input. However, we just need to delay the process of setting that event value to the query (setQuery(e.target.value)).

### Debounce Implementation

We are going to build the debounce function step by step. The first step is to delay the function call. To do this, we can use the timer function. However, we need to make a function call after some delay, which is where the setTimeout function comes in.

Here is the code implementation following the above steps:

```
 const debounce = (cb, wait) => {
    let timer;
    return function (...args) {
        clearTimeout(timer);
        timer = setTimeout(() => {
            cb(...args);
        }, wait);
    };
  };
```

Here is a breakdown of what each line does:

1. The debounce function returns a function, as it will be called multiple times.
2. The debounce function accepts a callback function and a wait time for delay.
3. As discussed, we are delaying the callback function execution call by the wait time .
4. The callback can be a fetch request or a setter function.
5. To execute the callback, we need to make sure previous setTimeouts are cleared .
6. The user can pass another event before the previous timer gets completed, so we need to clear the timer to handle that case.

### Input Element with Debouncing

Here is an example of what the input element looks like with debouncing:

![With debouncing](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mz7xxb6bgiqd64ycfwdm.gif)

We can see that there is a slight delay.
we achieved the goal

That brings an end to this blog. Thanks for reading and happy coding!
