# Graph

## Definition

* A graph is a linked list of data, where a data item is linked to other data items by a certain relationship.
* A Graph is composed with Node and Edge(direct, undirect, weighted)

----

## Types

* connected, disconnected, cycle, acyclic.

----

## Representation

* Matrix, List with **adjacency**

----

## Graph Traversal

* Depth-First Traversal(using stack), Breadth-First Traversal(using queue)

----

## Spanning Tree

A Tree is a special case of a graph. Spanning graph is obtained from a **connected** graph of N nodes via a **DFT or BFT** and **N nodes and N-1 Edges** with **no cycle** (spanning tree is not only one. there are able to make many spanning trees in one graph like below picture)

![spanningtree](https://user-images.githubusercontent.com/44596480/60176548-96208f80-9851-11e9-889c-a73a23c1e2cb.PNG)

----

### Minimum Spanning Tree

 It is obtained from a weighted connected graph of N nods with a minimum total weight

#### Algorithms

* **Prim's algorithm**
* **Kruskal's algorithm**
* Sollin's algorithm

##### Prim's algorithm

1. Start from a node of an undirected graph
2. Examine all adjacent nodes( visited)
3. pick a minimum-weight edge **avoiding cycles**

![prim](https://user-images.githubusercontent.com/44596480/60177127-0da2ee80-9853-11e9-87f4-c82328c86126.PNG)


##### Kruskal's algorithm

1. Examine all edges of an undirected graph
2. pick a minimum-weight edge avoiding cycle

There are two ways(One is start from delete most weighted edge, another is start from adding minimum weight edge )

![kruskal](https://user-images.githubusercontent.com/44596480/60177219-480c8b80-9853-11e9-978c-29021850bdb4.PNG)


#### Other algorithms..

##### Transitive closure algorithms

