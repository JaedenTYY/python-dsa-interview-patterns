# 02 — Hash Maps and Sets

## Use it when

- you need fast membership checking;
- duplicates or frequencies matter;
- a value must be paired with a complement;
- order is less important than identity or count.

## Choose the structure

- `set`: “Have I seen this value?”
- `dict`: “What information is associated with this value?”

## Invariants

- Seen-set scan: before processing the current value, `seen` contains all unique earlier values.
- Frequency map: `counts[x]` equals the number of processed occurrences of `x`.

## Templates

```python
def contains_duplicate(values):
    seen = set()

    for value in values:
        if value in seen:
            return True
        seen.add(value)

    return False
```

```python
def frequencies(values):
    counts = {}

    for value in values:
        counts[value] = counts.get(value, 0) + 1

    return counts
```

## Complexity

- Average time: `O(n)`
- Extra space: `O(n)`

## Practice ladder

1. Contains Duplicate
2. Valid Anagram
3. Two Sum
4. Group Anagrams

## Common failure

Using a set when multiplicity matters. `{a, b}` cannot distinguish `aab` from `abb`; a frequency dictionary can.
