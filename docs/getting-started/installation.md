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

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr


