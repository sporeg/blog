---
title: Majority_Element
date: 2016-04-11 14:17:45
categories: [code]
tags: [leetcode,Divide and Conquer,Array,Bit Manipulation]
comments: yes
layout: post
---

## 题目

Given an array of size n, find the majority element. The majority element is the element that appears more than | n/2 | times.

You may assume that the array is non-empty and the majority element always exist in the array.

## 解题思路

计数即可

## 代码

```java
public class Solution {
    public int majorityElement(int[] nums) {
        int length = nums.length;
        int num = nums[0];
        int count = 1;
        for(int i = 1;i<length;i++) {
            if(num==nums[i]) {
                count++;
            }else if(count==0) {
                num = nums[i];
                count++;
            }else {
                count--;
            }
        }
        return num;
    }
}
```