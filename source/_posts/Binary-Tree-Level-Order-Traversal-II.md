---
title: Binary_Tree_Level_Order_Traversal_II
date: 2016-04-19 14:02:47
categories: [code]
tags: [leetcode,Tree,Breadth-first Search]
comments: yes
layout: post
---

## 题目

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:

Given binary tree {3,9,20,#,#,15,7},

```
    3
   / \
  9  20
    /  \
   15   7
```

return its bottom-up level order traversal as:

```
[
  [15,7],
  [9,20],
  [3]
]
```

confused what "{1,#,2,3}" means? > read more on how binary tree is serialized on OJ.

OJ's Binary Tree Serialization:

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
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        List<List<Integer>> list = new LinkedList<List<Integer>>();
        if(null == root)
            return list;
        queue.offer(root);
        while(!queue.isEmpty()) {
            int level = queue.size();
            List<Integer> newList = new LinkedList<Integer>();
            for(int i=0;i<level;i++) {
                if(null != queue.peek().left)
                    queue.offer(queue.peek().left);
                if(null != queue.peek().right)
                    queue.offer(queue.peek().right);
                newList.add(queue.poll().val);
            }
            list.add(0,newList);
        }
        return list;
    }
}
```