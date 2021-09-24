---
layout: post
title: "Algorithms: removeFromArray"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi there!

While solving problems faced an very easy and interesting task: implement a function that takes an array and some other arguments then removes the other arguments from that array. It's fairly easy, but how to deal with multiple optional arguments in a javascript function?

So first function I wrote with _for_ loop and _push_ every element to new array if it's not equal to some other arguments:
```
const removeFromArray = function(arr, num) {
  let newArr = [];
  for( let i = 0; i < arr.length; i++ ){
    if( arr[i] !== num ){
      newArr.push(arr[i]);
    }
  }
  return newArr;
};
```

But what to do if we have the following condition: **removeFromArray([1, 2, 3, 4], 7, "tacos")**?
Using the [spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters) to get an array of all of the arguments that are passed to a function.

```
const removeFromArray = function (...args) {
  // the very first item in our list of arguments is the array, we pull it out with args[0]
  const array = args[0];
  // create a new empty array
  const newArray = [];
  // use forEach to go through the array
  array.forEach((item) => {
    // push every element into the new array
    // UNLESS it is included in the function arguments
    // so we create a new array with every item, except those that should be removed
    if (!args.includes(item)) {
      newArray.push(item);
    }
  });
  // and return that array
  return newArray;
};
```
That's it!
