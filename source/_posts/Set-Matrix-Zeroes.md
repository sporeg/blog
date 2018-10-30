---
title: Set_Matrix_Zeroes
date: 2016-05-06 10:19:55
categories: [code]
tags: [leetcode,Array]
comments: yes
layout: post
---

## 题目

Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in place.

## 解题思路

用第1行和第1列记录清零状态(0清1不清)

对第1行和第1列的清零用2个(matrix[0][0]有冲突)boolean记录(true清false不清)

倒着清的话可以省去一个boolean记录

## 代码

```java
public class Solution {
    public void setZeroes(int[][] matrix) {
        boolean zeroFlagCol = false;
        int rows = matrix.length;
        int cols = matrix[0].length;
        for(int i=0;i<rows;i++) {
            if(matrix[i][0]==0) 
                zeroFlagCol = true;
            for(int j=1;j<cols;j++) {
                if(matrix[i][j]==0) {
                    matrix[i][0] = matrix[0][j] = 0;
                }
            }
        }
        for(int i=rows-1;i>=0;i--) {
            for(int j=cols-1;j>=1;j--) {
                if(matrix[0][j] == 0 || matrix[i][0] == 0)
                    matrix[i][j] = 0;
            }
            if(zeroFlagCol)
                matrix[i][0] = 0;
        }
    }
}
```