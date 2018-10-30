---
title: Kth_Largest_Element_in_an_Array
date: 2016-04-01 10:44:58
categories: [code]
tags: [leetcode,Divide and Conquer,Heap]
comments: yes
layout: post
---

## 题目

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

**For example**

Given [3,2,1,5,6,4] and k = 2, return 5.

**Note: **

You may assume k is always valid, 1 ≤ k ≤ array's length.

## 代码

```java
public class Solution {
    public int findKthLargest(int[] nums, int k) {
        int n = nums.length;
        Arrays.sort(nums);
        return nums[n-k];
    }
}
```
