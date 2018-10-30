---
title: Find_the_Duplicate_Number
date: 2016-04-28 15:00:05
categories: [code]
tags: [leetcode,Binary Search,Array,Two Pointers]
comments: yes
layout: post
---

## 题目

Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

**Note:**
*	You must not modify the array (assume the array is read only).
*	You must use only constant, O(1) extra space.
*	Your runtime complexity should be less than O(n2).
*	There is only one duplicate number in the array, but it could be repeated more than once.

## 代码

```java
public class Solution {
    public int findDuplicate(int[] nums) {
        if(nums.length < 2)
            return -1;
        int slow = nums[0];
        int fast = nums[slow];
        while(slow != fast) {
            slow = nums[slow];
            fast = nums[nums[fast]];
        }
        fast = 0;
        while(slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
}
```