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
