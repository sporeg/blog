---
title: House_Robber
date: 2016-04-15 09:32:24
categories: [code]
tags: [leetcode,Dynamic Programming]
comments: yes
layout: post
---

## 题目

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night.**

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police.**

## 代码

```java
public class Solution {
    public int rob(int[] nums) {
        if(null == nums)
            return 0;
        int no = 0;
        int yes = 0;
        int length = nums.length;
        for(int i=0;i<length;i++) {
            int tempNo = no;
            no = Math.max(no,yes);
            yes = nums[i] + tempNo;
        }
        return Math.max(no,yes);
    }
}
```
