---
title: Search_in_Rotated_Sorted_Array
date: 2016-05-09 10:26:44
categories: [code]
tags: [leetcode,Binary Search,Array]
comments: yes
layout: post
---

## 题目

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

## 代码

```java
public class Solution {
    public int search(int[] nums, int target) {
        int length = nums.length;
        int head = 0;
        int tail = length - 1;
        while(head < tail) {
            int mid = (head + tail) / 2;
            if(nums[mid]>nums[tail]) {
                head = mid + 1;
            } else {
                tail = mid;
            }
        }
        int begin = head;
        head = 0;
        tail = length - 1;
        while(head <= tail) {
            int mid = (head + tail) / 2;
            int pos = (begin + mid) % length;
            if(nums[pos] == target)
                return pos;
            if(nums[pos] < target) {
                head = mid + 1;
            } else {
                tail = mid - 1;
            }
        }
        return -1;
    }
}
```