---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---
# 0/1 Knapsack using Branch and Bound

Given two arrays **v[]** and **w[]** that represent **values** and **weights** associated with **n** items respectively. Find out the maximum value subset(Maximum Profit) of **v[]** such that the sum of the weights of this subset is smaller than or equal to Knapsack capacity **W**.

**Note:** The constraint here is we can either put an item completely into the bag or cannot put it at all [It is not possible to put a part of an item into the bag.
```plaintext
Input: N = 3, W = 4, v[] = {1, 2, 3}, w[] = {4, 5, 1}
Output: 3
Explanation: There are two items which have weight less than or equal to 4.
             If we select the item with weight 4, the possible profit is 1.
             And if we select the item with weight 1, the possible profit
             is 3. So the maximum possible profit is 3. Note that we cannot
             put both the items with weight 4 and 1 together as the capacity
             of the bag is 4.


Input: N = 5, W = 10, v[] = {40, 50, 100, 95, 30}, w[] = {2, 3.14, 1.98, 5, 3}
Output: 235
```

# Branch and Bound Algorithm:
```plainetext
Branch and bound is an algorithm design paradigm which is generally used for solving combinatorial
optimization problems. These problems typically exponential in terms of time complexity and may
require exploring all possible permutations in worst case. Branch and Bound solve these problems
relatively quickly.
```
Firstly, let us explore all approaches for this problem.

## 1. 0/1 Knapsack using Greedy Approach:
```plainetext
A Greedy approach is to pick the items in decreasing order of value per unit weight. The Greedy
approach works only for fractional knapsack problem and may not produce correct result for
0/1 knapsack.
```

## 2. 0/1 Knapsack using Dynamic Programming (DP):
```plainetext
We can use Dynamic Programming (DP) for 0/1 Knapsack problem. In DP, we use a 2D table of size n x W.
 The DP Solution doesn’t work if item weights are not integers.
```

## 3. 0/1 Knapsack using Brute Force:
```plainetext
Since DP solution doesn’t always work just like in case of non-integer weight, a solution is to use
Brute Force. With n items, there are 2n solutions to be generated, check each to see if they satisfy
the constraint, save maximum solution that satisfies constraint. This solution can be expressed as tree.
```
