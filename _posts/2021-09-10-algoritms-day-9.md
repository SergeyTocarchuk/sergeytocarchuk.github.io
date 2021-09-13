---
layout: post
title: "Algorithms: Day 9"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Will try to solve problem [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) with Multiple Pointers Pattern:
```
var containsDuplicate = function(nums) {
  nums.sort((a,b)=> a - b)

  if (nums.length === 0)
  return false

  var i = 0;
  for( let j = 1; j < nums.length; j++ ) {
    if( nums[i] !== nums[j] ) {
      i++;
      nums[i] === nums[j];
      return false;
    }
  }
  return true;
};
```