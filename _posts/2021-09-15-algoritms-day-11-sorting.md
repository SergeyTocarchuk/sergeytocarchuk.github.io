---
layout: post
title: "Algorithms Day 11: Sorting"
author: "Serhii T."
categories: journal
tags: [algorithms,js,swap,bubble]
image: 
---

JavaScript has built-in method _sort()_. But if you sort an array with integers you will find that result differs from one you expected:
```
[6,4,10,15].sort();
>[10, 15, 4, 6]
```
According to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) elements are sorted by converting them to strings first and comparing strings in UTF-16 code units order. The built-in sort method accepts an optional comparators function (comparator looks at pairs of elements: **a** and **b**) and determines sort order based on the return value: if it returns a negative number, **a** should come before **b**:
```
function numberCompare(num1, num2) {
  return num1 - num2;
};

[6,4,10,15].sort;
```

### Swapping Functionality
```
//ES5
function swap(arr, idx1, idx2) {
  var temp = arr[idx1];
  arr[idx1] = arr[idx2];
  arr[idx2] = temp
}

//ES2015
const swap = (arr, idx1, idx2) => {
  [arr[idx1],arr[idx2]] = [arr[idx2],arr[idx1]];
}
```
### BUBBLE SORT

A sorting algorithm where the largest value swap (**bubble up**)to the top of the array.
```
function bubbleSort(arr) {
  for (var i = arr.length; i > 0; i--) {
    for (var j = 0; j < i - 1; j++) {
      if( arr[j] > arr[j + 1] ) {
        var temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  return arr;
};
```
The same sorting method using another Swap functionality:
```
function bubbleSort(arr) {
  const swap = (arr, idx1, idx2) => {
    [arr[idx1],arr[idx2]] = [arr[idx2],arr[idx1]];
}
  for (var i = arr.length; i > 0; i--) {
    for (var j = 0; j < i - 1; j++) {
      if( arr[j] > arr[j + 1] ) {
        swap(arr, j, j+1)
      }
    }
  }
  return arr;
};
```
Optimized with noSwaps:
```
function bubbleSort(arr) {
  var noSwaps;
  for (var i = arr.length; i > 0; i--) {
    noSwaps = true;
    for (var j = 0; j < i - 1; j++) {
      if( arr[j] > arr[j + 1] ) {
        var temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
        noSwaps = false;
      }
    }
    if(noSwaps) break;
  }
  return arr;
};
```
