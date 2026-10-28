# 16. Heaps and Top K

## Use it when

- you repeatedly need the smallest or largest remaining item;
- only the best `k` candidates matter;
- sorted streams must be merged;
- values arrive over time.

A heap is like a priority checkout line: the highest-priority item is always available at the front.

Python's `heapq` is a min-heap.

## Core invariant for Top K

After processing any prefix, the heap contains the best `k` candidates from that prefix.

## Template: k largest values

```python
import heapq

def k_largest(nums: list[int], k: int) -> list[int]:
    heap = []

    for number in nums:
        heapq.heappush(heap, number)

        if len(heap) > k:
            heapq.heappop(heap)

    return sorted(heap, reverse=True)
```

The smallest of the retained candidates sits at the root, so an inferior extra value is easy to remove. For a max-heap, store negated values.

## Complexity

Top K takes `O(n log k)` time and `O(k)` space. A single push or pop is `O(log k)`.

## Practice ladder

1. Last Stone Weight
2. Kth Largest Element in an Array
3. Top K Frequent Elements
4. Merge K Sorted Lists

## Common failure

Using a heap of all `n` values when only `k` matter. A size-`k` heap usually gives the intended `O(n log k)` solution.
