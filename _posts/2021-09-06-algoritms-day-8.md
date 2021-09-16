---
layout: post
title: "Algorithms: Day 8"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi!

I covered "Divide and Conquer Pattern". It's something like a binary search tree system. First will be shown naive solution:
```
function search(arr, num) {
  for( let i = 0; i < arr.length; i++ ) {
    if( arr[i] === num ) {
      return i;
    }
  }
  return -1;
}
```

And here is solution with Divide and Conquer Pattern:
```
function binarySearch(arr, num) {
  var left = 0;
  var right = arr.length - 1;
  var middle = Math.floor((left + right) / 2);

  if(arr[left] == num) {
    return left;
  }

  while(arr[middle] !== num && left <= right) {
    if(num < arr[middle]) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
    middle = Math.floor((left + right) / 2);
  }
  if(arr[middle] === num) {
    return middle;
  }
  return -1; 
};
```

Shorter version of the code provided above:
```
function binarySearch(arr, num) {
  var left = 0;
  var right = arr.length - 1;
  var middle = Math.floor((left + right) / 2);

  if(arr[left] == num) {
    return left;
  }

  while(arr[middle] !== num && left <= right) {
    if(num < arr[middle]) right = middle - 1; 
    else left = middle + 1;
    middle = Math.floor((left + right) / 2);
  }

  return arr[middle] === num ? middle : -1; 
};
```