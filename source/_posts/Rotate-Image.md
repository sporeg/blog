---
title: Rotate_Image
date: 2016-05-17 13:37:10
categories: [code]
tags: [leetcode,Array]
comments: yes
layout: post
---

## 题目

You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Follow up:

Could you do this in-place?

## 解题思路

使1/4个矩阵旋转

```
1 2 3       1 2 3           1
4 5 6  ==>   (5)   ==>   (5)2
7 8 9                       3 
```

## 代码

```java
public class Solution {
    public void rotate(int[][] matrix) {
        if (matrix == null) {
            return;
        }

        int n = matrix.length;

        for (int i = 0; i < n / 2 ; i++) {
            for (int j = i; j < n-i-1 ; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[(n-1)-j][i];
                matrix[(n-1)-j][i] = matrix[(n-1)-i][(n-1)-j];
                matrix[(n-1)-i][(n-1)-j] = matrix[j][(n-1)-i];
                matrix[j][(n-1)-i] = temp;
            }
        }
    }
}
```
