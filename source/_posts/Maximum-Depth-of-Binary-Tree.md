---
title: Maximum_Depth_of_Binary_Tree
date: 2016-04-07 13:42:23
categories: [code]
tags: [leetcode,Tree,Depth-first Search]
comments: yes
layout: post
---

## 题目

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## 解题思路

DFS

## 代码

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public int maxDepth(TreeNode root) {
        return root==null? 0 : Math.max(maxDepth(root.left), maxDepth(root.right))+1;
    }
}
```