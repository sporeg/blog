---
title: Product_of_Array_Except_Self
date: 2016-07-12 10:29:02
categories: [code]
tags: [leetcode,Array]
comments: yes
layout: post
---

## 题目

Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

Solve it without division and in O(n).

For example, given [1,2,3,4], return [24,12,8,6].

**Follow up:**

Could you solve it with constant space complexity? (Note: The output array does not count as extra space for the purpose of space complexity analysis.)

## 解题思路

从左往右乘一遍，从右往左乘一遍

## 代码

```java
public class Solution {
    public int[] productExceptSelf(int[] nums) {
        int length = nums.length;
        int[] output = new int[length];
        output[0] = 1;
        //left to right
        for(int i=1;i<length;i++) {
            output[i] = output[i-1] * nums[i-1];
        }
        //right to left
        for(int i = length-1, right = 1;i>=0;right = right*nums[i--]) {
            output[i] = output[i] * right;
        }
        return output;
    }
}
```