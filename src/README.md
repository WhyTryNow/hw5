# graphs_jcasaus

`graphs_jcasaus` is a Python library that provides efficient implementations of core graph data structures and algorithms, specifically designed for pathfinding and graph traversal in weighted networks. Its primary feature is Dijkstra's shortest path algorithm, which computes the minimum travel cost and optimal path routing from a designated source vertex to all other reachable nodes in a graph.

## Installation

Install the package directly via `pip`:

```bash
pip install graphs-jcasaus==0.0.2

```

## Quickstart & Usage

Import `sp` (shortest path module) directly from `graphs_jcasaus` into your Python scripts:

```python
from graphs_jcasaus import sp
import sys

if __name__ == '__main__':
    # Usage: python test.py <graph_file>
    if len(sys.argv) != 2:
        print(f'Use: {sys.argv[0]} graph_file')
        sys.exit(1)

    # Build graph adjacency list from input text file
    graph = {}
    with open(sys.argv[1], 'rt') as f:
        for line in f:
            line = line.strip()
            if not line:
                continue
            s, d, w = line.split()
            s, d, w = int(s), int(d), int(w)
            if s not in graph:
                graph[s] = {}
            graph[s][d] = w

    # Compute shortest paths starting from source vertex 0
    source = 0
    dist, path = sp.dijkstra(graph, source)

    print(f'Shortest distances from source node {source}:')
    print(dist)
    for d in path:
        print(f'Shortest path to node {d}: {path[d]}')

```

## Graph File Format

Input files should represent directed edges using space-separated values formatted as `source destination weight`:

```text
0 1 4
0 7 8
1 2 8
1 7 11
2 3 7
2 8 2

```