---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---
# Printing Items in 0/1 Knapsack
Given weights and values of n items, put these items in a knapsack of capacity W to get the maximum total value in the knapsack. In other words, given two integer arrays, val[0..n-1] and wt[0..n-1] represent values and weights associated with n items respectively. Also given an integer W which represents knapsack capacity, find out the items such that sum of the weights of those items of a given subset is smaller than or equal to W. You cannot break an item, either pick the complete item or don’t pick it (0-1 property).

**Examples:**

```plaintext
Input : val[] = {60, 100, 120};
         wt[] = {10, 20, 30};
         W = 50;
Output : 220 //maximum value that can be obtained
           30 20 //weights 20 and 30 are included.

Input : val[] = {40, 100, 50, 60};
         wt[] = {10, 20, 10, 40, 30};
         W = 60;
Output : 200
           30 20 10
```

Approach : 

Let val[] = {1, 4, 5, 7}, wt[] = {1, 3, 4, 5} 

W = 7. 

The 2d knapsack table will look like : 
 
