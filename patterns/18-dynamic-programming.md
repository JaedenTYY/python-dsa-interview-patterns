# 18. Dynamic Programming

## Use it when

- the same smaller problem appears repeatedly;
- the question asks for a minimum, maximum, count, or feasibility;
- a result can be built from previously solved states.

Dynamic programming is like writing intermediate totals on a notepad so you never recalculate them.

## Four questions

1. **State:** What does `dp[i]` mean?
2. **Transition:** Which smaller states create it?
3. **Base cases:** What answers are already known?
4. **Order:** When is every dependency ready?

## Core invariant

Before calculating state `i`, every state it depends on is already correct.

## Template: climbing stairs

```python
def climb_stairs(n: int) -> int:
    if n <= 2:
        return n

    two_steps_back = 1
    one_step_back = 2

    for _ in range(3, n + 1):
        current = one_step_back + two_steps_back
        two_steps_back = one_step_back
        one_step_back = current

    return one_step_back
```

Here, the state means “number of ways to reach this step,” and the transition combines the two possible previous steps.

## Complexity

This example takes `O(n)` time and `O(1)` space. DP complexity is generally the number of states multiplied by the work per state.

## Practice ladder

1. Climbing Stairs
2. Min Cost Climbing Stairs
3. House Robber
4. Coin Change

## Common failure

Starting with code instead of defining the state. If the sentence “`dp[i]` means ...” is unclear, the implementation will probably be unclear too.
