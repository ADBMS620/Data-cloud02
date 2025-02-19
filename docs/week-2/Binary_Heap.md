---
layout: page
menubar: docs_menu
title: Learning materials
show_sidebar: false
toc: true
---

# Binary Heap
Binary heap is a complete binary tree-based data structure that satisfies the heap property,where the key of each parent node is either greater than or equal to (in a max heap) or less than or equal to (in a min heap)the keys of its child nodes.
## Goals
By the end of this lesson, you should be able to:

<li>Implement binary heap using Python's built-in list<l/i>
<li>Describe heap property<l/i>
<li>Describe the steps to build heap<l/i>
<li>Implement algorithm to restore heap property<l/i>
<li>Write functions to do binary heap data structure operation<l/i>

## Keywords 
<b> tree, binary tree, root, binary heap, heap property, heapify, node, leaf, parent node, child node<b>

# Introduction
Previously, we discussed two sorting algorithms called Bubble Sort and Insertion Sort. In this section we will apply our programming skills to investigate another sorting algorithm called the Heapsort. We will then compare the performance of Heapsort with the previous sorting algorithms. We will discuss some notations on how to analyze these performance.

<div style="border-left: 4px solid #4CAF50; background-color: #E8F5E9; padding: 1em;">
  <h3>WHY SO MANY SORTING ALGORITHMS?</h3>
  <p>
    One reason why we introduce different sorting algorithms is to
    show you that there are many ways to solve the same problems.
    At the same time, these different ways may have different
    performances.After we introduce binary heap and heapsort algorithm, we will
    begin to teach you how to analyze these different algorithms in
    terms of computation time. You will notice that the Heapsort
    algorithm is a much better sorting algorithm compared to Bubble
    sort and Insertion sort.
  </p>
</div>

# Binary Heap
Before discussing the Heapsort algorithm, we have to introduce a new data structure called binary heap or simply called heap.
<div style="border-left: 4px solid #0288d1; background-color: #e1f5fe; padding: 1em;">
  <strong>❗ HEAP</strong>
  <p>
    The heap is an array of objects that we can view as a 
    nearly perfect binary tree (or we can call it a 
    <em>complete</em> binary tree).
  </p>
</div>

> A perfect binary tree is a full binary tree in which **all** leaf nodes are at the same level.
> Complete binary trees are nearly perfect **except** the last level, and all the leaves at the last level are packed towards the left.


You are familiar with the concept of array. But what is a binary tree? The easiest way to explain it is using some examples.The image below shows you an array of integers.
![](docs/week-2/Binary_Heap1.png)

## Binary Tree
We have indicated the indices of each element in the array, which starts from 0. We can visualize the elements in this array in a form of a tree as shown below.


A tree in computer science is up-side down. It consists of nodes and it has one root node, which is at the top. In a binary tree, each node has only two children, which we will call the left child and the right child. Every node, except the root, has a parent node. The node without children is what we called a leaf.

Let's take a look at the example above and put in all the terms we have mentioned:
* In the above tree, we have 10 nodes, where each node is each element in the array.
* The root node is the element 16, which has an index 0 in the array.
* Node with element 16 (root node) has two children. The left child is a node with the element 14, while the right child is a node with the element 10.
* Elements 9, 3, 2, 4, and 1 are all leaves because they do not have any children.
* The node with element 7 (index 4) has only one child, which is the node with element 1 (index 9).
* The node with element 1 (index 9) has node with index 4 as its parent.

  Now, let's go back to our definition of a heap. The heap is an array of object that we can view as a nearly perfect binary tree.

* A binary tree is a tree where all the nodes have only a maximum of two children, which you can call left child and right child.
* A full binary tree is a tree where all the nodes except the leaves have two children. In our case, heap is a complete binary tree and not a full binary tree. A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible. A complete binary tree is similar to a full binary tree with two major differences: all the leaf elements must lean toward the left and the last leaf element may not have the right sibling.
* The root of the tree is the node with index 0.
* We put the elements of our array into our tree from top to bottom and left to right sequence. With this, we can calculate the index of the children and the parent for every node.

## Indices of Children and Parent in a Heap
Let's start by considering how to calculate the index of the parent node. Let's take a look at the example tree we have considered.

> ⚠ **INDEX ≠ NODE CONTENT**
>  The parent of node index 1 is 0. Similarly, the parent  of node index 2 is also 0. The parent of node index 3  and 4 is 1, while the parent of node index 5 and 6 is 2.

How do we get index 0 from both indices 1 and 2? And how do we get index 1 from indices 3 and 4? 
Or index 2 from indices 5 and 6?

We can test the above pseudocode. **(1−1)/2=0** and **(2−1)/2=0** for the second level nodes. Similarly, **(3−1)/2=1 and (4−1)/2=1** for the third-level nodes with the parent index **1**. And **(5−1)/2=2** together with **(6−1)/2=2** for the third level nodes with the parent index 2. Note that we use integer division to get the correct parent node.

## Left Child Index
n order to get the index of the left child, let's observe the following:
* The left child of node 0 is index 1.
* The left child of node 1 is index 3.
* The left child of node 2 is index 5.
* and so on.

We can get the left child index using the following:



## Right Child Index
Similarly, we can observe the following for the indices of the right child nodes:

* The right child of node 0 is index 2.
* The right child of node 1 is index 4.
* The right child of node 2 is index 6.
* and so on.


# Heap Property
There are two kinds of heap: max-heaps and min-heaps. In this case we will discuss only max-heaps. Both heaps must satisfy **heap property**, which specifies the kind of heap we are dealing with. The **max-heap property** is specified as follows:

> ### MAX HEAP PROPERTY
> For all nodes except the root:
>
> ```text
> A[parent(i)] >= A[i]
> ```

This means that in a max-heap, the parent nodes are always greater that their children. This also implies that the largest node is at the root. The figure below is an example of a max-heap because it satisfies the condition above.

# Maintaining The Heap Property with `Heapify`

We will now describe an algorithm on how to maintain the *heap property*, 
and in this example it is the **max-heap property**. We call the procedure 
to maintain the max-heap property **max-heapify**. The idea is that for a 
given node, we will “push down” this node in such a way that the 
max-heap property is satisfied. This assumes the *left child* of the given 
node already forms a tree that satisfies the max-heap property. Similarly, 
the *right child* of the given node also forms a tree that satisfies the 
max-heap property. The only part that does not satisfy the max-heap 
property is the current node and its two children.

## (P)roblem Statement

Given an index of a node in a binary tree, where the left and the right children 
of that node satisfy the *max-heap property*, restore the *max-heap property* 
of the tree starting from the current node.

```text
Input: index of the current node in a heap
Output: None
Process: re-order the elements in the heap
         in such a way that the max-heap property is satisfied
         from the current index node.

assumption:
 - left child forms a tree that satisfies max-heap property
 - right child forms a tree that satisfies max-heap property
 - current node with its children may not satisfy max-heap property
```
## Test (C)ase

Let's take a look at the tree below.

Note the following:

- The current node is **index 1**, which has the element of 4.
- The current node with its children does not satisfy the *max-heap property* 
  because `4 < 14` and `4 < 7`.
- The left child, i.e. the tree starting from index 3 (element 14, with children 
  of 2 and 8), forms a tree that satisfies the *max-heap property*.
- The right child, i.e. the tree starting from index 4 (element 7, with 
  one child of 1), forms a tree that satisfies the *max-heap property*.

The procedure of *max-heapify* will push the current node by swapping with the 
largest node along the way to satisfy the *max-heap property*. To do that, in 
the process of pushing the nodes, we will swap that node with the **largest child**. 
In this way, we satisfy the *max-heap property*.

Let's look at the particular example above. Given the tree above, we do the following:

- We first find the largest child of the current node. The current node is element 4 
  (index 1). The largest child is element 14 (index 3), which is the left child of 
  the current node.




