---
title: Missing_Number
date: 2016-05-31 09:20:57
categories: [code]
tags: [leetcode,Array,Math,Bit Manipulation]
comments: yes
layout: post
---

## 题目

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

For example,

Given nums = [0, 1, 3] return 2.

**Note:**

Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?

## 代码

```java
public class Solution {
    public int missingNumber(int[] nums) {
        int length = nums.length;
        int res = length;
        for(int i=0;i<length;i++) {
            res += i - nums[i];
        }
        return res;
    }
}
```

```java
public class Solution {
    public int missingNumber(int[] nums) {
        int length = nums.length;
        int res = length;
        for(int i=0;i<length;i++) {
            res = res ^ i ^ nums[i];
        }
        return res;
    }
}
```