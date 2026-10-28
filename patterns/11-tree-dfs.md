# 11. Tree Depth-First Search

## Use it when

- the answer depends on complete subtrees or root-to-leaf paths;
- you need depth, path sums, validation, or subtree information;
- processing children before combining their answers is natural.

DFS is like exploring every room down one hallway before returning to try another hallway.

## Core invariant

Each recursive call returns the correct answer for the subtree rooted at its node.

## Template: maximum depth

```python
def max_depth(root) -> int:
    if root is None:
        return 0

    left_depth = max_depth(root.left)
    right_depth = max_depth(root.right)

    return 1 + max(left_depth, right_depth)
```

Ask three questions:

1. What does the function return for one subtree?
2. What is the smallest base case?
3. How do child answers combine into the parent's answer?

## Complexity

`O(n)` time because every node is visited once. Recursive space is `O(h)`, where `h` is tree height.

## Practice ladder

1. Maximum Depth of Binary Tree
2. Invert Binary Tree
3. Path Sum
4. Diameter of Binary Tree

## Common failure

Writing recursion before defining what one call returns. State that meaning in a sentence first.
