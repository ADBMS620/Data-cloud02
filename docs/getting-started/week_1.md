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

### Bubble Sort
Bubble sort is one of the simplest sorting algorithms. We will be following the PCDIT framework (Problem statement, Test Cases, Design of Algorithm, Implementation, and Testing) in describing the steps of these algorithms.

Problem Statement
The problem is specified as follows. Given a sequence of numbers, write some steps to sort the sequence in some order. Usually, we will sort the sequence from the smallest to the largest.

### Algorithm Steps:
1. Compare the first element with the second element.
2. If the first element is greater than the second, swap them.
3. Continue comparing adjacent elements and swapping them until the entire list is sorted.
4. Repeat the process until no more swaps are needed.

Problem Statement
The problem is specified as follows. Given a sequence of numbers, write some steps to sort the sequence in some order. Usually, we will sort the sequence from the smallest to the largest.

### Test Case:
For example, given the following input:

numbers = [16, 14, 10, 8, 7, 8, 3, 2, 4, 1]

We want to write some steps that sort the numbers, such that the output will be:

[1, 2, 3, 4, 7, 8, 8, 10, 14, 16]

We can intuitively try to sort the numbers by comparing two numbers (a pair) at a time. If the order is incorrect, we will swap the two numbers. Let's illustrate the steps!

We start from the input:

[16, 14, 10, 8, 7, 8, 3, 2, 4, 1]

We compare the first two numbers (16, 14), i.e. positions 0 and 1 in the list. Since 16 is bigger than 14, we will swap them.

[14, 16, 10, 8, 7, 8, 3, 2, 4, 1]

Now we move to the next pair (16, 10), i.e. positions 1 and 2 in the list. Since 16 is bigger than 10, we will swap them again.

[14, 16, 10, 8, 7, 8, 3, 2, 4, 1]

[14, 10, 16, 8, 7, 8, 3, 2, 4, 1]

And next pair (16, 8), i.e. positions 2 and 3. Since 16 is bigger than 8, we will swap.

[14, 10, 16, 8, 7, 8, 3, 2, 4, 1]

[14, 10, 8, 16, 7, 8, 3, 2, 4, 1]

We continue until 16 reaches the last position.

[14, 10, 8, 16, 7, 8, 3, 2, 4, 1]

[14, 10, 8, 7, 16, 8, 3, 2, 4, 1]

--

[14, 10, 8, 7, 16, 8, 3, 2, 4, 1]

[14, 10, 8, 7, 8, 16, 3, 2, 4, 1]

--

[14, 10, 8, 7, 8, 16, 3, 2, 4, 1]

[14, 10, 8, 7, 8, 3, 16, 2, 4, 1]

--

[14, 10, 8, 7, 8, 3, 16, 2, 4, 1]

[14, 10, 8, 7, 8, 3, 2, 16, 4, 1]

--

[14, 10, 8, 7, 8, 3, 2, 16, 4, 1]

[14, 10, 8, 7, 8, 3, 2, 4, 16, 1]

--

[14, 10, 8, 7, 8, 3, 2, 4, 16, 1]

[14, 10, 8, 7, 8, 3, 2, 4, 1, 16]

So now the largest number has occupied its place in the last position. But the other numbers are still not in the right order. Therefore, we have to repeat the steps starting from the beginning again. We start from the pair (14, 10). This will repeat the pair-wise comparison and move 14 to the second last position. Similarly, we can see how 10 and 8 will reach their final position. Here, we no longer show the pair-wise comparison and swapping for brevity.

[10, 8, 7, 8, 3, 2, 4, 1, 14, 16]
[8, 7, 8, 3, 2, 4, 1, 10, 14, 16]
[7, 8, 3, 2, 4, 1, 8, 10, 14, 16]
At this point, we will start comparing the pair (7, 8). But since 7 is not greater than 8, there is no swap.

[7, 8, 3, 2, 4, 1, 8, 10, 14, 16]
Afterward, we will compare the pair (8, 3).

[7, 8, 3, 2, 4, 1, 8, 10, 14, 16]
Since 8 is greater than 3, there will be a swap, and these pair-wise swaps will continue to push 8 to its final position.

[7, 3, 2, 4, 1, 8, 8, 10, 14, 16]
Now we begin again with the pair (7, 3) and push 7 to its final position. The detailed pair-wise swapping is not shown below, but the final arrangement at the end of this iteration will be as the one below.

[3, 2, 4, 1, 7, 8, 8, 10, 14, 16]
At this point, we will start a new iteration by comparing the pair (3, 2). Since 3 is greater than 2, there will be a swap. The next comparison will fall on the pair (3, 4), i.e. [2, 3, 4, 1, 7, 8, 8, 10, 14, 16]. But since 3 is less than 4, there is no swap happening. And the rest of the comparison will push 4 to its final position.

[2, 3, 1, 4, 7, 8, 8, 10, 14, 16]
A similar situation occurs. There is no swap between (2, 3), but then it will swap (3, 1).

[2, 1, 3, 4, 7, 8, 8, 10, 14, 16]
In the last iteration, it wil swap (2, 1).

[1, 2, 3, 4, 7, 8, 8, 10, 14, 16]
Here's an animated example from Wikipedia,sorting a different sequence of numbers.

### Design of Algorithm
After we work on the test cases, we can now write down the steps in pseudocode. Several things to note from the above test cases:

There are two kind of iterations:
the inner iteration is when we compare the pairs (a, b) and do a swap if 
a
>
b
a>b,
the outer iteration is when repeat the inner iteration pass starting from the first pair again.
The number of inner iteration is the 
n
−
1
n−1, where 
n
n is the number of elements in the list. This is because the inner iteration compares a pair. So if there is 
n
n elements, there will be 
n
−
1
n−1 pairs to compare.
The number of outer iteration is also 
n
−
1
n−1. You can refer back to the case above that there were 9 outer iterations for the 10 elements.
Let's write down what we did in the above case. Note that in this algorithm we chose not to return the sorted list as a new object, but rather sort the list in place. This means that the input list is modified and the sorted list exists in the object pointed by the input list. The advantage of this is that the list need not be duplicated and the memory is saved as we deal only with one list.

Show Pseudocode
Optimised Bubble Sort
### Bubble Sort v2
We can optimized bubble sort algorithm by noting the following:

If the sequence is already in order, we can reduce the next outer iteration.

For example, if the input is

[16, 1, 2, 3, 4, 5]

The first iteration will push 16 to the last position.

[1, 2, 3, 4, 5, 16]

In the second iteration, no swap is made since all the numbers are already in the correct order. However, with the above algorithm, the outer iteration will still repeat for 
n
−
1
n−1 times. We can conclude therefore that if no swap is made in one pass of outer iteration, the sequence is already in order, and we can stop the outer iteration. We can then modify the pseudocode as follows.

Show Pseudocode

### Comparison with v1
Let's compare this with version 1. Notice that the number of outer iteration is much less in version two as compared to version one. The n-th pass of the outer iteration will place the n-th largest number to its final position. For example, in the given input below,

[16, 14, 10, 8, 7, 8, 3, 2, 4, 1]

In the 1-st outer pass, the 1-st largest number (i.e. 16) will be placed to its final position.

[14, 10, 8, 7, 8, 3, 2, 4, 1, 16]

This means that we can reduce the number of inner iteration. Instead of comparing 
n
−
1
n−1 pairs for each inner iteration, we can reduce the number of inner iteration after each pass of outer iteration is done. For example, in the above example, we have 10 elements. In the first outer iteration, we have 9 comparisons in the inner iteration. In the next outer iteration, we can simply do 8 comparisons instead of 9. In the third outer iteration, we can do just 7 comparisons instead of 9, and so on.

Bubble Sort v3
We can further optimise and re-write the pseudocode as follows.

Show Pseudocode
The additional step is 3.3 which is to reduce the number of 
n
n. With this, Step 3.2 will decrease by one in the next outer iteration.

Bubble Sort v4
It can happen that more than one elements are place in their final positions in one outer iteration pass. This means that we don't have to decrease the number of inner iteration by 1 on each step of outer iteration. We can record down, at which position was the last swap, and on the next outer iteration, we can do comparison up to that last position. To illustrate this, consider the following input.

[1000, 1, 4, 7, 3, 10, 100]

In the first outer pass, we push 1000 to its final position. This means we have 
n
−
1
n−1 comparisons and swaps.

[1, 4, 7, 3, 10, 100, 1000]

In the second outer pass, we first compare the pair (1, 4), but no swap happens. Similarly with (4, 7). Now, when comparing the pair (7, 3), we do a swap to result in.

[1, 4, 3, 7, 10, 100, 1000]

When we have a swap, we will record down our position. In this case, it is at the position of the 4th element in the list, or index 3 (if our index starts from 0). Subsequently, we compare (7, 10), but no swap happens. Similarly with (10, 100). We stop at this point because the second iteration only compares up to the second last element in the above algorithm.

Now, if we follow the previous algorithm, the next outer pass will compare up to the third last element, which is 10. However, we note that the last five elements are already ordered. We know this because in the last pass, the last swap happens at (7, 3) to (3, 7) pair. In this case, we just need to run our inner iteration up to this position, i.e. 4th position, or index 3.

We can modify our pseudocode as follows.

Show Pseudocode
In the above pseudocode, we set record down the position of the element on the last swap (step 3.3.3.3), and we assign this as the new ending position for the next outer pass (step 3.4).

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

### Design of Algorithm
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

### Insertion Sort v1
Let's write it down.

Show Pseudocode

Optimised Insertion Sort
We can improve the algorithm slightly by reducing the number of assignment in the inner loop. This means that instead of swapping and assigning elements in the inner iteration, we only assign the element once it finds its final position. To do this, we store the element we are going to move into a temporary variable.

### Test Case
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
