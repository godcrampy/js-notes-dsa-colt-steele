# Graph Implementation

```javascript
class Graph {
    constructor() {
        this.adjacencyList = {};
    }
    addVertex(vertex) {
        if (!this.adjacencyList[vertex])
            this.adjacencyList[vertex] = [];
    }
    addEdge(vertex1, vertex2) {
        if (!this.adjacencyList[vertex1].includes(vertex2))
            this.adjacencyList[vertex1].push(vertex2);
        if (!this.adjacencyList[vertex2].includes(vertex1))
            this.adjacencyList[vertex2].push(vertex1);
    }
    removeEdge(vertex1, vertex2) {
        this.adjacencyList[vertex1] = this.adjacencyList[vertex1].filter((value) => value != vertex2);
        this.adjacencyList[vertex2] = this.adjacencyList[vertex2].filter((value) => value != vertex1);
    }
    deleteVertex(vertex) {
        let vertices = [...this.adjacencyList[vertex]];
        for (let vertexIndex in vertices) {
            // Remove vertex from corresponding vertex array
            let otherVertex = vertices[vertexIndex];
            this.adjacencyList[otherVertex] = this.adjacencyList[otherVertex].filter((value) => value != vertex);
            // delete vertex itself
            delete this.adjacencyList[vertex];
        }
    }
    DFS(vertex) {
        let visited = {};
        let result = [];
        const adjacencyList = this.adjacencyList;

        function searchDepthFirst(vertex) {
            if (!vertex) return null;
            visited[vertex] = true;
            result.push(vertex);
            adjacencyList[vertex].forEach(function (nextVertex) {
                if (!visited[nextVertex])
                    return searchDepthFirst(nextVertex);
            })
        }
        searchDepthFirst(vertex)
        return result;
    }
    BFS(vertex) {
        let visited = {};
        let result = [];
        let queue = [vertex];
        visited[vertex] = true;
        let currentVertex;
        while (queue.length) {
            currentVertex = queue.shift;
            result.push(currentVertex);

            this.adjacencyList[currentVertex].forEach((nextVertex) => {
                if (!visited[nextVertex]) {
                    visited[nextVertex] = true;
                    queue.push(neighbor);
                }
            });
        }
        return result;
    }
}
```