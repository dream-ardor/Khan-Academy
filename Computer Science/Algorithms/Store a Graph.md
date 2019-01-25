Challenge: Store a graph

Store an adjacency matrix

We've stored a graph, with 6 vertices indexed 0-5, as an edge list in the variable edgeList.

* Store the same graph, as an adjacency matrix, in the variable adjMatrix.

* Store the same graph, as an adjacency list, in the variable adjList.


**Solution:**
```javascript
var edgeList = [ [0, 2], [1, 3], [2, 3], [2, 4], [3, 5], [4, 5] ];

var adjMatrix = [    [0, 0, 1, 0, 0, 0],
    [0, 0, 0, 1, 0, 0],
    [0, 0, 0, 1, 1, 0],
    [0, 0, 0, 0, 0, 1],
    [0, 0, 0, 0, 0, 1],
    [0, 0, 0, 0, 0, 0]
    ];

var adjList = [
    [2],
    [3],
    [3, 4],
    [5],
    [5],
    [ ]
    ];
```
