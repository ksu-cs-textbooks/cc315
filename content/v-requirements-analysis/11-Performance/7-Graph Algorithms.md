---
title: "Graph Algorithms"
weight: 35
pre: "7. "
---

Path Searches
---

``` tex
1. function DEPTHFIRSTSEARCH(GRAPH,SRC,TAR)
2.     STACK = empty array
3.     DISCOVERED = empty set
4.     PARENT_MAP = empty dictionary
5.     append SRC to STACK
6.     while STACK is not empty
7.         CURR = top of the stack
8.         if CURR not in DISCOVERED
9.             if CURR is TAR
10.                 PATH = empty array
11.                 TRACE = TAR
12.                 while TRACE is not SRC
13.                     append TRACE to PATH
14.                     set TRACE equal to PARENT_MAP[TRACE]
15.                 reverse the order of PATH
16.                 return PATH
17.            add CURR to DISCOVERED
18.            NEIGHS = neighbors of CURR
19.            for EDGE in NEIGHS
20.                NODE = first entry in EDGE
21.                append NODE to STACK
22.                if PARENT_MAP does not have key NODE
23.                    in the PARENT_MAP dictionary set key NODE with value CURR
24.    return nothing
```
- **Time**: The time analysis for the depth first search can be a bit complex. Lines 1 through 5 would execute in near constant time. When we start the while loop on line 6, it is more difficult to analyze how many times this can execute as `STACK` can contain duplicates. In the case that we have a sparse graph, this would be bound by the number of nodes. For a dense graph however, the number of executions would be bound by the number of edges. The code within the while loop would be bound by the number of nodes because of the check that we have not already discovered the node in line 8. If we haven't discovered it, we would take either the logic of lines 8 through 16 or lines 17 through 23 but never both in the same iteration. Both of these blocks are bound by the number of nodes in our graph. Thus the worst case time requirement would be $n^2$.
- **Space**: Depending on the density of our graph, the space required will be linear with respect to the number of nodes or edges. This is due to the fact that `STACK` can contain duplicate nodes. If we have a sparse graph then it will be bound by the number of nodes. If we have a dense graph then the space is bound by the number of edges.
    - `STACK`: linear with respect to the number of edges
    - `DISCOVERED`: linear with respect to the number of nodes
    - `PARENT_MAP`: linear with respect to the number of nodes
    - `CURR`: 1
    - `PATH`: linear with respect to the number of nodes
    - `TRACE`: 1
    - `NEIGHS`: linear with respect to the number of neighbors
    - `EDGE`: 1
    - `NODE`: 1
    

``` tex
1. function BREADTHFIRSTSEARCH(GRAPH,SRC,TAR)
2.     QUEUE = empty queue
3.     DISCOVERED = empty set
4.     PARENT_MAP = empty dictionary
5.     add SRC to DISCOVERED
6.     add SRC to QUEUE
7.     while QUEUE is not empty
8.         CURR = first element in QUEUE
9.         if CURR is TAR 
10.            PATH = empty list 
11.            TRACE = TAR
12.            while TRACE is not SRC
13.                    append TRACE to PATH
14.                    set TRACE equal to PARENT_MAP[TRACE]
15.                reverse the order of PATH
16.                return PATH
17.        NEIGHS = neighbors of CURR
18.        for EDGE in NEIGHS
19.            NODE = first entry in EDGE
20.            if NODE is not in DISCOVERED
21.                add NODE to DISCOVERED
22.                if PARENT_MAP does not have key NODE
23.                    in the PARENT_MAP dictionary set key NODE with value CURR
24.                append NODE to QUEUE
25.    return nothing
```
- **Time**: The run time expected for breadth first search is a bit more straight forward as `QUEUE` will never have duplicates. Lines 1 through 6 will all execute in constant time. The while loop will occur $n$ times where $n$ is the number of nodes. Based on the logic, either 9-16 will execute or 17-24 will execute. Both of these are bound by the number of nodes in terms of time. Each iteration of the while loop will take $n$ time and we do the while loop $n$ times; thus the running time will be $n^2$.
- **Space**: The space required for BFS will be linear with respect to the number of nodes. We have 5 variables which have size bound by the number of nodes. If the number of nodes doubles, then we expect the amount of space to roughly double. 
    - `QUEUE`: linear with respect to the number of nodes
    - `DISCOVERED`: linear with respect to the number of nodes
    - `PARENT_MAP`: linear with respect to the number of nodes
    - `CURR`: 1
    - `PATH`: linear with respect to the number of nodes
    - `TRACE`: 1
    - `NEIGHS`: linear with respect to the number of nodes
    - `EDGE`: 1
    - `NODE`: 1

MSTs
---

``` tex
1. function KRUSKAL(GRAPH)
2.     MST = GRAPH without the edges attribute(s)
3.     ALLSETS = an empty list which will contain the sets
4.     for NODE in GRAPH NODES
5.         SET = a set with element NODE
6.         add SET to ALLSETS
7.     EDGES = list of GRAPH's edges
8.     SORTEDEDGES = EDGES sorted by edge weight, smallest to largest
9.     for EDGE in SORTEDEDGES
10.        SRC = source node of EDGE
11.        TAR = target node of EDGE
12.        SRCSET = the set from SETS in which SRC is contained
13.        TARSET = the set form SETS in which TAR is contained
14.        if SRCSET not equal TARSET
15.            UNIONSET = SRCSET union TARSET
16.            add UNIONSET to ALLSETS
17.            remove SRCSET from ALLSETS
18.            remove TARSET from ALLSETS
19.            add EDGE to MST as undirected edge
20.    return MST
```
- **Time**: The time to initialize `MST` would be linear with respect to the number of nodes. Regardless of the graph implementation, inserting nodes is constant time and we would do it for the number of nodes in `GRAPH`. Lines 4-6 would take linear time with respect to the number of nodes. Then lines 9-19 would take linear time with respect to the number of edges as it would execute $e$ times and each operation can be done in constant time, except for searching through the sets and performing set operations, which require $log_2(n)$ time. Thus, Kruskal's algorithm will take time on the order of $e \times log_2(n)$ in the worst case. 

- **Space**:The required space for Kruskal's algorithm is dependent on the implementation of the MST. A matrix graph would require $n^2$ space and a list graph we would require $n+e$ space.
    - `MST`: matrix graph $n^2$ or list graph $n+e$
    - `ALLSETS`: linear with respect to the number of nodes
    - `NODE`: 1
    - `GRAPH NODES`: linear with respect to the number of nodes
    - `SET`: 1
    - `EDGES`: linear with respect to the number of edges
    - `SORTEDEDGES`: linear with respect to the number of edges
    - `SRC`: 1
    - `TAR`: 1
    - `SRCSET`: 1
    - `TARSET`: 1
    - `UNIONSET`: 1

``` tex
1. function PRIM(GRAPH, START)
2.     MST = GRAPH without the edges attribute(s)
3.     VISITED = empty set
4.     add START to VISITED
5.     AVAILEDGES = list of edges where START is the source
6.     sort AVAILEDGES
7.     while VISITED is not all of the nodes
8.         SMLEDGE = smallest edge in AVAILEDGES
9.         SRC = source of SMLEDGE
10.        TAR = target of SMLEDGE
11.        if TAR not in VISITED
12.            add SMLEDGE to MST as undirected edge
13.            add TAR to VISITED
14.            add the edges where TAR is the source to AVAILEDGES
15.        remove SMLEDGE from AVAILEDGES
16.        sort AVAILEDGES
17.    return MST
```
- **Time without Priority Queue**: The time to initialize `MST` would be linear with respect to the number of nodes. Regardless of the graph implementation, inserting nodes is constant time and we would do it for the number of nodes in `GRAPH`. With a matrix graph, setting up `AVAILEDGES` would take linear time with respect to the number of nodes. With a list graph, this would happen in constant time. Then, we need to get the smallest edge from the `AVAILEDGES` list, which would be a linear time operation based on the number of edges, and we must do that once for up to each edge in the graph. So, the worst case running time for Prim's algorithm is $e^2$. (Our implementation is actually a bit slower than this since we sort the list of available edges each time, but that is technically not necessary - our implementation is closer to $e^2 \times log_2(e)$!)
- **Time with Priority Queue**: We do get an improvement when we choose to implement this with a priority queue. For the most part, the performance is the same. Using a priority queue, heapify would optimize the sorting to happen in linear time with respect to the number of elements. In that case, we can reduce the total running time to on the order of $e \times log_2(n)$, which is the same as Kruskal's algorithm. 
- **Space**: The required space for Prim's algorithm is also dependent on the implementation of the MST. A matrix graph would require $n^2$ space and a list graph we would require $n+e$ space. 
    - `MST`: matrix graph $n^2$ or list graph $n+e$
    - `VISITED`: linear with respect to the number of nodes
    - `AVAILEDGES`: linear with respect to the number of edges
    - `SMLEDGE`: 1
    - `SRC`: 1
    - `TAR`: 1


Shortest Path
---

``` tex
1. DIJKSTRAS(GRAPH, SRC)
2.    SIZE = size of GRAPH
3.    DISTS = array with length equal to SIZE
4.    PREVIOUS = array with length equal to SIZE
5.    set all of the entries in PREVIOUS to none
6.    set all of the entries in DISTS to infinity 

7.    DISTS[SRC] = 0 
8.    PQ = min-priority queue

9.    loop IDX starting at 0 up to SIZE
10.        insert (DISTS[IDX],IDX) into PQ

11.    while PQ is not empty
12.        MIN = REMOVE-MIN from PQ
13.        for NODE in neighbors of MIN
14.            WEIGHT = graph weight between MIN and NODE
15.            CALC = DISTS[MIN] + WEIGHT
16.            if CALC < DISTS[NODE]
17.                DISTS[NODE] = CALC
18.                PREVIOUS[NODE] = MIN
19.                PQIDX = index of NODE in PQ
20.                PQ decrease-key (PQIDX, CALC)
21.    return DISTS and PREVIOUS
```
- **Time**: The time required for Dijkstra's algorithm will be $n^2$ in the worst case. We would expect lines 1 through 8 to take constant time. The for loop on line 9 would be bound by the number of nodes. We would expect the for loop on line 13 to be bound by the number of nodes. This for loop will execute each time `PQ` is not empty (line 11), which is bound by the number of nodes. Thus, the block of code starting at 11 will take $n^2$ time to run in the worst case. This means that if we double the number of nodes, then the running time will be quadrupled. The worst case for Dijkstra's algorithm is characterized by being a very dense graph, meaning each node has a lot of neighbors. If the graph is sparse and our priority queue is efficient, we could expect this running time to be more along the lines of $(n + e) \times log_2(n)$, where $e$ is the number of edges. 
- **Space**: The required space for Dijkstra's algorithm will be linear with respect to the number of nodes. We have 4 variables which have linear size with respect to the number of nodes. We say that this is linear because if we were to double the number of nodes, we would roughly double the space requirement. 
    - `SIZE`: 1
    - `DISTS`: linear with respect to the number of nodes
    - `PREVIOUS`: linear with respect to the number of nodes
    - `PQ`: linear with respect to the number of nodes
    - `IDX`: 1
    - `MIN`: 1
    - `NODE`: 1
    - `NEIGHBORS`: linear with respect to the number of nodes
    - `WEIGHT`: 1
    - `CALC`: 1
    - `PQIDX`: 1
