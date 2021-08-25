---
layout: post
title: "Algorithms: Day 3"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi!

Rewrite algorithm of reversed array: itterate with _for loop_ and concatenate each element to empty array.
```
var reversed = function(nums) {
  let revNums = [];
  for (let i = nums.length - 1; i >= 0; i--) {
    revNums += nums[i];
  }
  return revNums;
};
```

