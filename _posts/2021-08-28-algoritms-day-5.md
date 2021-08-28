---
layout: post
title: "Algorithms: Day 5"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi!

Here is [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) solution:
```
var maxProfit = function(prices) {
  let Profit = 0;

  for (let i = 1; i < prices.length; i++) {
    if (prices[i] > prices[i - 1]) {
      Profit += prices[i] - prices[i - 1];
    }
  }
  return Profit;
};
```