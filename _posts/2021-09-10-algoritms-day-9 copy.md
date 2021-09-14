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
function containsDuplicate(nums) {
  nums.sort((a,b) => a - b);

  if (nums.length === 0)
  return false

  let i = 0;
  for( let j = i + 1; j < nums.length; j++ ) {
    if( nums[j] === nums[i] ) {
      return true;
    }
    i++;
  }
  return false;
};
```

[268. Missing Number](https://leetcode.com/problems/missing-number/) has the following solution:

```
function missingNumber(nums) {
    let sum = nums.length;
    for(let i = 0; i < nums.length; i++) {
        sum = sum + i - nums[i];
    }
    return sum;
};
```