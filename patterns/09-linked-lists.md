# 9. Linked-List Pointers

## Use it when

- the input is a chain of nodes connected by `next` references;
- nodes must be reversed, merged, removed, or checked for a cycle;
- changing links is cheaper than copying values.

Think of train cars: rearranging the connectors changes the whole train without moving the cargo.

## Core invariant for reversal

`previous` is the fully reversed prefix, while `current` begins the unprocessed suffix.

## Reversal template

```python
def reverse_list(head):
    previous = None
    current = head

    while current:
        next_node = current.next  # Save before changing the link.
        current.next = previous
        previous = current
        current = next_node

    return previous
```

## Useful variations

- **Dummy node:** simplifies changes near the head.
- **Slow/fast pointers:** find a middle or detect a cycle.
- **Two list pointers:** merge sorted lists.

## Complexity

Reversal takes `O(n)` time and `O(1)` extra space.

## Practice ladder

1. Reverse Linked List
2. Merge Two Sorted Lists
3. Linked List Cycle
4. Remove Nth Node From End of List

## Common failure

Changing `current.next` before saving the original next node. That loses access to the unprocessed remainder of the list.
