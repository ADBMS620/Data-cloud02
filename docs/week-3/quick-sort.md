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
<p><b>Hoare’s Partition:</b> This is the fastest of all. Here we traverse array from both sides and keep swapping greater element on left with smaller on right while the array is not partitioned.</p>

## Example
Let's consider an example of a short array and try to understand the algorithm:

<b>Step 1:</b> We start with an unsorted array.
<pre>
[ 11, 9, 12, 7, 3]
</pre>
<b>Step 2:</b> We choose the last value 3 as the pivot element.
<pre>
[ 11, 9, 12, 7, <b>3</b>]
</pre>
<b>Step 3:</b> The rest of the values in the array are all greater than 3, and must be on the right side of 3. Swap 3 with 11.
<pre>
[<b>3</b>, 9, 12, 7, <b>11</b>]
</pre>
<b>Step 4:</b> Value 3 is now in the correct position. We need to sort the values to the right of 3. We choose the last value 11 as the new pivot element.
<pre>
[ 3, 9, 12, 7, <b>11</b>]
</pre>
<b>Step 5:</b> The value 7 must be to the left of pivot value 11, and 12 must be to the right of it. Move 7 and 12.
<pre>
[ 3, 9, <b>7</b>, <b>12</b>, 11]
</pre>
<b>Step 6:</b> Swap 11 with 12 so that lower values 9 and 7 are on the left side of 11, and 12 is on the right side.
<pre>
[ 3, 9, 7, <b>11</b>, <b>12</b>]
</pre>
<b>Step 7:</b> 11 and 12 are in the correct positions. We choose 7 as the pivot element in sub-array [ 9, 7], to the left of 11.
<pre>
[ 3, 9, <b>7</b>, 11, 12]
</pre>
<b>Step 8:</b> We must swap 9 with 7.
<pre>
[ 3, <b>7</b>, <b>9</b>, 11, 12].
</pre>
And now, the array is sorted.

## Advantages of Quick Sort
1.It is a divide-and-conquer algorithm that makes it easier to solve problems.

2.It is efficient on large data sets.

3.It has a low overhead, as it only requires a small amount of memory to function.

4.It is Cache Friendly as we work on the same array to sort and do not copy data to any auxiliary array.

5.Fastest general purpose algorithm for large data when stability is not required.

6.It is tail recursive and hence all the tail call optimization can be done.
## Disadvantages of Quick Sort
1.It has a worst-case time complexity of O(n2), which occurs when the pivot is chosen poorly.

2.It is not a good choice for small data sets.

3.It is not a stable sort, meaning that if two elements have the same key, their relative order will not be preserved in the sorted output in case of quick sort, because here we are swapping elements according to the pivot’s position (without considering their original positions).
## Applications of Quick Sort
1.Efficient for sorting large datasets with O(n log n) average-case time complexity.

2.Used in partitioning problems like finding the kth smallest element or dividing arrays by pivot.

3.Integral to randomized algorithms, offering better performance than deterministic approaches.

4.Applied in cryptography for generating random permutations and unpredictable encryption keys.

5.Partitioning step can be parallelized for improved performance in multi-core or distributed systems.

6.Important in theoretical computer science for analyzing average-case complexity and developing new techniques.
