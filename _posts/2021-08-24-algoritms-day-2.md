---
layout: post
title: "Algorithms: Day 2"
author: "Serhii T."
categories: journal
tags: [algorithms,js]
image: 
---

Hi there!

Keep working on algorithms on [LeetCode](https://leetcode.com/problemset/algorithms/?page=1&topicSlugs=array&difficulty=EASY).

I began from revising problems I covered yesterday for better understanding JS.

Additionally I solved the following algorithms:
- 66. Plus One
- 88. Merge Sorted Array

And get familier with the following methods: sort, splice, unshift/shift.

Here is example of algorithms for merge and sort an array:
```
var merge = function(nums1, m, nums2, n) {
  while (n) {
    if (nums1[m - 1] > nums2[n - 1]) {
      nums1[m + n - 1] = nums1[m - 1];
      m--;
    } else {
      nums1[m + n - 1] = nums2[n - 1];
      n--;
    }
  }
  return nums1;
};
```

