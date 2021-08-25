---
layout: post
title: "Algorithms: Day "
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi!

Rewrite algorithm of revising array:
```
var reversed = function(nums) {
  let revNums = [];
  for (let i = nums.length - 1; i >= 0; i--) {
    revNums += nums[i];
  }
  return revNums;
};
```

