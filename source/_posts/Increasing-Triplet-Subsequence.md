---
title: Increasing_Triplet_Subsequence
date: 2016-05-19 13:48:35
categories: [code]
tags: [leetcode]
comments: yes
layout: post
---

## 题目

Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.

Formally the function should:

```
Return true if there exists i, j, k 
such that arr[i] < arr[j] < arr[k] given 0 ≤ i < j < k ≤ n-1 else return false.
```

Your algorithm should run in O(n) time complexity and O(1) space complexity.

**Examples**:

Given [1, 2, 3, 4, 5],

return true.

Given [5, 4, 3, 2, 1],

return false.

## 代码

```java
public class Solution {
    public boolean increasingTriplet(int[] nums) {
        int first = second = Integer.MAX_VALUE;
        for(int num:nums) {
            if(num <= first) {
                first = num;
            } else if(num <= second) {
                second = num;
            } else {
                return true;
            }
        }
        return false;
    }
}
```