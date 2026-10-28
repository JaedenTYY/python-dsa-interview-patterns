# 6. Stack and Monotonic Stack

## Use it when

- the newest unfinished item must be handled first;
- symbols must be matched in nested order;
- you need the next greater or smaller value;
- removing one item exposes the next candidate.

A stack is like a pile of plates: the last plate added is the first one removed.

## Core invariant

The stack contains exactly the unresolved items from the part of the input already processed.

## Basic template: valid brackets

```python
def is_valid(text: str) -> bool:
    matching_open = {')': '(', ']': '[', '}': '{'}
    stack = []

    for character in text:
        if character in '([{':
            stack.append(character)
        else:
            if not stack or stack[-1] != matching_open[character]:
                return False
            stack.pop()

    return not stack
```

`stack[-1]` reads the top item. `pop()` removes it.

## Monotonic-stack form

A monotonic stack keeps values or indexes in increasing or decreasing order. When the new value breaks that order, pop resolved items.

```python
def next_greater(nums: list[int]) -> list[int]:
    answer = [-1] * len(nums)
    stack = []  # indexes whose next greater value is unknown

    for index, number in enumerate(nums):
        while stack and nums[stack[-1]] < number:
            previous_index = stack.pop()
            answer[previous_index] = number
        stack.append(index)

    return answer
```

## Complexity

Usually `O(n)` time because each item is pushed and popped at most once, with `O(n)` space.

## Practice ladder

1. Valid Parentheses
2. Remove All Adjacent Duplicates in String
3. Daily Temperatures
4. Largest Rectangle in Histogram

## Common failure

Storing values when the answer needs indexes. Decide what information will be required when an item is eventually popped.
