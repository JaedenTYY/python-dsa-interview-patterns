# 14. Topological Sort

## Use it when

- tasks have prerequisites;
- dependencies are directed;
- you need a valid order or must detect an impossible cycle.

Think of getting dressed: socks must come before shoes, but unrelated items can be ordered flexibly.

## Core invariant

The queue contains exactly the unfinished nodes with no remaining prerequisites.

## Kahn's algorithm template

```python
from collections import deque

def topological_order(n: int, edges: list[list[int]]) -> list[int]:
    graph = [[] for _ in range(n)]
    indegree = [0] * n

    for before, after in edges:
        graph[before].append(after)
        indegree[after] += 1

    queue = deque(
        node for node in range(n) if indegree[node] == 0
    )
    order = []

    while queue:
        node = queue.popleft()
        order.append(node)

        for neighbor in graph[node]:
            indegree[neighbor] -= 1
            if indegree[neighbor] == 0:
                queue.append(neighbor)

    return order if len(order) == n else []
```

If fewer than `n` nodes are processed, a directed cycle prevents the remaining indegrees from reaching zero.

## Complexity

`O(V + E)` time and `O(V + E)` space.

## Practice ladder

1. Find the Town Judge
2. Course Schedule
3. Course Schedule II
4. Minimum Height Trees

## Common failure

Reversing prerequisite edges. Decide whether `[a, b]` means `a → b` or `b → a` before building the graph.
