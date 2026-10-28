# 05 — Sliding Window

## Use it when

- the answer concerns a contiguous subarray or substring;
- a window expands and sometimes shrinks;
- old work can be updated rather than recalculated.

## Forms

- Fixed-size window: add the entering value and remove the leaving value.
- Variable-size window: expand `right`; shrink `left` until the condition is valid.

## Invariant

The maintained state describes exactly the elements in the current window `[left, right]`.

## Template: fixed-size maximum sum

```python
def max_sum_size_k(values, k):
    if k > len(values):
        return None

    window_sum = sum(values[:k])
    best = window_sum

    for right in range(k, len(values)):
        window_sum += values[right]
        window_sum -= values[right - k]
        best = max(best, window_sum)

    return best
```

## Template: variable-size window

```python
left = 0

for right, value in enumerate(values):
    add(value)

    while window_is_invalid():
        remove(values[left])
        left += 1

    update_answer(left, right)
```

## Complexity

Usually `O(n)`: each element enters once and leaves at most once.

## Practice ladder

1. Maximum Average Subarray I
2. Longest Substring Without Repeating Characters
3. Minimum Size Subarray Sum
4. Permutation in String

## Common failure

Using a sliding window when negative values destroy the monotonic expand/shrink reasoning. Always justify why moving `left` improves validity.
