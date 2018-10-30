---
title: Bulls_and_Cows
date: 2016-03-31 12:23:55
categories: [code]
tags: [leetcode,Hash Table]
fullview: 
shortinfo: 
description: 
comments: yes
layout: post
---

## 题目

You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.

For example:

> Secret number:  "1807"
> Friend's guess: "7810"

Hint: 1 bull and 3 cows. (The bull is 8, the cows are 0, 1 and 7.)

Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. In the above example, your function should return "1A3B".

Please note that both secret number and friend's guess may contain duplicate digits, for example:

> Secret number:  "1123"
> Friend's guess: "0111"

In this case, the 1st 1 in friend's guess is a bull, the 2nd or 3rd 1 is a cow, and your function should return "1A1B".

You may assume that the secret number and your friend's guess only contain digits, and their lengths are always equal.

## 代码

```c
char* getHint(char* secret, char* guess) {
    int bull = 0;
    int cow = 0;
    int i;
    int s_hit[10];
    int g_hit[10];
    int length = strlen(guess);
    memset(s_hit,0,sizeof(int)*10);
    memset(g_hit,0,sizeof(int)*10);
    for(i=0;i<length;i++){
        if(secret[i]==guess[i]){
            bull++;
        }else{
            s_hit[secret[i]-'0']++;
            g_hit[guess[i]-'0']++;
        }
    }
    for(i=0;i<10;i++){
        cow+=(s_hit[i]<g_hit[i]?s_hit[i]:g_hit[i]);
    }
    sprintf(guess,"%dA%dB",bull,cow);
    return guess;
}
```