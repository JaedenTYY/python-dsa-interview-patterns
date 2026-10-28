# 8. Binary Search

## Use it when

- data is sorted;
- a yes/no condition changes only once;
- comparing with a candidate lets you discard half the search space.

Binary search resembles finding a word in a dictionary by repeatedly opening near the middle.

## Core invariant

If the target exists, it remains inside the inclusive range `[left, right]`.

## Exact-match template

```python
def binary_search(nums: list[int], target: int) -> int:
    left = 0
    right = len(nums) - 1

    while left <= right:
        middle = left + (right - left) // 2

        if nums[middle] == target:
            return middle
        if nums[middle] < target:
            left = middle + 1
        else:
            right = middle - 1

    return -1
```

## First-true template

```python
def first_true(left: int, right: int) -> int:
    while left < right:
        middle = left + (right - left) // 2
        if condition(middle):
            right = middle
        else:
            left = middle + 1
    return left
```

Use this second form when searching for a boundary or the smallest feasible answer.

## Complexity

`O(log n)` time and `O(1)` space for the iterative version.

## Practice ladder

1. Binary Search
2. Search Insert Position
3. First Bad Version
4. Koko Eating Bananas

## Common failure

Mixing interval rules. Choose either inclusive `[left, right]` or half-open `[left, right)` boundaries and update them consistently.
