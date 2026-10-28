# 03 — Prefix Sums

## Use it when

- many sums over ranges are requested;
- left and right portions must be compared;
- recalculating each range repeats additions.

## Core idea

Store cumulative totals so a range sum becomes subtraction.

If `prefix[i]` is the sum of the first `i` values, then:

```text
sum(left..right) = prefix[right + 1] - prefix[left]
```

## Invariant

`prefix[i]` equals the sum of `values[0:i]`; index `i` itself is excluded.

## Template

```python
def build_prefix(values):
    prefix = [0]

    for value in values:
        prefix.append(prefix[-1] + value)

    return prefix


def range_sum(prefix, left, right):
    return prefix[right + 1] - prefix[left]
```

## Complexity

- Build: `O(n)` time and `O(n)` space
- Each range query: `O(1)`

## Practice ladder

1. Running Sum of 1d Array
2. Find Pivot Index
3. Range Sum Query — Immutable
4. Subarray Sum Equals K

## Common failure

Mixing inclusive array indexes with the exclusive prefix definition. Write the meaning of `prefix[i]` before coding.
