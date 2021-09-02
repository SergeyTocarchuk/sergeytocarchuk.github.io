---
layout: post
title: "Algorithms: Day 6"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi there!

Here is problem [136. Single Number](https://leetcode.com/problems/single-number/) solution.
The idea is to sort first given array:
```
var singleNumber = function(nums) {
    nums.sort((a,b)=> a - b)
    for (var i = 1; i < nums.length; i = i + 2){
        if (nums[i-1] != nums[i]) return nums[i-1];
    }
    return nums[i - 1];
};
```

Today I also covered the [Sliding Window Pattern](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/learn/lecture/11183952#overview). The problem is to find maximum sum of given subarray. 

Here is easy solution:
```
function maxSubArray(arr, nums) {
  if(nums > arr.length){
    return null;
  }
  var max = 0;
  for (let i = 0; i < arr.length; i++){
    temp = 0;
    for (j = 0; j < nums; j++){
      temp += arr[i + j]
    }
    if (temp > max) {
      max = temp;
    }
  }
  return max;
};
```

Using Sliding Window Pattern we will refactor our algorithm the following way:
```
function maxSubArray(arr, nums) {
  let temp = 0;
  let max = 0;
  if(nums > arr.length){
    return null;
  }

  for (let i = 0; i < nums; i++){
    max += arr[i];
  }
  temp = max;

  for (let i = nums; i < arr.length; i++){
    temp = temp - arr[i - nums] + arr[i];
    max = Math.max(max, temp);
  }
  return max;
};
```