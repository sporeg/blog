---
title: Intersection_of_Two_Arrays
date: 2016-05-27 15:43:19
categories: [code]
tags: [leetcode,Binary Search,Hash Table,Two Pointers,Sort]
comments: yes
layout: post
---

## 题目

Given two arrays, write a function to compute their intersection.

**Example:**

Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

**Note:**

*	Each element in the result must be unique.
*	The result can be in any order.

## 代码

```java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet();
        HashSet<Integer> set2 = new HashSet();
        for(int num:nums1) {
            set1.add(num);
        }
        for(int num:nums2) {
            if(set1.contains(num)) {
                set2.add(num);
            }
        }
        int i = 0;
        int[] res = new int[set2.size()];
        for(int num:set2){
            res[i++] = num;
        }
        return res;
    }
}
```