---
layout: post
title: "Algorithms: Day 7"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi!

here is solution for [167. Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/):
```
function twoSum(numbers, target) {
  for( let i = 0; i < numbers.length - 1; i++ ){
    for( let j = i + 1; j < numbers.length; j++ ) {
      if( numbers[i] + numbers[j] == target ) {
        return [i + 1, j + 1]
      }
    }
  }
};
```