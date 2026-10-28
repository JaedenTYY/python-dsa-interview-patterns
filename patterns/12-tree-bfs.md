# 12. Tree Breadth-First Search

## Use it when

- the problem mentions levels, rows, or nearest depth;
- nodes must be grouped by distance from the root;
- the first matching level is enough.

BFS is like checking every room on one floor before taking the stairs to the next floor.

## Core invariant

At the beginning of each outer loop, the queue starts with exactly the nodes on the current level.

## Template

```python
from collections import deque

def level_order(root) -> list[list[int]]:
    if root is None:
        return []

    levels = []
    queue = deque([root])

    while queue:
        level = []
        level_size = len(queue)

        for _ in range(level_size):
            node = queue.popleft()
            level.append(node.val)

            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)

        levels.append(level)

    return levels
```

## Complexity

`O(n)` time and `O(w)` auxiliary space, where `w` is the tree's maximum width. The returned output may also use `O(n)` space.

## Practice ladder

1. Binary Tree Level Order Traversal
2. Average of Levels in Binary Tree
3. Minimum Depth of Binary Tree
4. Binary Tree Right Side View

## Common failure

Calling `len(queue)` repeatedly inside the level loop. Save it first so children are processed on the next level.
