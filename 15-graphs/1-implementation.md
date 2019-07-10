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
}
