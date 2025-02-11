---
layout: page
menubar: docs_menu
title: Installation
subtitle: Getting Started
show_sidebar: false
toc: true
---
## Heapsort
Heapsort is a comparison-based sorting algorithm that builds a binary heap data structure and repeatedly extracts the maximum element to sort a given array.
## Goals
By the end of this lesson, you should be able to:
        <li>Implement heapsort using iteration.</li>
    
## Keywords
<b>binary heap, heap property, heapify, heapsort.</b>
## Introduction
Now, we can consider Heapsort algorithm. The idea of a heapsort is pretty simple. For any arbitrary array, we can sort the integers in the array by first building a max-heap. Once the max-heap is built, we know that the maximum is at the root node. With this, we can swap the root node with the last element and then exclude it from our heap. We then should restore the max-heap property after this swap because now the root node will be a small number. We can do this repetitively until there is no more element in the heap.
## Problem Statement
Given an arbitrary array of integers, sort the element using heapsort algorithm.
        <li>Input: array of integers</li>
        <li>Output: None</li>
        <li>Process: Sort the elements of the array in place using heapsort.</li>
    
## Test Cases
   <p>Let's use the same example as in the previous section...</p>
    <pre>
[1, 2, 8, 7, 14, 9, 3, 10, 4, 16]
    </pre>
    <p>We will sort the elements following these steps:</p>
    <pre>
heap = [<b>1</b>, 14, 9, 10, 2, 8, 3, 7, 4 ,|| <b>16</b>]
    </pre>
<li>Build a max-heap from this array. The previous section has shown that the final output of building a max-heap will be:</li>
    <pre>
[16, 14, 9, 10, 2, 8, 3, 7, 4, 1]
    </pre>
<li>Now, we will swap the largest element with the last element, and exclude it from the heap. We will put the excluded element in what we called as sorted of the list. This sorted section is separated by || in the list below.</li>
    <pre>
heap = [<b>1</b>, <b>14</b>, 9, 10, 2, 8, 3, 7, 4 ,|| 16]
heap = [<b>14</b>, <b>1</b>, 9, 10, 2, 8, 3, 7, 4 ,|| 16]
heap = [14, <b>10</b>, 9, <b>1</b>, 2, 8, 3, 7, 4 ,|| 16]
heap = [14, 10, 9, <b>7</b>, 2, 8, 3, <b>1</b>, 4 ,|| 16]
        </pre>
<li>Once we have restored the max-heap property, we can take out the largest element from the first element and swap it with the last element in the heap.</li>    
<pre>
    heap = [<b>4</b>, 10, 9, 7, 2, 8, 3, 1,|| <b>14</b> , 16]
</pre>
<li>We then max-heapify the heap again to restore the max-heap property.</li>
<pre>
    heap = [<b>4</b>, <b>10</b>, 9, 7, 2, 8, 3, 1,|| <b>14</b> , 16]
    heap = [<b>10</b>, <b>4</b>, 9, 7, 2, 8, 3, 1,|| <b>14</b> , 16]
    heap = [10, <b>7</b>, 9, <b>4</b>, 2, 8, 3, 1,|| <b>14</b> , 16]
    
</pre>
<li>We then swap the largest element with the last element in the heap, and take it out from the heap.</li>
<pre>
     heap = [<b>1</b>, 7, 9, 4, 2, 8, 3,|| <b>10</b>, 14, 16]
</pre>
<li>The same process of max-heapify happens again. We will now remove the intermediate step and only show the first and the final state of the heaps.</li>

<pre>
     heap = [<b>1</b>, 7, 9, 4, 2, 8, 3,|| <b>10</b>, 14, 16]
     heap = [9, 7, 8, 4, 2, <b>1</b>, 3,|| <b>10</b>, 14, 16]
</pre>
<li>We swap and take out again the largest element. The next iteration would be:</li>
<pre>
    heap = [<b>3</b>, 7, 8, 4, 2, <b>1</b>,|| <b>9</b>, 10, 14, 16]
</pre>
then we max-heapify the array:
<pre>
    heap = [8, 7, <b>3</b>, 4, 2, 1,||<b>9</b>, 10, 14, 16]
</pre>
Swapping and taking out the largest element:
<pre>
    heap = [<b>1</b>, 7, 4, 3, 2,|| <b>8</b>, 9, 10, 14, 16]
</pre>
and max-heapify:
<pre>
    heap = [7, 4, <b>1</b>, 2,|| <b>8</b>, 9, 10, 14, 16]
</pre>
Swapping and taking out the largest element:
<pre>
    heap = [<b>2</b>, 4, 3, 1||<b>7</b>, 8, 9, 10, 14, 16]
</pre>
and max-heapify:
<pre>
    heap = [4, <b>2</b>, 3, 1||<b>7</b>, 8, 9, 10, 14, 16]
</pre>
Swapping and taking out the largest element:
<pre>
    heap = [<b>1</b>, 2, 3,|| <b>4</b>, 7, 8, 9, 10, 14, 16]
</pre>
and max-heapify:
<pre>
    heap = [3, 2, <b>1</b>,|| <b>4</b>, 7, 8, 9, 10, 14, 16]
</pre>
Swapping and taking out the largest element:
<pre>
    heap = [<b>1</b>, 2, <b>3</b>,|| 4, 7, 8, 9, 10, 14, 16]
</pre>
and max-heapify:
<pre>
    heap = [2, <b>1</b>,|| <b>3</b>, 4, 7, 8, 9, 10, 14, 16]
</pre>
Swapping and taking out the largest element:
<pre>
    heap = [<b>1</b>,|| <b>2</b>, 3, 4, 7, 8, 9, 10, 14, 16]
</pre>
<li>At this point in time, the array is already sorted. If <b>heap</b> and <b>sorted</b> are not a separate array but rather one single array, we will have:</li>
<pre>
    result=[1, 2, 3, 4, 7, 8, 9, 10, 14, 16]
</pre>

## Design of Algorithm
Let's write down the steps in the previous section in a pseudocode.
<li><b>Pseudocode</b></li>
    <pre>
def heapsort(array):
    # Input: any arbitrary array
    # Output: None
    # Steps:
    1. call build-max-heap(array)
    2. heap_end_pos = length of array - 1 # index of the last element in the heap
    3. As long as (heap_end_pos > 0), do:
        3.1 swap( array[0], array[heap_end_pos])
        3.2 heap_end_pos = heap_end_pos -1 # reduce heap size
        3.3 call max-heapify(array[from index 0 to heap_end_pos inclusive], 0)
    </pre>

We first call the procedure in the previous section called <b>build-max-heap</b> to create the max-heap data structure. We then start from the last element in the heap and swap it with the largest element (always at index 0).

We reduce the variable <b>heap_end_pos</b> to reduce the heap size and exclude the largest element from the heap.

Then, we can call <b>max-heapify</b> on a subarray. The subarray starts from index 0 of the current array up to index <b>heap_end_pos</b>. In this way, we exclude the largest element from being <b>max-heapified</b>.

The second argument of <b>max-heapify</b> is the starting node where the process should begins. In this case, we always want to start <b>max-heapify</b> from index 0 because this is the node where we replace the largest element with some small element from the end of the heap.
