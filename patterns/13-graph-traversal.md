# 13. Graph DFS and BFS

## Use it when

- objects are connected in an arbitrary network;
- you need reachability, components, or an unweighted shortest path;
- the input contains edges, neighbours, grids, friendships, or routes.

A graph is like a metro map: stations are nodes, and direct routes are edges.

## Core invariant

Every item in `visited` has already been discovered, so it never needs to be added again.

## Template: count connected components

```python
def count_components(graph: dict[int, list[int]]) -> int:
    visited = set()
    components = 0

    for start in graph:
        if start in visited:
            continue

        components += 1
        stack = [start]
        visited.add(start)

        while stack:
            node = stack.pop()

            for neighbor in graph[node]:
                if neighbor not in visited:
                    visited.add(neighbor)
                    stack.append(neighbor)

    return components
```

Use DFS or BFS for reachability. Prefer BFS when you need the fewest edges in an unweighted graph.

## Complexity

`O(V + E)` time and `O(V)` space, where `V` is the number of vertices and `E` the number of edges.

## Practice ladder

1. Find if Path Exists in Graph
2. Number of Provinces
3. Number of Islands
4. Shortest Path in Binary Matrix

## Common failure

Forgetting disconnected nodes. Starting from only one node explores only its connected component.
