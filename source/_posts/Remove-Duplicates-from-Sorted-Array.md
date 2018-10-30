---
title: Remove_Duplicates_from_Sorted_Array
date: 2016-04-19 17:02:16
categories: [code]
tags: [leetcode,Array,Two Pointers]
comments: yes
layout: post
---

## 题目

Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,

Given input array nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.

## 代码

```java
public class Solution {
    public int removeDuplicates(int[] nums) {
        int arrayLength = nums.length;
        if(arrayLength == 0)
            return 0;
        int length = 1;
        int pre = nums[0];
        for(int i = 1;i<arrayLength;i++) {
            if(nums[i] == pre)
                continue;
            nums[length++] = nums[i];
            pre = nums[i];
        }
        return length;
    }
}
```