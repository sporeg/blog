---
title: Symmetric_Tree
date: 2016-04-16 09:57:23
categories: [code]
tags: [leetcode,Tree,Depth-first Search,Breadth-first Search]
comments: yes
layout: post
---

## 题目

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree is symmetric:

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

But the following is not:

```
    1
   / \
  2   2
   \   \
   3    3
```

**Note:**

Bonus points if you could solve it both recursively and iteratively.

confused what "{1,#,2,3}" means? > read more on how binary tree is serialized on OJ.

**OJ's Binary Tree Serialization:**

The serialization of a binary tree follows a level order traversal, where '#' signifies a path terminator where no node exists below.

Here's an example:

```
   1
  / \
 2   3
    /
   4
    \
     5
```

The above binary tree is serialized as "{1,2,3,#,#,4,#,#,5}".

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
    public boolean isSymmetric(TreeNode root) {
        if(null==root)
            return true;
        return isSymmetricLR(root.left,root.right);
    }
    
    public boolean isSymmetricLR(TreeNode left,TreeNode right) {
        if(null == left || null == right)
            return left == right;
        if(left.val != right.val)
            return false;
        return isSymmetricLR(left.left,right.right) && isSymmetricLR(left.right,right.left); 
    }
}
```