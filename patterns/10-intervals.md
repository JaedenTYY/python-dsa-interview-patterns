# 10. Merge Intervals

## Use it when

- values describe ranges such as `[start, end]`;
- ranges may overlap;
- the task involves schedules, availability, or coverage.

Think of painting sections of a wall. Overlapping painted sections form one continuous painted region.

## Core invariant

The `merged` list contains non-overlapping intervals that exactly cover every processed interval.

## Template

```python
def merge(intervals: list[list[int]]) -> list[list[int]]:
    intervals.sort(key=lambda interval: interval[0])
    merged = []

    for start, end in intervals:
        if not merged or start > merged[-1][1]:
            merged.append([start, end])
        else:
            merged[-1][1] = max(merged[-1][1], end)

    return merged
```

Sorting by start time makes it sufficient to compare each new interval with only the last merged interval.

## Complexity

`O(n log n)` time for sorting and `O(n)` output space. The scan itself is `O(n)`.

## Practice ladder

1. Summary Ranges
2. Merge Intervals
3. Insert Interval
4. Non-overlapping Intervals

## Common failure

Checking only whether endpoints are equal. Two intervals overlap whenever the new start is at most the current end.
