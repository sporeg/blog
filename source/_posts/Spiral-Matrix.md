---
title: Spiral Matrix
date: 2016-03-23 11:40:04
layout: post
categories: [code]
tags: [code]
fullview: 
shortinfo: 
description: 螺旋矩阵
comments: yes
thread: 7
---

## 题目

如下矩阵：

|  |  |  |  |  |
|:---:|:---:|:---:|:---:|:---:|
| 1 |  2 |  3 |  4 |  5 | 
| 16 | 17 | 18 | 19 | 6 |
| 15 | 24 | 25 | 20 | 7 | 
| 14 | 23 | 22 | 21 | 8 |
| 13 | 12 | 11 | 10 | 9 |

从1开始，依次递增呈螺旋状

## 输入

行数，列数，指定行

> {row,col,row_m}

## 输出

row_m行所有数

## 解题思路

1) 沿矩阵一周，回到起始位置

* 向右
* 向下
* 向左
* 向上

2) 向右下一格(i++;j++)

3) 矩阵长宽各减1，之后回到步骤1)

注意： 

* 填周长时调整(i,j)防止发生错误
* 数组从0开始

## 代码

``` c
void printmatrow(int row,int col,int row_m)
{
	int **matrix=(int **)malloc(sizeof(int*) * row);
	int i,j,num,num_max;
	int row_min,row_max,col_min,col_max;
	for(i=0;i<row;i++)
	{
		matrix[i] = (int *)malloc(sizeof(int) * col);
		memset(matrix[i],0,sizeof(int) * col);
	}
	i=0;
	j=0;
	row_min=0;
	col_min=0;
	row_max=row;
	col_max=col;
	num = 1;
	num_max=row*col;
	while(num<=num_max)
	{
		//上横 向右
		for(;col_max>=0&&j<col_max;j++,num++)
		{
			matrix[i][j] = num;
		}
		if(num>num_max)
			break;
		//左下移动一格 右竖 向下
		for(i++,j--;row_max>=0&&i<row_max;i++,num++)
		{
			matrix[i][j] = num;
		}
		if(num>num_max)
			break;
		//左上移动一格 下横 向左
		for(i--,j--;col_min<col_max&&j>=col_min;j--,num++)
		{
			matrix[i][j] = num;
		}
		if(num>num_max)
			break;
		//右上移动一格 左竖 向上到起始位置下方一格
		for(i--,j++,row_min++;row_min<row_max&&i>=row_min;i--,num++)
		{
			matrix[i][j] = num;
		}
		//此时回到起始位置
		if(num>num_max)
			break;
		//右下移动一格
		i++;
		j++;
		//缩小矩阵长宽
		col_min++;
		col_max--;
		row_max--;
	}
	//打印第row_m行
	for(j=0;j<col;j++)
	{
		printf("%d ",matrix[row_m-1][j]);
	}
	printf("\n");
	for(i=0;i<row;i++)
	{
		free(matrix[i]);
	}
	free(matrix);
}
```