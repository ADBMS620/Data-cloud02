---
layout: page
menubar: docs_menu
title: Installation
subtitle: Getting Started
show_sidebar: false
toc: true
---

## Bubble Sort Algorithm

Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.
Goals
By the end of this lesson, you should be able to:

describe bubble sort algorithm steps and ways to optimise them.
implement bubble sort algorithm to sort a sequence of number.
Keywords
sorting, bubble sort

The best way to practice your programming skills is by writing actual code. One of the common computation is to sort some items in some way. For example, sorting a number from smallest to biggest or names from A to Z. In this notebook, we will describe some sorting algorithms which you can implement in Python.

A Note about Show Pseudocode Button
Throughout these notes, you will see a button that says Show Pseudocode as shown below. Go ahead and click it.

Show Pseudocode
Another thing about pseudocode is that it is not a Python code.

Pseudocode ≠ Code
Do not copy and paste the pseudocode into any Python interpreter or Jupyter notebook cell and expect it to work. There is a good reason why it is called pseudocode and not pythoncode. See definition of pseudo.

Bubble Sort
Bubble sort is one of the simplest sorting algorithms. We will be following the PCDIT framework (Problem statement, Test Cases, Design of Algorithm, Implementation, and Testing) in describing the steps of these algorithms.

Problem Statement
The problem is specified as follows. Given a sequence of numbers, write some steps to sort the sequence in some order. Usually, we will sort the sequence from the smallest to the largest.

### Algorithm Steps:
1. Compare the first element with the second element.
2. If the first element is greater than the second, swap them.
3. Continue comparing adjacent elements and swapping them until the entire list is sorted.
4. Repeat the process until no more swaps are needed.

### Example:

## Insertion Sort Algorithm:

Insertion sort is a comparison-based sorting algorithm that builds the final sorted array one element at a time by inserting each element into its correct position within the already sorted portion of the array.

### Goals:

By the end of this lesson, you should be able to:

describe insertion sort algorithm steps and ways to optimise them.
implement insertion sort algorithm.

Insertion sort is another algorithm that solves the same problem as bubble sort. Let's start by looking at the same test case

### Test Case

Given the following input:

numbers = [16, 14, 10, 8, 7, 8, 3, 2, 4, 1]

We want to write some steps that sort the numbers such that the output will be:

[1, 2, 3, 4, 7, 8, 8, 10, 14, 16]

We start from the second element in the list, i.e. 14.

[16, 14, 10, 8, 7, 8, 3, 2, 4, 1]

We then compare that number with the one on the left. If it is smaller, then we will swap. Since 
14
<
16
14<16, we do a swap.

[14, 16, 10, 8, 7, 8, 3, 2, 4, 1]

Since 14 has reached its place, we now move to the third element in the list, i.e. 10. Since 
10
<
16
10<16, we swap (16, 10).

[14, 16, 10, 8, 7, 8, 3, 2, 4, 1]

[14, 10, 16, 8, 7, 8, 3, 2, 4, 1]

Now we continue comparing 10 with the one on its left, i.e. 14. Since 
10
<
14
10<14, we swap (14, 10).

[14, 10, 16, 8, 7, 8, 3, 2, 4, 1]

[10, 14, 16, 8, 7, 8, 3, 2, 4, 1]

Now 10 has reached its position.

We now move to the fourth element, i.e. 8, and compare it with the number on its left. Since 
8
<
16
8<16, we swap (16, 8). We then continue swapping until 8 reaches its position.

[10, 14, 16, 8, 7, 8, 3, 2, 4, 1]

[10, 14, 8, 16, 7, 8, 3, 2, 4, 1]

[10, 14, 8, 16, 7, 8, 3, 2, 4, 1]

[10, 8, 14, 16, 7, 8, 3, 2, 4, 1]

[10, 8, 14, 16, 7, 8, 3, 2, 4, 1]

[8, 10, 14, 16, 7, 8, 3, 2, 4, 1]

We now move to the fifth element, i.e. 7. We then have the same swapping all the way until 7 reaches its place.

[8, 10, 14, 16, 7, 8, 3, 2, 4, 1]

[8, 10, 14, 7, 16, 8, 3, 2, 4, 1]

[8, 10, 14, 7, 16, 8, 3, 2, 4, 1]

[8, 10, 7, 14, 16, 8, 3, 2, 4, 1]

[8, 10, 7, 14, 16, 8, 3, 2, 4, 1]

[8, 7, 10, 14, 16, 8, 3, 2, 4, 1]

[8, 7, 10, 14, 16, 8, 3, 2, 4, 1]

[7, 8, 10, 14, 16, 8, 3, 2, 4, 1]

We now move to the sixth element, i.e. 8. We will continue swapping until 8 encounters another 8 in the 2nd element. At this point, the swapping will stop.

[7, 8, 10, 14, 16, 8, 3, 2, 4, 1]

[7, 8, 10, 14, 8, 16, 3, 2, 4, 1]

[7, 8, 10, 14, 8, 16, 3, 2, 4, 1]

[7, 8, 10, 8, 14, 16, 3, 2, 4, 1]

[7, 8, 10, 8, 14, 16, 3, 2, 4, 1]

[7, 8, 8, 10, 14, 16, 3, 2, 4, 1]

[7, 8, 8, 10, 14, 16, 3, 2, 4, 1]

no swapping occurs

We can now move to the seventh element, i.e. 3. We will not show the swapping steps, and only show the final position of the seventh element.

[3, 7, 8, 8, 10, 14, 16, 2, 4, 1]

We do the same with the eighth element, i.e. 2.

[2, 3, 7, 8, 8, 10, 14, 16, 4, 1]

Similarly, with the nineth element, i.e. 4. However, this element will stop swapping when it sees the number lower than itself, so it will stop when it sees 3.

[2, 3, 4, 7, 8, 8, 10, 14, 16, 1]

Finally, the tenth element, i.e. 1, will move all the way to the first position.

[1, 2, 3, 4, 7, 8, 8, 10, 14, 16]

Design of Algorithm
Looking at the above case, we can try to write down our algorithm in pseudocode. Several things to note.

Outer and Inner Iteration
There are two iterations in the steps above:

outer iteration is moving from the second element to the last element in the list. What the outer iteration does is to place that n-th element into its position.
inner iteration is swapping the n-th element until either: a) it reaches the most left position, or b) the number on its left is smaller
Fixed Outer Iteration
The number of outer iteration is fixed, which is 
n
−
1
n−1. This is because it starts from the second element to the last element. So if there are 
n
n elements, it will repeat itself 
n
−
1
n−1 times.

The outer iteration starts from the second element, which is index 1.

Non-Fixed Inner Iteration
The number of inner iteration is not fixed since it depends on the two cases stated above. The maximum number of iteration is when the number reaches the most left position. In this case for element at position 
i
i, it will repeat 
i
i times. If it sees a number that is smaller than itself, the number of iteration for the element at position 
i
i will be less than 
i
i.

Insertion Sort v1
Let's write it down.

Show Pseudocode
Optimised Insertion Sort
We can improve the algorithm slightly by reducing the number of assignment in the inner loop. This means that instead of swapping and assigning elements in the inner iteration, we only assign the element once it finds its final position. To do this, we store the element we are going to move into a temporary variable.

Test Case
Let's illustrate this when the outer iteration is moving the sixth element, i.e. 8.

[7, 8, 10, 14, 16, 8, 3, 2, 4, 1]

Instead of swapping (16, 8) pair, we store 8 into a temporary variable. Then we compare the temporary variable with 16. Since 
8
<
16
8<16, we simply shift 16 to the right. We indicate the position to be replaced with an underscore below. Since no swap is being done, the old value remains after the shift.

[7, 8, 10, 14, 16, _8_, 3, 2, 4, 1] , temporary = 8

[7, 8, 10, 14, _16_, 16, 3, 2, 4, 1] , temporary = 8

We then now compare, the temporary variable with 14. Since 
8
<
14
8<14, we shift 14 to the right.

[7, 8, 10, 14, _16_, 16, 3, 2, 4, 1] , temporary = 8

[7, 8, 10, _14_, 14, 16, 3, 2, 4, 1] , temporary = 8

We do the same with 10.

[7, 8, 10, _14_, 14, 16, 3, 2, 4, 1] , temporary = 8

[7, 8, _10_, 10, 14, 16, 3, 2, 4, 1] , temporary = 8

Now, we compare the temporary variable with 8. But since 8 is not less than the value in the temporary variable, we do not swap, and store the temporary value to element on the right of it. We can then stop the inner iteration, and move to the next pass of outer iteration.

[7, 8, _10_, 10, 14, 16, 3, 2, 4, 1] , temporary = 8

[7, 8, 8, 10, 14, 16, 3, 2, 4, 1] , temporary = 8
