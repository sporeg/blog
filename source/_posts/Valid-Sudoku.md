---
layout: post
title: Valid Sudoku
date: 2016-03-22 15:53:50
categories: [code]
tags: [leetcode]
fullview: 
shortinfo: 
description: Determine if a Sudoku is valid
comments: yes
thread: 6
---

## 题目

Determine if a Sudoku is valid, according to: Sudoku Puzzles - The Rules.

The Sudoku board could be partially filled, where empty cells are filled with the character '.'.

![A partially filled sudoku which is valid.](/images/Valid_Sudoku.png)

**Note:**
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.

## 代码

``` c
bool isValidSudoku(char** board, int boardRowSize, int boardColSize) {
    int i,j,k;
    int checki[9][9]={0},checkj[9][9]={0},checkk[9][9]={0};
    int num;
    for(i=0;i<boardRowSize;i++)
    {
        for(j=0;j<boardColSize;j++)
        {
            k = i/3*3+j/3;
            num = board[i][j]-'1';
            if(board[i][j] != '.')
            {
                if(checki[i][num] || checkj[j][num] || checkk[k][num])
                {
                    return false;
                }
                checki[i][num]=checkj[j][num]=checkk[k][num]=1;
            }
        }
    }
    return true;
}

```

添加位运算，减少空间开销

```c
bool isValidSudoku(char** board, int boardRowSize, int boardColSize) {
    int i,j,k;
    int checki[9]={0},checkj[9]={0},checkk[9]={0};
    int num;
    for(i=0;i<boardRowSize;i++)
    {
        for(j=0;j<boardColSize;j++)
        {
            k = i/3*3+j/3;
            num = 1 << (board[i][j]-'1');
            if(board[i][j] != '.')
            {
                if((checki[i]|num)==checki[i] || (checkj[j]|num)==checkj[j] || (checkk[k]|num)==checkk[k])
                {
                    return false;
                }
                checki[i]=checki[i]|num;
                checkj[j]=checkj[j]|num;
                checkk[k]=checkk[k]|num;
            }
        }
    }
    return true;
}

```