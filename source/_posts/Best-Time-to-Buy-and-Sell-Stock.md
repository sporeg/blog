---
title: Best_Time_to_Buy_and_Sell_Stock
date: 2016-04-14 11:12:20
categories: [code]
tags: [leetcode,Array,Dynamic Programming]
comments: yes
layout: post
---

## 题目

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

## 解题思路

记录最低价和最大收益

## 代码

```java
public class Solution {
    public int maxProfit(int[] prices) {
        int min = Integer.MAX_VALUE;
        int max = 0;
        int length = prices.length;
        for(int i = 0 ; i < length ; i++) {
            min = Math.min(min,prices[i]);
            max = Math.max(max,prices[i]-min);
        }
        return max;
    }
}
```