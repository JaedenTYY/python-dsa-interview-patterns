# 17. Backtracking

## Use it when

- you must generate all valid combinations, subsets, or permutations;
- every step offers several choices;
- an invalid partial choice can be abandoned early.

Backtracking is like exploring a maze: choose a corridor, explore it, then return to the junction and try another.

## Core invariant

`path` represents exactly the choices made along the current route in the decision tree.

## Template: subsets

```python
def subsets(nums: list[int]) -> list[list[int]]:
    answer = []
    path = []

    def backtrack(start: int) -> None:
        answer.append(path.copy())

        for index in range(start, len(nums)):
            path.append(nums[index])      # Choose
            backtrack(index + 1)          # Explore
            path.pop()                    # Undo

    backtrack(0)
    return answer
```

The three actions are **choose, explore, undo**. Copy `path` when saving it because the same list is later modified.

## Complexity

Often exponential and output-dependent. Subsets take `O(n × 2^n)` time including copies and `O(n)` recursion depth, excluding output.

## Practice ladder

1. Subsets
2. Letter Combinations of a Phone Number
3. Permutations
4. Combination Sum

## Common failure

Appending `path` instead of `path.copy()`. Every answer entry would then reference the same changing list.
