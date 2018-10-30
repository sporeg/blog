---
title: Combinations
date: 2016-06-03 15:33:15
categories: [code]
tags: [leetcode,Backtracking]
comments: yes
layout: post
---

## 题目

Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

For example,

If n = 4 and k = 2, a solution is:

```
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

## 解题思路

combine(n,k)可以分解为

*	combine(n-1,k-1) 选择n，还需要选k-1个数
*	combine(n-1,k) 不选择n，还需要选k个数

注意combine(n-1,k-1)计算后把n加入结果

## 代码

```java
public class Solution {
    public List<List<Integer>> combine(int n, int k) {
        if(k == 0 || k == n) {
            List<Integer> row = new LinkedList<>();
            for(int i=1;i<=k;i++) {
                row.add(i);
            }
            return new LinkedList<>(Arrays.asList(row));
        }
        List<List<Integer>> result = this.combine(n - 1, k - 1);
        result.forEach(e -> e.add(n));
        result.addAll(this.combine(n - 1 , k));
        return result;
    }
}
```