---
title: Word_Ladder
date: 2016-03-24 10:07:04
layout: post
categories: [code]
tags: [leetcode]
fullview: 
shortinfo: 
description: 
comments: yes
thread: 9
---

## 题目

Given two words (beginWord and endWord), and a dictionary's word list, find the length of shortest transformation sequence from beginWord to endWord, such that:

Only one letter can be changed at a time

Each intermediate word must exist in the word list

For example,

> Given:

> beginWord = "hit"

> endWord = "cog"

> wordList = ["hot","dot","dog","lot","log"]

> As one shortest transformation is "hit" -> "hot" -> "dot" -> "dog" -> "cog",

> return its length 5.

Note:

* Return 0 if there is no such transformation sequence.
* All words have the same length.
* All words contain only lowercase alphabetic characters.

## 解题思路

BFS广搜，用队列解决

## 代码

``` java
public class Solution {
    public int ladderLength(String beginWord, String endWord, Set<String> wordList) {
        Queue<String> queue = new LinkedList<String>();
        queue.add(beginWord);
        wordList.add(endWord);
        int length = 1;
        while(!queue.isEmpty())
        {
            length++;
            int queueSize = queue.size();//队列长度会变化，所以用变量记下来
            for(int i = 0; i < queueSize; i++)
            {
                String checkWord = queue.poll();
                char[] w = checkWord.toCharArray();
                for(int j = 0; j < w.length; j++)
                {
                    char c = w[j];
                    for(int k = 0; k < 26; k++)
                    {
                        w[j] = (char)('a' + k);
                        String s = new String(w);
                        if(endWord.equals(s))
                        {
                            return length;
                        }
                        if(wordList.contains(s))
                        {
                            queue.add(s);
                            wordList.remove(s);
                        }
                    }
                    w[j] = c;
                }
            }
        }
        return 0;
    }
}

```