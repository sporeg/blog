---
title: Two_Sum
date: 2016-04-11 17:21:42
categories: [code]
tags: [leetcode,Array,Hash Table]
comments: yes
layout: post
---

## 题目

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution.

**Example:**

> Given nums = [2, 7, 11, 15], target = 9,
> 
> Because nums[0] + nums[1] = 2 + 7 = 9,
> return [0, 1].

**UPDATE (2016/2/13):**

The return format had been changed to **zero-based** indices. Please read the above updated description carefully.

## 解题思路

(i,num)->(num,i)

找到(target-num,j),两数为(i,j)

## 代码

```java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        for (int i = 0; i < nums.length; i++) {
            if(map.containsKey(target - nums[i])) {
                return new int[]{map.get(target - nums[i]), i};
            }else {
                map.put(nums[i], i);
            }
        }
        return new int[]{0, 0};
    }
}
```