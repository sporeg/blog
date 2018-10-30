---
title: Single_Number
date: 2016-05-11 10:06:54
categories: [code]
tags: [leetcode,Hash Table,Bit Manipulation]
comments: yes
layout: post
---

## 题目

Given an array of integers, every element appears twice except for one. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

## 代码

```java
public class Solution {
    public int singleNumber(int[] nums) {
        int res = 0;
        for(int num:nums) {
            res = res ^ num;
        }
        return res;
    }
}
```