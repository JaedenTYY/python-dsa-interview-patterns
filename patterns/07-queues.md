# 7. Queue and Level Processing

## Use it when

- items must be handled in arrival order;
- a problem says “level by level” or “nearest first”;
- newly discovered work belongs behind existing work.

A queue is like a checkout line: the first person to enter is the first served.

## Core invariant

The queue contains discovered items that have not yet been processed, in the order they should be processed.

## Python template

```python
from collections import deque

def process(start):
    queue = deque([start])

    while queue:
        current = queue.popleft()

        for next_item in get_neighbors(current):
            queue.append(next_item)
```

Use `append()` to add at the back and `popleft()` to remove from the front. A Python list's `pop(0)` is slower because all remaining elements shift left.

## Level boundary template

```python
while queue:
    level_size = len(queue)

    for _ in range(level_size):
        node = queue.popleft()
        # Process only nodes from this level.
```

Save `level_size` before adding children. Otherwise, the current level and next level become mixed.

## Complexity

Queue operations are `O(1)`. A traversal is usually `O(V + E)` for vertices and edges, with `O(V)` space.

## Practice ladder

1. Number of Recent Calls
2. Binary Tree Level Order Traversal
3. Rotting Oranges
4. Open the Lock

## Common failure

Marking an item as visited only when removing it. Mark it when adding it, or the same item may enter the queue many times.
