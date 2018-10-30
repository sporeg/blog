---
title: Merge_Two_Sorted_Lists
date: 2016-04-14 11:14:59
categories: [code]
tags: [leetcode,Linked List]
comments: yes
layout: post
---

## 题目

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

## 代码

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(null==l1)
            return l2;
        if(null==l2)
            return l1;
        if(l1.val<=l2.val) {
            l1.next = mergeTwoLists(l1.next,l2);
            return l1;
        }else {
            l2.next = mergeTwoLists(l1,l2.next);
            return l2;
        }
    }
}
```