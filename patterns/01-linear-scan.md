# 01 — Linear Scan and Running State

## Use it when

- every item must be examined once;
- the current answer depends on what has been seen so far;
- wording includes “consecutive”, “running total”, “maximum so far”, or “single pass”.

## Core idea

Maintain only the information needed for the next element. A current-state variable describes what is true now; a best-so-far variable preserves the strongest earlier result.

## Invariant

After processing index `i`, `best` is the best valid answer within `values[0:i+1]`.

## Template

```python
def longest_positive_streak(values):
    current = 0
    best = 0

    for value in values:
        if value > 0:
            current += 1
        else:
            current = 0

        best = max(best, current)

    return best
```

## Complexity

- Time: `O(n)`
- Extra space: `O(1)`

## Practice ladder

1. Running Sum of 1d Array
2. Max Consecutive Ones
3. Best Time to Buy and Sell Stock
4. Maximum Subarray

## Common failure

Returning the final `current` value instead of `best`. The final streak is not necessarily the longest earlier streak.
