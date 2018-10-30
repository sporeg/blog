---
title: Remove_Duplicates_from_Sorted_List_II
date: 2016-04-01 11:18:48
categories: [code]
tags: [leetcode,Linked List]
comments: yes
layout: post
---

## 题目

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

For example

> Given 1->2->3->3->4->4->5, return 1->2->5.
> Given 1->1->1->2->3, return 2->3.

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
    public ListNode deleteDuplicates(ListNode head) {
        if(null==head)
            return null;
        ListNode pHead = new ListNode(0);
        ListNode pTail = pHead;
        ListNode pNext = head;
        pHead.next = head;
        while(null!=pNext){
            while(null!=pNext.next && pNext.val==pNext.next.val){
                pNext = pNext.next;
            }
			//pNext.val有可能是重复元素
			//pTail.next为首，pNext为尾，首尾相同则说明pNext.val不是重复元素
            if(pTail.next==pNext){
                pTail = pTail.next;
            }else{
                pTail.next = pNext.next;
            }
            pNext = pNext.next;
        }
        return pHead.next;
    }
}
```
