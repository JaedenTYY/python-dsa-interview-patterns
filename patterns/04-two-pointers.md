# 04 — Two Pointers

## Use it when

- a sorted sequence lets you eliminate candidates;
- opposite ends interact;
- values must be compacted or rewritten in place;
- two sequences are merged.

## Common forms

1. Opposite ends: `left` and `right` move inward.
2. Read/write: one pointer scans and one marks the next destination.
3. Same direction: pointers maintain a relationship between positions.

## Invariant

For opposite-end search, everything outside `[left, right]` has been processed or proven impossible.

## Template: sorted pair sum

```python
def pair_sum(numbers, target):
    left = 0
    right = len(numbers) - 1

    while left < right:
        total = numbers[left] + numbers[right]

        if total == target:
            return [left, right]
        if total < target:
            left += 1
        else:
            right -= 1

    return [-1, -1]
```

## Complexity

- Time: `O(n)`
- Extra space: `O(1)`

## Practice ladder

1. Reverse String
2. Valid Palindrome
3. Two Sum II
4. 3Sum

## Common failure

Moving a pointer without proving why discarded candidates cannot be answers. Sorted order is what justifies the elimination.
