---
title: Contains_Duplicate
date: 2016-04-11 14:03:33
categories: [code]
tags: [leetcode,Array,Hash Table]
comments: yes
layout: post
---

## 题目

Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

## 解题思路

|方式|时间|空间|
|:---:|:---:|:---:|
|哈希表|O(n)|O(n)|
|暴力|O(n^2)|O(1)|
|排序|O(nlogn)|O(1)|

## 代码

```java
public class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set array = new HashSet<Integer>();
        for(int i : nums) {
            if(!array.add(i))
                return true;
        }
        return false;
    }
}
```