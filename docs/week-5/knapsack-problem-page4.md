---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---

# 0-1 knapsack queries

Given an integer array **W[]** consisting of weights of the items and some queries consisting of capacity **C** of knapsack, for each query find maximum weight we can put in the knapsack. Value of **C** doesn’t exceed a certain integer **C_MAX**.

**Examples:** 

```plaintext
Input: W[] = {3, 8, 9} q = {11, 10, 4} 
Output: 
11 
9 
3 
If C = 11: select 3 + 8 = 11 
If C = 10: select 9 
If C = 4: select 3


Input: W[] = {1, 5, 10} q = {6, 14} 
Output: 
6 
11
```


Its recommended that you go through this article on 0-1 knapsack before attempting this problem.

**Naive approach:** For each query, we can generate all possible subsets of weight and choose the one that has maximum weight among all those subsets that fits in the knapsack. Thus, answering each query will take exponential time.

**Efficient approach:** We will optimize answering each query using dynamic programming. 
0-1 knapsack is solved using 2-D DP, one state ‘i’ for current index(i.e select or reject) and one for remaining capacity ‘R’. 
Recurrence relation is 

```plaintext
dp[i][R] = max(arr[i] + dp[i + 1][R – arr[i]], dp[i + 1][R])
```
 We will pre-compute the 2-d array dp[i][C] for every possible value of ‘C’ between 1 to C_MAX in O(C_MAX*i). 
 
Using this, pre-computation we can answer each queries in O(1) time.

**Efficient approach:** Using DP Tabulation method ( Iterative approach )

The approach to solve this problem is same but **DP tabulation(bottom-up)** method is better then **Dp +** **memoization(top-down)** because memoization method needs extra stack space of recursion calls.

**Steps to solve this problem :**

* Create a DP to store the solution of the subproblems and initialize it with 0.
* Initialize the DP  with base cases
* Now Iterate over subproblems to get the value of current problem form previous computation of subproblems stored in DP.
* After filling the DP now in Main function call every query and get the answer stored in DP.

**Time complexity:** O(n*c)

**Auxiliary Space:** O(n*C)

[⬅️ Back](knapsack-problem-page3.md)


