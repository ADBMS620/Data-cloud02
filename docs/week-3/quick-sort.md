---
layout: page
menubar: docs_menu
title: Learning materials
show_sidebar: false
toc: true
---
## Quick Sort
QuickSort is a sorting algorithm based on the Divide and Conquer that picks an element as a pivot and partitions the given array around the picked pivot by placing the pivot in its correct position in the sorted array.
## Goals
The primary goal of the quicksort algorithm is to efficiently sort an array or list of elements by using a divide-and-conquer approach, partitioning the array around a <b>pivot</b> element and recursively sorting the resulting sub-arrays.
## Keywords
<b>Pivot,Divide and Conquer, Partition the Array, Recurssion.</b>
## Introduction
Quicksort is a <b>divide-and-conquer</b> algorithm. It works by selecting a <b>pivot</b> element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. For this reason, it is sometimes called partition-exchange sort. The sub-arrays are then sorted recursively. This can be done in-place, requiring small additional amounts of memory to perform the sorting.
## Quick Sort
As the name suggests, Quicksort is one of the fastest sorting algorithms.
The Quicksort algorithm takes an array of values, chooses one of the values as the 'pivot' element, and moves the other values so that lower values are on the left of the pivot element, and higher values are on the right of it.
The Quicksort algorithm does the same operation recursively on the sub-arrays to the left and right side of the pivot element. This continues until the array is sorted.
<b>Recursion</b> is when a function calls itself.
After the Quicksort algorithm has put the pivot element in between a sub-array with lower values on the left side, and a sub-array with higher values on the right side, the algorithm calls itself twice, so that Quicksort runs again for the sub-array on the left side, and for the sub-array on the right side. The Quicksort algorithm continues to call itself until the sub-arrays are too small to be sorted.
## QuickSort Algorithm
QuickSort works on the principle of divide and conquer, breaking down the problem into smaller sub-problems.

There are mainly four steps in the algorithm:

<p>1.<b>Choose a Pivot:</b> Select an element from the array as the pivot. The choice of pivot can vary (e.g., first element, last element, random element, or median).</p>
<p>2.<b>Partition the Array:</b> Rearrange the array around the pivot. After partitioning, all elements smaller than the pivot will be on its left, and all elements greater than the pivot will be on its right. The pivot is then in its correct position, and we obtain the index of the pivot.</p>
<p>3.<b>Recursively Call:</b> Recursively apply the same process to the two partitioned sub-arrays (left and right of the pivot).</p>
<p>4.<b>Base Case:</b> The recursion stops when there is only one element left in the sub-array, as a single element is already sorted.</p>

## Choice of Pivot
There are many different choices for picking pivots.

<p><b>Always pick the first (or last) element as a pivot.</b> The below implementation picks the last element as pivot. The problem with this approach is it ends up in the worst case when array is already sorted.</p>
<b>Pick a random element as a pivot.</b> This is a preferred approach because it does not have a pattern for which the worst case happens.
Pick the median element is pivot. This is an ideal approach in terms of time complexity as we can find <b>median in linear time</b> and the partition function will always divide the input array into two halves. But it takes more time on average as median finding has high constants.

## Partition Algorithm
The key process in quickSort is a partition. There are three common algorithms to partition. All these algorithms have O(n) time complexity.

<p><b>Naive Partition:</b> Here we create copy of the array. First put all smaller elements and then all greater. Finally we copy the temporary array back to original array. This requires O(n) extra space.</p>
<p><b>Lomuto Partition:</b> We have used this partition in this article. This is a simple algorithm, we keep track of index of smaller elements and keep swapping. We have used it here in this article because of its simplicity.</p>
<p><b>Hoare’s Partition:</b> This is the fastest of all. Here we traverse array from both sides and keep swapping greater element on left with smaller on right while the array is not partitioned. Please refer Hoare’s vs Lomuto for details.</p>
