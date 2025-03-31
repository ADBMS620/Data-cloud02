---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---
# 0/1 Knapsack Problem
Given **n** items where each item has some weight and profit associated with it and also given a bag with capacity **W**, [i.e., the bag can hold at most **W** weight in it]. The task is to put the items into the bag such that the sum of profits associated with them is the maximum possible. 


**Note:** The constraint here is we can either put an item completely into the bag or cannot put it at all [It is not possible to put a part of an item into the bag].

> **Input:**  W = 4, profit[] = [1, 2, 3], weight[] = [4, 5, 1]
> 
> **Output:** 3
> 
>**Explanation:** There are two items which have weight less than or equal to 4. If we select the item with weight 4, the possible profit is 1. And if we select the item with weight 1, the possible profit is 3. So the maximum possible profit is 3. Note that we cannot put both the items with weight 4 and 1 together as the capacity of the bag is 4.
>
>
>**Input:** W = 3, profit[] = [1, 2, 3], weight[] = [4, 5, 6]
> 
>**Output**: 0

## Table of Content

* [[Naive Approach] Using Recursion O(2^n) Time and O(n) Space](#-naive-approach-using-recursion-o2n-time-and-on-space)
  
* [[Better Approach 1] Using Top-Down DP (Memoization) - O(n x W) Time and Space](#-using-top-down-dp-memoization---nx-w-time-and-space)
* [[Better Approach 2] Using Bottom-Up DP (Tabulation) - O(n x W) Time and Space](#using-bottom-up-dp-tabulation---nx-w-time-and-space)
* [[Expected Approach] Using Bottom-Up DP (Space-Optimized) - O(n x W) Time and O(W) Space](#-using-bottom-up-dp-space-optimized---nx-w-time-and-w-space)
* Problems based on 0-1 Knapsack

## [Naive Approach] Using Recursion O(2^n) Time and O(n) Space
> A simple solution is to consider all subsets of items and calculate the total weight and value of all subsets. Consider the only subsets whose total weight is smaller than W. From all such subsets, pick the subset with maximum value.
>
> **Optimal Substructure:** To consider all subsets of items, there can be two cases for every item. 


> * **Case 1:** The item is included in the optimal subset.
>   
>  * **Case 2:** The item is not included in the optimal set.
  
Follow the below steps to solve the problem:

The maximum value obtained from ‘n’ items is the max of the following two values. 

* Case 1 (pick the $n^{th}$ item): Value of the $n^{th}$ item + maximum value obtained by remaining (n-1) items and remaining weight i.e. (W-weight of the $n^{th}$ item).
* Case 2 (don’t pick the $n^{th}$ item): Maximum value obtained by (n-1) items and W weight.
* If the weight of the ' $n^{th}$ ' item is greater than ‘W’, then the $n^{th}$ item cannot be included and **Case 2** is the only possibility.

**Example**

![ Knapsack Problem 1](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/Knapsack%20Problem/Knapsack%20Problem%201.jpg?raw=true)

## [Better Approach 1] Using Top-Down DP (Memoization)- O(n x W) Time and Space

**Note:** The above function using recursion computes the same subproblems again and again. See the following recursion tree, K(1, 1) is being evaluated twice.

![ Knapsack Problem 2](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/Knapsack%20Problem/Knapsack%20Problem%202.jpg?raw=true)

As there are repetitions of the same subproblem again and again we can implement the following idea to solve the problem.

> If we get a subproblem the first time, we can solve this problem by creating a 2-D array that can store a particular state (n, w). Now if we come across the same state $(n, w)$ again instead of calculating it i again we can directly return its result stored in the table in constant time.

## [Better Approach 2] Using Bottom-Up DP (Tabulation) – O(n x W) Time and Space

There are two parameters that change in the recursive solution and these parameters go from 0 to n and 0 to W. So we create a 2D dp[][] array of size (n+1) x (W+1), such that **dp[i][j]** stores the maximum value we can get using **i** items such that the knapsack capacity is **j**.

* We first fill the known entries when m is 0 or n is 0.
* Then we fill the remaining entries using the recursive formula.

For each item i and knapsack capacity j, we decide whether to pick the item or not.

* **If we don’t pick the item:** dp[i][j] remains same as the previous item, that is dp[i – 1][j].
* **If we pick the item:** dp[i][j] is updated to val[i] + dp[i – 1][j – wt[i]].

## [Expected Approach] Using Bottom-Up DP (Space-Optimized) – O(n x W) Time and O(W) Space
> For calculating the current row of the dp[] array we require only previous row, but if we start traversing the rows from right to left then it can be done with a single row only

[Next ➡️](docs/week-5/knapsack-problem-page2.md)




