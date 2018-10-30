---
title: Remove_Duplicates_from_Sorted_List
date: 2016-04-12 19:17:54
categories: [code]
tags: [leetcode,Linked List]
comments: yes
layout: post
---

## 题目

Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,

Given 1->1->2, return 1->2.

Given 1->1->2->3->3, return 1->2->3.

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
    public ListNode  deleteDuplicates(ListNode head) {
        if(head==null)
            return null;
        ListNode pre = head;
        ListNode cur = head.next;
        while(cur!=null) {
            if(cur.val != pre.val) {
                pre.next = cur;
                pre = pre.next;
            }
            cur = cur.next;
        }
        pre.next = null;
        return head;
    }
}
```