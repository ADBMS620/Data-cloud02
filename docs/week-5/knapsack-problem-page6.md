---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---
# 0/1 Knapsack using Least Cost Branch and Bound

Given **N** items with weights **W[0..n-1]**, values **V[0..n-1]** and a knapsack with capacity **C**, select the items such that: 

1. The sum of weights taken into the knapsack is less than or equal to C.
2. The sum of values of the items in the knapsack is maximum among all the possible combinations.

**Examples:** 
 
```plaintext

Input: N = 4, C = 15, V[]= {10, 10, 12, 18}, W[]= {2, 4, 6, 9} 
Output: 
Items taken into the knapsack are 
1 1 0 1 
Maximum profit is 38 
Explanation: 
1 in the output indicates that the item is included in the knapsack while 0 indicates that the item is excluded. 
Since the maximum possible cost allowed is 15, the ways to select items are: 
(1 1 0 1) -> Cost = 2 + 4 + 9 = 15, Profit = 10 + 10 + 18 = 38. 
(0 0 1 1) -> Cost = 6 + 9 = 15, Profit = 12 + 18 = 30 
(1 1 1 0) -> Cost = 2 + 4 + 6 = 12, Profit = 32 
Hence, maximum profit possible within a cost of 15 is 38.
Input: N = 4, C = 21, V[]= {18, 20, 14, 18}, W[]= {6, 3, 5, 9} 
Output: 
Items taken into the knapsack are 
1 1 0 1 
Maximum profit is 56 
Explanation: 
Cost = 6 + 3 + 9 = 18 
Profit = 18 + 20 + 18 = 56

```

 **Approach**

In this post, the implementation of Branch and Bound method using **Least Cost (LC)** for the *0/1 Knapsack Problem* is discussed.

Branch and Bound can be solved using FIFO, LIFO and **LC** strategies. The **least cost(LC)** is considered the most intelligent as it selects the next node based on a **Heuristic Cost Function**. It picks the one with the least cost.

As **0/1 Knapsack** is about maximizing the total value, we cannot directly use the **LC Branch and Bound technique** to solve this. Instead, we convert this into a minimization problem by taking negative of the given values. 

Follow the steps below to solve the problem:

1. Insert the items based on their value/weight (V/W) ratio.
2. Insert a dummy node into the priority queue.
3. Repeat the following steps until the priority queue is empty:
   - Extract the best complete path or the best path in progress and attach it to the current node.
   - If the upper bound of the current node is less than `minLB` (the minimum lower bound of all the nodes explored), then there is no point in exploring further. Continue to the next node. The reason for not considering the nodes whose upper bound is greater than `minLB` is that the best possible solution for that node might be better than `minLB`.
   - Update the path array.
   - If the level of the current node is `N`, then check whether the best path so far is of no use.
   - If the current node's level is `N`, and it is of no use, update the `finalPath` and `minLB`.
   - Calculate the lower and upper bounds of the right child of the current node.
   - If the current node can be inserted into the knapsack, calculate the lower and upper bounds of the left child of the current node.
   - Update the `minLB` and insert the children if their upper bound is less than `minLB`.


[⬅️ Back](/Data-cloud02/docs/week-5/knapsack-problem-page5)
