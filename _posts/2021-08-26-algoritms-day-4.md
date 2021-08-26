---
layout: post
title: "Algorithms: Day 4"
author: "Serhii T."
categories: journal
tags: [algorithms,js,multiple pointers]
image: 
---

Hi there!

Start my day with Multiple Pointers Pattern on Udemy course and practice on Count Unique Values algorithm:
```
var countUniqueValues = function(arr) {
  if(arr.length === 0) return 0;
  var i = 0;
  for (let j = 1; j < arr.length; j++) {
    if(arr[i] !== arr[j]) {
      i++;
      arr[i] = arr[j]
    }
  }
  return i + 1;
}
```

Have to dive into Time and Space Complexity. 

_Multiple pointers_ pattern helps me to solve the following problem: [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/).
```
var maxProfit = function(prices) {
  let minValue = prices[0];
  let maxProfit = 0;
  for (let i = 1; i < prices.length; i++) {
    if(minValue > prices[i]) {
      minValue = prices[i];
    } else {
      if (prices[i] - minValue > maxProfit) {
        maxProfit = prices[i] - minValue;    
      }
    }
  }
  return maxProfit;
};
```