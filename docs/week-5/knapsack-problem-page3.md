---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---

# 0/1 Knapsack Problem to print all possible solutions
Given weights and profits of **N** items, put these items in a knapsack of capacity **W**. The task is to print all possible solutions to the problem in such a way that there are no remaining items left whose weight is less than the remaining capacity of the knapsack. Also, compute the maximum profit.

**Examples:** 

```plaintext
Input: Profits[] = {60, 100, 120, 50} 
Weights[] = {10, 20, 30, 40}, W = 40 
Output: 
10: 60, 20: 100, 
10: 60, 30: 120, 
Maximum Profit = 180 
Explanation: 
Maximum profit from all the possible solutions is 180


Input: Profits[] = {60, 100, 120, 50} 
Weights[] = {10, 20, 30, 40}, W = 50 
Output: 
10: 60, 20: 100, 
10: 60, 30: 120, 
20: 100, 30: 120, 
Maximum Profit = 220 
Explanation: 
Maximum profit from all the possible solutions is 220
```

**Approach:** The idea is to make pairs for the weight and the profits of the items and then try out all permutations of the array and including the weights until their is no such item whose weight is less than the remaining capacity of the knapsack. Meanwhile after including an item increment the profit for that solution by the profit of that item.

[⬅️ Back](knapsack-problem-page2.md)       [Next ➡️](knapsack-problem-page4.md)




