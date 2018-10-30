---
title: Jump_Game
date: 2016-05-24 17:07:34
categories: [code]
tags: [leetcode,Array,Greedy]
comments: yes
layout: post
---

## 题目

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:

A = [2,3,1,1,4], return true.

A = [3,2,1,0,4], return false.

## 代码

```java
public class Solution {
    public boolean canJump(int[] nums) {
        int length = nums.length;
        int max = 0;
        for(int i=0;i<length;i++) {
            if(i > max) {
                return false;
            }
            max = Math.max(max,nums[i] + i);
        }
        return true;
    }
}
```