---
layout: post
title: "Algorithms Day 12: Merge, Quick, Radix Sorting"
author: "Serhii T."
categories: journal
tags: [algorithms,js,sort,merge]
image: 
---

I dive in another merge sort method (using recursion).
First of all here is a function responsible for merging two sorted array:
```
function merge(arr1, arr2) {
  let results = [];
  let i = 0;
  let j = 0;
  while( i < arr1.length && j < arr2.length ) {
    if( arr2[j] > arr1[i] ){
      results.push(arr1[i]);
      i++;
    } else {
      results.push(arr2[j]);
      j++;  
    }
  } 
  while( i < arr1.length ){
    results.push(arr1[i]);
    i++
  }
  while( j < arr2.length ){
    results.push(arr2[j]);
    j++;
  }
  return results;
}

merge([1,10,29], [2,24,101,199]);
```

And here is function of merge sorting with recursion:
```
function mergeSort(arr) {
  if( arr.length <= 1 ) return arr;
  let mid = Math.floor(arr.length / 2);
  let left = mergeSort(arr.slice(0,mid));
  let right = mergeSort(arr.slice(mid));
  return merge(left, right);
}

mergeSort([10,24,76,73,12,4387,23,34,45,1,20]);
```

Here is another method: Quick Sort. The main idea is to find a pivot element and push it on its place - other elements quick sort both on left and right side:
```
// Pivot helper
function pivot(arr, start=0, end=arr.length+1){
  function swap(array, i, j){
    var temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  }

  var pivot = arr[start];
  var swapIdx = start;

  for( var i = start + 1; i < arr.length; i++ ){
    if( pivot > arr[i] ){
      swapIdx++;
      swap(arr, swapIdx, i);
    }
  }
  swap(arr, start, swapIdx);
  return swapIdx;
}

// Quick Sort
function quickSort(arr, left = 0, right = arr.length - 1){
  if( left < right ){
    let pivotIndex = pivot(arr, left, right)
    //left
    quickSort(arr, left, pivotIndex - 1);
    //right
    quickSort(arr, pivotIndex + 1, right);
  }
  return arr;
}

quickSort([10,24,76,73,12,4387,23,34,45,1,20]);
```

Radix sort based on sorting elements into buskets according to their k-digits.
```
//find place of digit in num
function getDigit(num, i){
  return Math.floor(Math.abs(num) / Math.pow(10, i)) % 10;
}

//how many digits in num
function digitCount(num){
  if( num === 0 ) return 1;
  return Math.floor(Math.log10(Math.abs(num))) + 1;
}

//find the largest number of digits in num
function mostDigits(nums){
  let maxDigits = 0;
  for( let i = 0; i < nums.length; i++ ){
    maxDigits = Math.max(maxDigits, digitCount(nums[i]));
  }
  return maxDigits;
}

function radixSort(arr){
  let maxDigitCount = mostDigits(arr);
  for( let k = 0; k < maxDigitCount; k++ ){
    //create 10 empty arrays (buckets)
    let digitBuckets = Array.from({length: 10}, () => [] );
    for( let i =0; i < nums.length; i++ ){
      let digit = getDigit(nums[i],k);
      digitBuckets[digit].push(nums[i]);
    }
    //recollect all nums from buckets in array. Spread operator '...' allow to collect arrays as elements into our array 
    nums = [].concat(...digitBuckets);
  }

  return arr
}

radixSort([23,567,18276,2,-1,34,67,7,33,21,9,99]);
```