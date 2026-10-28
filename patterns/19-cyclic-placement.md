# 19. Cyclic Placement

## Use it when

- an array of length `n` contains values constrained near `1..n` or `0..n`;
- values should correspond naturally to indexes;
- you need missing or duplicate values with constant extra space.

Think of numbered students standing in numbered positions. Swap each student toward the matching position.

## Core invariant

After placement, any value in the expected range is either at its correct index or blocked by a duplicate.

## Template: missing numbers from `1..n`

```python
def find_missing(nums: list[int]) -> list[int]:
    index = 0

    while index < len(nums):
        correct_index = nums[index] - 1

        if nums[index] != nums[correct_index]:
            nums[index], nums[correct_index] = (
                nums[correct_index],
                nums[index],
            )
        else:
            index += 1

    return [
        index + 1
        for index, value in enumerate(nums)
        if value != index + 1
    ]
```

The index advances only when the current position is resolved. The duplicate check prevents endless swapping.

## Complexity

`O(n)` time because each swap places at least one value, and `O(1)` auxiliary space excluding the answer.

## Practice ladder

1. Missing Number
2. Find All Numbers Disappeared in an Array
3. Find the Duplicate Number
4. First Missing Positive

## Common failure

Using this pattern when values do not map to a small index range. Without that constraint, a set or sorting is usually more appropriate.
