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
function search(arr, num) {
  let min = 0;
  let max = arr.length - 1;

  while (min <= max) {
    let middle = Math.floor((min + max) / 2);
    let currentEl = arr[middle];

    if (arr[middle] < num) {
      min = middle + 1;
    } else if (arr[middle] > num) {
      max = middle - 1;
    } else {
      return middle;
    }
  }
  return -1;
};
```