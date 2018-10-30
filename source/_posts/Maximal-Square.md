---
title: Maximal_Square
date: 2016-05-20 17:03:10
categories: [code]
tags: [leetcode,Dynamic Programming]
comments: yes
layout: post
---

## 题目

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing all 1's and return its area.

For example, given the following matrix:

```
1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0
```

Return 4.

## 代码

```java
public class Solution {
    public int maximalSquare(char[][] matrix) {
        int row = matrix.length;
        if(row == 0)
            return 0;
        int col = matrix[0].length;
        int result = 0;
        int[][] check = new int[row+1][col+1];
        for (int i = 1 ; i <= row; i++) {
            for (int j = 1; j <= col; j++) {
                if(matrix[i-1][j-1] == '1') {
                    check[i][j] = Math.min(Math.min(check[i][j-1] , check[i-1][j-1]), check[i-1][j]) + 1;
                    result = Math.max(check[i][j], result); // update result
                }
            }
        }
        return result * result;
    }
}
```