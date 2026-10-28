# 20. Bit Manipulation

## Use it when

- values are treated as binary flags;
- the problem mentions XOR, masks, powers of two, or individual bits;
- paired values cancel and one value remains.

Bits are tiny on/off switches. A mask selects which switches to inspect or change.

## XOR facts

```text
x ^ x = 0
x ^ 0 = x
XOR can be applied in any order
```

## Core invariant

After processing a prefix, `result` is the XOR of every value in that prefix; all completed pairs have cancelled.

## Template: single number

```python
def single_number(nums: list[int]) -> int:
    result = 0

    for number in nums:
        result ^= number

    return result
```

Useful bit operations:

| Goal | Python expression |
|---|---|
| Test bit `k` | `number & (1 << k)` |
| Set bit `k` | `number | (1 << k)` |
| Clear bit `k` | `number & ~(1 << k)` |
| Toggle bit `k` | `number ^ (1 << k)` |
| Remove lowest set bit | `number & (number - 1)` |

## Complexity

The single-number solution takes `O(n)` time and `O(1)` space.

## Practice ladder

1. Single Number
2. Number of 1 Bits
3. Power of Two
4. Counting Bits

## Common failure

Using clever bit operations without explaining why they match the constraints. Write a few values in binary and verify the identity first.
