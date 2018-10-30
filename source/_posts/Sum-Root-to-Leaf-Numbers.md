---
title: Sum_Root_to_Leaf_Numbers
date: 2016-04-29 09:53:38
categories: [code]
tags: [leetcode,Tree,Depth-first Search]
comments: yes
layout: post
---

## 题目

Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers.

For example,

```
    1
   / \
  2   3
```

The root-to-leaf path 1->2 represents the number 12.

The root-to-leaf path 1->3 represents the number 13.

Return the sum = 12 + 13 = 25.

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
    public int sumNumbers(TreeNode root) {
        return sumNumber(root,0);
    }
    public int sumNumber(TreeNode root, int preSum) {
        if(null == root)
            return 0;
        if(null == root.left && null == root.right)
            return preSum*10 + root.val;
        return sumNumber(root.left, preSum*10 + root.val) + sumNumber(root.right, preSum*10 + root.val);
    }
}
```