---
title: Reorder_List
date: 2016-05-24 13:58:04
categories: [code]
tags: [leetcode,Linked List]
comments: yes
layout: post
---

## 题目

Given a singly linked list L: L0→L1→…→Ln-1→Ln,

reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…

You must do this in-place without altering the nodes' values.

For example,

Given {1,2,3,4}, reorder it to {1,4,2,3}.

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
    public void reorderList(ListNode head) {
        if(null == head || null == head.next)
            return;
        //Find the middle of the list
        ListNode slow = head;
        ListNode fast = head;
        while(null != fast.next && null != fast.next.next) {
            slow = slow.next;
            fast = fast.next.next;
        }
        
        //Reverse the half after middle  1->2->3->4->5->6 to 1->2->3->6->5->4
        ListNode pMid = slow;
        ListNode pCur = slow.next;//4
        while(null != pCur.next) {
            ListNode pNext = pCur.next;//5
            pCur.next = pNext.next;//4->6
            pNext.next = pMid.next;//5->4->6
            pMid.next = pNext;//3->5->4->
        }
        
        //Start reorder one by one  1->2->3->6->5->4 to 1->6->2->5->3->4
        ListNode pFir = head;
        ListNode pSec = pMid.next;
        while(pFir != pMid){
            pMid.next = pSec.next;
            pSec.next = pFir.next;
            pFir.next = pSec;
            pFir = pSec.next;
            pSec = pMid.next;
        }
    }
}
```