# 15. Union-Find

## Use it when

- groups are repeatedly joined;
- you need to ask whether two items are connected;
- edges arrive dynamically;
- a new edge may create a cycle.

Union-find is like merging friend groups and appointing one representative for each group.

## Core invariant

Two items are connected exactly when `find()` returns the same representative for both.

## Template

```python
class UnionFind:
    def __init__(self, size: int):
        self.parent = list(range(size))
        self.rank = [0] * size

    def find(self, node: int) -> int:
        if self.parent[node] != node:
            self.parent[node] = self.find(self.parent[node])
        return self.parent[node]

    def union(self, first: int, second: int) -> bool:
        root_first = self.find(first)
        root_second = self.find(second)

        if root_first == root_second:
            return False

        if self.rank[root_first] < self.rank[root_second]:
            root_first, root_second = root_second, root_first

        self.parent[root_second] = root_first

        if self.rank[root_first] == self.rank[root_second]:
            self.rank[root_first] += 1

        return True
```

Path compression shortens future searches. Union by rank avoids building tall trees.

## Complexity

Each operation is effectively `O(1)` amortized for interview-sized inputs; formally it is `O(α(n))`, where `α` grows extraordinarily slowly. Space is `O(n)`.

## Practice ladder

1. Number of Provinces
2. Redundant Connection
3. Accounts Merge
4. Number of Operations to Make Network Connected

## Common failure

Comparing direct parents rather than representatives. Always call `find()` before deciding whether two items share a group.
