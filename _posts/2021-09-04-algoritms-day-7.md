---
layout: post
title: "Algorithms: Day 7"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi!

Here is solution for [167. Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/):
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

Find [169. Majority Element](https://leetcode.com/problems/majority-element/): the element that appears more than ⌊n / 2⌋ times:
```
var majorityElement = function(nums) {
  let majIndex = 0, count = 1;
  
  for(let i = 1; i < nums.length; i++){
    if(nums[majIndex] === nums[i]){
      count++;
    }else{
      count--;
      if(!count){
        majIndex = i;
        count = 1;
      }
    }
  }
  return nums[majIndex];
};
```