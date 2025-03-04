---
layout: page
menubar: docs_menu
title: Learning materials
show_sidebar: false
toc: true
---
## Depth First Search
Depth First Search is a graph traversal algorithm that explores as far as possible along each branch before backtracking.

## Goals
By the end of this lesson, you should be able to:

explain and implement <b>depth</b> first search.
## Keywords
<b>depth first search, topological search, colour, parent vertex, start/finish time</b>
## Depth-First Search
There is another kind of search that can be done on a graph. This is called <b>depth-first</b> search (DFS). As the name implies, this algorithm explores the neighbouring vertices in a depth-wise manner. DFS is used in topological sorting, scheduling problems, cycle detection in graph and solving puzzles with only one solution such as finding a path in a maze or solving a sudoku puzzle. Let's illustrate this with the same graph as we have seen previously.
## Cases
![DFS_1](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/dfs_graph_1.jpg?raw=true)

In depth-first search, we go down the tree before moving to the next siblings. For example, as we start from A, we look into its neighbouring vertices. So vertex A has two neighbours, i.e. B and D. The depth-first search algorithm will visit one of them, say vertex B. After it visits B, it will explore one of the neighbours of B instead of visiting D. This is illustrated below.
![DFS_2](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/dfs_graph-2.jpg?raw=true)

In the figures above, every time we visit a vertex, we put a timestamp on that vertex called <b>discovery time</b>. Once we finish visiting all the neighbours of that vertex, we put another timestamp called <b>finishing time</b>. For example, vertex A has a discovery time 1 and finishing time 12 as indicated by 1/12 in the figure.

We also labelled the edges with two different kind of symbols. The solid line edges are called <b>tree edges</b>. These are edges in the depth-first forest. An edge (u, v) is a tree edge if v was first discovered by exploring edge (u, v). For example, the edge (A, B) is a tree edge since B is first discovered by exploring the edge (A, B). On the other hand the edge (A, D) is not a tree edge since D was not first discovered by exploring edge (A, D). Rather, D was first discovered by exploring the edge (C, D).

This brings us to the other kind of edges discovered by depth-first search. The dashed line edges are called <b>back edges</b>. These are those edges connected a vertex u to an ancestor v in a depth-first tree. For example, A is an ancestor of D. We can see that because we explore D through A - B - C - D. So the edge connecting D to A is a back edge since it connects D to one of its ancestor. Similarly with the edge (C, F). The depth-first forest is shown below.
![DFS_3](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/dfs_graph_3.jpg?raw=true)
## Design of Algorithm
Now we can try to write the steps to do depth-first search. We will write the steps using two functions. The first one is called DFS as shown below.
DFS
<pre>
    Input:
- G: graph
Output:
- G: graph with the following attributes marked
  - colour
  - discovery time
  - finishing time
  - parent
Steps:
1. Initialize each vertex as follows:
  1.1 set colour to white
  1.2 set parent to NILL
2. set time to 0
3. for each vertex in the graph G
  3.1 if the vertex's colour is white, do:
    3.1.1 dfs-visit(G, u)
</pre>
The above algorithm simply initialize the vertices and go through every vertex to perform the second function DFS-VISIT.

<pre>
    DFS-Visit
Input:
- G: graph
- u: vertex to visit
Output:
- G: graph with the following attributes marked
  - colour
  - discovery time
  - finishing time
  - parent
Steps:
1. increase time by 1
2. set current time to be the discovery time for u
3. set u's colour to gray
4. for each vertex in u's neighbours, do:
  4.1 if the vertex's colour is white, do:
    4.1.1 set u as the parent of the vertex
    4.1.2 call dfs-visit(G, the current vertex)
5. set u's colour to black
6. increase time by 1
7. set current time to be the finishing time
</pre>

This function simply set the discovery time for the visited vertex u and begins to visit all the neighbouring vertices of u. However, it only calls DFS-VISIT if the neighbouring vertices are white, which means these vertices have not been visited yet. Once it finishes visiting all the neighbouring vertices, it marks the vertex u to be black and set the finishing time.

## Topological Sort
One application of depth-first search algorithm is to perform a topological sort. For example, if we have list of task with dependencies, we can sort which task should be performed first. The figure below gives an example of this dependencies tasks
![DFS_4](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/topological_sort_graph_1.jpg?raw=true)
The figure above shows a directed graph of dependencies between different tasks. For example, the task wearing a pant must be done only after the task of wearing underpant and wearing a shirt. We can use the finishing time of DFS to determine the sequence of tasks.
Let's try to perform DFS for the above graph. The discovery time and the finishing time for each task is shown in the figure below.
![DFS_5](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/topological_sort_2.jpg?raw=true)

In the process of DFS, it somehow starts with "undershirt" and traverse to all the children vertices in the tree, i.e. "pants", "wallets", "belt", and then "shoes". After this, it creates another tree starting from "socks", and then another tree starting from "watch", and finally another tree starting from "underpant". The depth-first forest looks like the figure below.
![DFS_6](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/dfs_graph_4.jpg?raw=true)
We can re-order the tasks by its finishing time from the largest to the smallest as shown in the figure below.
![DFS_7](https://github.com/ADBMS620/Data-cloud02/blob/master/docs/week-4/DFS/dfs_graph_5.jpg?raw=true)

The sequence above is based on its finishing time from the largest to the smallest. The first three are independent and their sequence can be interchanged, but subsequently, "shirt" must be done only after "undershirt" task. This sequence may also depends on which vertex the search encounters first. With this in mind, we can write the topological sort steps as follows.

<pre>
    Topological-Sort
Input:
- G: graph
Output:
- list of sorted vertices
Steps:
1. call DFS(G) to compute the finishing time for each vertex in G
2. sort the vertices based on its finishing time from largest to smallest
3. return a list of sorted vertices
</pre>
