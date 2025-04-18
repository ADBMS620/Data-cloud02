---
layout: page
menubar: docs_menu
title: Learning Materials
show_sidebar: false
toc: true
---
# Floyd Warshall Alogrithm
The Floyd Warshall Algorithm is an all-pair shortest path algorithm that uses Dynamic Programming to find the shortest distances between every pair of vertices in agraph,unlike Dijkstra and Bellman-Ford which are single source shortest path algorithms. This algorithm works for both the directed and undirected weighted graphs and can handle graphs with both positive and negative weight edges.
### Note:
It does not work for the graphs with negative cycles (where the sum of the edges in a cycle is negative).
### Idea Behind Floyd Warshall Algorithm:
Suppose we have a graph graph[][] with V vertices from 0to V-1. Now we have to evaluate a dist[][] where dist[i][j] represents the shortest path between vertex i to j.
Let us assume that vertices i to j have intermediate nodes. The idea behind Floyd Warshall algorithm is to treat each and every vertex k from 0 to V-1 as an intermediate node one by one.
When we consider the vertex k, we must have considered vertices from 0 to k-1 already. So we use the shortest paths built by previous vertices to build shorter
paths with vertex k included.

The following figure shows the above optimal substructure property in Floyd Warshall algorithm:

![image](https://github.com/user-attachments/assets/796e009e-6081-4b58-9388-a6e9229e8d24)
## Algorithm
Initialize the solution matrix same as the input graph matrix as a first step. 
Then update the solution matrix by considering all vertices as an intermediate vertex. 
The idea is to pick all vertices one by one and updates all shortest paths which include the picked vertex as an intermediate vertex in the shortest path. 
When we pick vertex number k as an intermediate vertex, we already have considered vertices {0, 1, 2, .. k-1} as intermediate vertices. 
For every pair (i, j) of the source and destination vertices respectively, there are two possible cases. 
k is not an intermediate vertex in shortest path from i to j. We keep the value of dist[i][j] as it is. 
k is an intermediate vertex in shortest path from i to j. We update the value of dist[i][j] as dist[i][k] + dist[k][j], if dist[i][j] > dist[i][k] + dist[k][j] 
![image](https://github.com/user-attachments/assets/aafcd3d8-7015-4a89-842d-08a21a207478)

### Why Floyd Warshall Works (Correctness Proof)?
The algorithm relies on the principle of optimal substructure, meaning:

- If the shortest path from i to j passes through some vertex k, then the path from i to k and the path from k to j must also be shortest paths.
- The iterative approach ensures that by the time vertex k is considered, all shortest paths using only vertices 0 to k-1 have already been computed.
By the end of the algorithm, all shortest paths are computed optimally because each possible intermediate vertex has been considered.

### Why Floyd-Warshall Algorithm better for Dense Graphs and not for Sparse Graphs?
Dense Graph: A graph in which the number of edges are significantly much higher than the number of vertices.
Sparse Graph: A graph in which the number of edges are very much low.

No matter how many edges are there in the graph the Floyd Warshall Algorithm runs for O(V3) times therefore it is best suited for Dense graphs. 
In the case of sparse graphs, Johnson’s Algorithm is more suitable. 

### Real World Applications of Floyd-Warshall Algorithm
In computer networking, the algorithm can be used to find the shortest path between all pairs of nodes in a network. This is termed as network routing.
Flight Connectivity In the aviation industry to find the shortest path between the airports.
GIS(Geographic Information Systems) applications often involve analyzing spatial data, such as road networks, to find the shortest paths between locations.
Kleene’s algorithm which is a generalization of floyd warshall, can be used to find regular expression for a regular language.

