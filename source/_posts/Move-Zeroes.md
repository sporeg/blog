---
title: Move_Zeroes
date: 2016-04-08 20:13:01
categories: [code]
tags: [leetcode,Array,Two Pointers]
comments: yes
layout: post
---

## 题目

Given an array nums, write a function to move all 0's to the end of it while **maintaining the relative order of the non-zero elements**.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

**Note:**

You must do this in-place without making a copy of the array.

Minimize the total number of operations.

## 解题思路

设置记录点

刚开始没好好看题，以为非0数换顺序也可以，就前后一起搜索然后互换 结果：WA。。。 sad story

## 代码

```java
public class Solution {
    public void moveZeroes(int[] nums) {
        int pos = 0;
        int length = nums.length;
        if(length<2)
            return;
        for(int i=0;i<length;i++) {
            if(nums[i]!=0)
                nums[pos++] = nums[i];
        }
        while(pos<length) {
            nums[pos++] = 0;
        }
    }
}
```