---
title: Largest_Rectangle_in_Histogram
date: 2016-05-03 09:50:43
categories: [code]
tags: [leetcode,Array,Stack]
comments: yes
layout: post
---

## 题目

Given n non-negative integers representing the histogram's bar height where the width of each bar is 1, find the area of largest rectangle in the histogram.

![histogram](/images/histogram1.png)

Above is a histogram where width of each bar is 1, given height = [2,1,5,6,2,3].

![histogram area](/images/histogram2.png)

The largest rectangle is shown in the shaded area, which has area = 10 unit.

For example,

Given heights = [2,1,5,6,2,3],

return 10.

## 代码

```java
public class Solution {
    public int largestRectangleArea(int[] heights) {
        int length  = heights.length;
        int maxArea = 0;
        Stack<Integer> s = new Stack<Integer>();
        for(int i=0;i<=length;i++) {
            int curHeight = (i == length ? 0 : heights[i]);
            if(s.isEmpty() || curHeight >= heights[s.peek()]) {
                s.push(i);
            } else {
                int pre = s.pop();
                maxArea = Math.max(maxArea, heights[pre] * (s.isEmpty() ? i : i-1 - s.peek()));
                i--;
            }
        }
        return maxArea;
    }
}
```