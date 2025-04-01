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
![ Knapsack Problem 4](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/Knapsack%20Problem/Knapsack-problem%204.jpg?raw=true)

## 4. 0/1 Knapsack using Backtracking:
```plainetext
We can use Backtracking to optimize the Brute Force solution. In the tree representation, we can do
DFS of tree. If we reach a point where a solution no longer is feasible, there is no need to
continue exploring. In the given example, backtracking would be much more effective if we had
even more items or a smaller knapsack capacity.
```

![ Knapsack Problem 5](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/Knapsack%20Problem/Knapsack-problem%205.jpg?raw=true)

## 5. 0/1 Knapsack using Branch and Bound:
```plainetext
The backtracking based solution works better than brute force by ignoring infeasible solutions.
We can do better (than backtracking) if we know a bound on best possible solution subtree rooted
with every node. If the best in subtree is worse than current best, we can simply ignore this
node and its subtrees. So we compute bound (best solution) for every node and compare the bound
with current best solution before exploring the node.
```
![ Knapsack Problem 6](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-5/Knapsack%20Problem/Knapsack-problem%206.jpg?raw=true)

## How to find bound for every node for 0/1 Knapsack?
```plainetext
The idea is to use the fact that the Greedy approach provides the best solution for Fractional
Knapsack problem. To check if a particular node can give us a better solution or not, we
compute the optimal solution (through the node) using Greedy approach. If the solution
computed by Greedy approach itself is more than the best so far, then we can’t get a
better solution through the node. 
```
Follow the steps to implement the above idea

1. Sort all items in **decreasing order of ratio of value per unit weight** so that  
   an upper bound can be computed using the Greedy Approach.

2. Initialize maximum profit, `maxProfit = 0`, create an empty queue `Q`, and  
   create a **dummy node** of the decision tree. Enqueue it to `Q`.  
   (Profit and weight of the dummy node are `0`.)

3. Do the following while `Q` is not empty:
   - Extract an item from `Q`. Let the extracted item be `u`.
   - Compute the profit of the next-level node.  
     If the profit is more than `maxProfit`, then update `maxProfit`.
   - Compute the bound of the next-level node.  
     If the bound is more than `maxProfit`, then enqueue that node to `Q`.
   - Consider the case when next level node is not considered as part of solution and
     add a node to queue with level as next, but weight and profit without considering next level nodes.


**Time Complexity: O(2^N)**

**Auxiliary Space: O(N)**

Branch and bound is very useful technique for searching a solution but in worst case, we need 
to fully calculate the entire tree. At best, we only need to fully calculate one path through 
the tree and prune the rest of it. 

[⬅️ Back](knapsack-problem-page4.md)         [Next ➡️](knapsack-problem-page6.md)
     
 
