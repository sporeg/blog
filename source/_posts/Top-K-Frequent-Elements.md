---
title: Top_K_Frequent_Elements
date: 2016-05-04 09:28:31
categories: [code]
tags: [leetcode,Hash Table,Heap]
comments: yes
layout: post
---

## 题目

Given a non-empty array of integers, return the k most frequent elements.

For example,

Given [1,1,1,2,2,3] and k = 2, return [1,2].

Note: 

*	You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
*	Your algorithm's time complexity must be better than O(n log n), where n is the array's size.

## 代码

```java
public class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        List<Integer>[] bucket = new List[nums.length + 1];
        Map<Integer, Integer> counterMap = new HashMap<>();
        for(int num : nums) {
            counterMap.put(num,counterMap.getOrDefault(num,0)+1);
        }
        for(int key : counterMap.keySet()) {
            int counter = counterMap.get(key);
            if (bucket[counter] == null) {
                bucket[counter] = new ArrayList<>();
            }
            bucket[counter].add(key);
        }
        List<Integer> res = new LinkedList<>();
        for (int pos = bucket.length - 1; pos >= 0 && res.size() < k; pos--) {
            if (bucket[pos] != null) {
                res.addAll(bucket[pos]);
            }
        }
        return res;
    }
}
```