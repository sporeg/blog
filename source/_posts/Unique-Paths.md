---
title: Unique_Paths
date: 2016-05-13 12:48:46
categories: [code]
tags: [leetcode,Array,Dynamic Programming]
comments: yes
layout: post
---

## 题目

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![unique paths](/images/uniquepaths1.png)

Above is a 3 x 7 grid. How many possible unique paths are there?

## 代码

```java
public class Solution {
    public int uniquePaths(int m, int n) {
        if (m == 0 || n == 0) {
            return 0;
        }
        if (m == 1 || n == 1) {
            return 1;
        }
        int[] res = new int[n];
        for(int j=0;j<n;j++) {
            res[j] = 1;
        }
        for(int i=1;i<m;i++) {
            for(int j=1;j<n;j++) {
                res[j] += res[j-1];
            }
        }
        return res[n-1];
    }
}
```

[公式法](https://leetcode.com/discuss/9110/my-ac-solution-using-formula)

```
First of all you should understand that we need to do n + m - 2 movements : m - 1 down, n - 1 right, because we start from cell (1, 1).

Secondly, the path it is the sequence of movements( go down / go right), therefore we can say that two paths are different when there is i-th (1 .. m + n - 2) movement in path1 differ i-th movement in path2.

So, how we can build paths. Let's choose (n - 1) movements(number of steps to the right) from (m + n - 2), and rest (m - 1) is (number of steps down).

I think now it is obvious that count of different paths are all combinations (n - 1) movements from (m + n-2).
```

一共走(n-1)+(m-1)步，其中向下走(m-1)步

(m-1)放在n的任何位置，(m-1)之间没有差异

```java
public class Solution {
    public int uniquePaths(int m, int n) {
        int N = n + m - 2;// how much steps we need to do
        int k = m - 1; // number of steps that need to go down
        double value = 1;
        // here we calculate the total possible path number 
        // Combination(N, k) = n! / (k!(n - k)!)
        // reduce the numerator and denominator and get
        // C = ( (n - k + 1) * (n - k + 2) * ... * n ) / k!
        for (int i = 1; i <= k; i++) {
            value *= ((double)(N - k + i) / (double)i);
        }
        return (int) Math.round(value);
    }
}
```