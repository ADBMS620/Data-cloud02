---
layout: page
menubar: docs_menu
title: Learning materials
show_sidebar: false
toc: true
---
## Breadth First Search
Breadth-first search is a graph traversal algorithm that explores all the vertices of a graph at the same level before moving to the next level, ensuring the shortest path to each vertex is discovered first.
## Goals
By the end of this lesson, you should be able to:
        explain and implement <b>breadth</b> first search.
## Keywords
<b>graph traversal, breadth first search, distance, colour, parent vertex, inheritance, child class, parent class, super</b>
## Introduction
In the previous lesson, we have introduced how we can represent a graph using object oriented programming. We created two classes <b>Vertex</b> and <b>Graph</b>. One main use cases with this kind of data is to do some search. For example, given the graph of MRT lines, we would like to search what is the path to take from one station to another station. We usually are interested in the shortest path. This is what Google Map and other Map application does. In this lesson, we will discuss two graph search algorithms: breadth-first search and depth-first search.
To do these algorithms, our <b>Vertex</b> class and <b>Graph</b> class may need some additional attributes to store more information as it performs the search. One way to modify our classes is to create a new class. However, we would like to introduce the concept of <b>Inheritance</b>. Inheritance allows us to re-use our existing class and create a new class that is derived from our existing class. Therefore, to implement our search algorithm, we will use inheritance to modify our existing Vertex and Graph classes.
## Breadth First Search:
Breadth first search is normally used to find a shortest path between two vertices. For example, when you plan your travel from one point to another point, breadth first search can identify the path you should take that gives the shortest path. How does this work? Let's take a look at the graph below.
## Cases


Let's say we want to find the shortest path from A to F. The way breadth-first search does is to calculate the distance of every vertex from A. So in this case, B will have a distance of 1 since it takes only one step from A to B. On the other hand, C has a distance of 2. D, however, has a distance of 1 since there is an edge from A to D connecting the two vertices directly. Vertex E has a distance 2 because from A it can go to D and then to E in two steps. Finally, F has a distance of 3. There are actually two paths from A to F. The first one is A - B - C - F and the second one is A - D - E - F. Notice that both has the same distance, which is 3.

How can we obtain all the distances for each vertex? We will start with the starting vertex which in this case is A. Next, we can look into the neighbouring vertices that A has. So in this case, A has two neighbours, i.e. B and D. We can then explore each of the neighbours. We can draw the the vertex that we are exploring as a kind of a tree.

We can then take turn to explore the neighbours of each of the children in the tree. In this case, B has two neighbours, i.e. A and C. But since we have visited A, we do not want to visit A again. So we should only visit C. This indicates that we need to mark the vertices that we have visited. Similarly, D has three children, i.e. A, C and E. But both A and C has been visited, so we should just add E into our tree. We can continue the same steps until all vertices have been visited. The final tree looks like the following.

Notice that we can actually add F either to C or to E in the tree above. In this case, we choose to add to C. The question is when do we stop? We should stop when all the vertices have been explored in terms of their children. Therefore, we need some way to indicate if a Vertex's children have been fully explored. The way we are going to do this is to colour the vertices. Moreover, we are going to use three different colours:
<p>(i)white: is used to indicate that we have not visited the vertex</p>
<p>(ii)grey: is used to indicate that we have visited the vertex but we have not completely explored all the neighbours</p>
<p>(iii)black: is when we have explored all the neighbours of this vertex.</p>

With this in mind, the image below shows the progression of the vertex exploration and how the colour of each vertex changes.

In the figures above, we use a Queue data structure to explore the vertices. When we visit vertex, we put all its neighbouring vertices into a queue. This also ensures that we explore the vertices in a <b>breadth-first</b> manner. For example, when we explore B from A, we did not go to C but rather D, which is at the same level as B in our search tree. This is where the name breadth-first search comes from. So now we are ready to write our algorithm for breadth-first search.

## Design of Algorithm
<pre>Input:
- G: Graph
- s: starting vertex
Output:
- Graph with distances on every vertex from s
Steps:
1. Initialize every vertex with the following:
  1.1 set color to white
  1.2 set distance to INF
2. start from s vertex:
  2.1 set s' color to grey
  2.2 set s' distance to 0
3. put s into the Queue
4. As long as Queue is not empty
  4.1 take out one vertex from Queue and store to u
  4.2 for each neighbour of vertex u, do:
    4.2.1 if the neighbour colour is white, do:
      4.2.1.1 set the neighbour's colour to grey
      4.2.1.2 set the neighbour's distance to u's distance + 1
      4.2.1.3 put the neighbour into the Queue
  4.3 after finish exploring all neighbours, set u's color to black
</pre>
