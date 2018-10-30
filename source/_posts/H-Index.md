---
title: H-Index
date: 2016-05-18 10:43:32
categories: [code]
tags: [leetcode,Hash Table,Sort]
comments: yes
layout: post
---

## 题目

Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.

According to the [definition of h-index on Wikipedia](https://en.wikipedia.org/wiki/H-index): "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."

For example, given citations = [3, 0, 6, 1, 5], which means the researcher has 5 papers in total and each of them had received 3, 0, 6, 1, 5 citations respectively. Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, his h-index is 3.

**Note**: If there are several possible values for h, the maximum one is taken as the h-index.

**Hint**:

*	An easy approach is to sort the array first.
*	What are the possible values of h-index?
*	A faster approach is to use extra space.

## 解题思路

*	1 排序后遍历 2ms
	*	O(nlogn)时间
*	2 数组记录 1ms
	*	O(n)时间
	*	O(n)空间

## 代码

```java
public class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);
        int length = citations.length;
        for(int i=0;i<length;i++) {
            if(citations[i] >= length-i)
                return length-i;
        }
        return 0;
    }
}
```

```java
public class Solution {
    public int hIndex(int[] citations) {
        int length = citations.length;
        int[] counter = new int[length+1];
        int count = 0;
        for(int i=0;i<length;i++) {
            if(citations[i] >= length) {
                counter[length]++;
            } else {
                counter[citations[i]]++;
            }
        }
        for(int i=length;i>=0;i--) {
            count += counter[i];
            if(count >= i) {
                return i;
            }
        }
        return 0;
    }
}
```
