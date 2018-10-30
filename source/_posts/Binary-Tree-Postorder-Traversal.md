---
title: Binary_Tree_Postorder_Traversal
date: 2016-05-31 14:58:20
categories: [code]
tags: [leetcode,Tree,Stack]
comments: yes
layout: post
---

## 题目

Given a binary tree, return the postorder traversal of its nodes' values.

For example:

Given binary tree {1,#,2,3},

```
   1
    \
     2
    /
   3
```

return [3,2,1].

**Note:** Recursive solution is trivial, could you do it iteratively?

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
    public List<Integer> postorderTraversal(TreeNode root) {
        LinkedList<Integer> res = new LinkedList<>();
        Stack<TreeNode> stack = new Stack<>();
        if(root == null)
            return res;
        stack.push(root);
        while(!stack.isEmpty()) {
            TreeNode node = stack.pop();
            res.addFirst(node.val);
            if(node.left != null) {
                stack.push(node.left);
            }
            if(node.right != null) {
                stack.push(node.right);
            } 
        }
        return res;
    }
}
```