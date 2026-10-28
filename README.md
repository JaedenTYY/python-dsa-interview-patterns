# Python DSA Interview Patterns

An original, Python-first guide for learning the recurring structures behind coding interview problems. The goal is not to memorise solutions. It is to recognise constraints, derive an approach from a brute-force baseline, state the invariant, and implement the solution confidently.

## How to use this repository

For every pattern:

1. Read the recognition clues without looking at the template.
2. Explain the brute-force approach and identify its repeated work.
3. Write down what every variable represents.
4. State the invariant: what must remain true after every iteration or recursive call.
5. Implement the template from memory.
6. Solve one easy problem, then two medium variations.
7. Revisit the pattern after 1 day, 1 week, and 1 month.

## Pattern roadmap

### Foundations

| # | Pattern | Typical clue |
|---:|---|---|
| 1 | [Linear scan and running state](patterns/01-linear-scan.md) | “best so far”, “consecutive”, one pass |
| 2 | [Hash maps and sets](patterns/02-hash-maps-and-sets.md) | duplicates, frequency, complement |
| 3 | [Prefix sums](patterns/03-prefix-sums.md) | repeated range sums, balance index |
| 4 | [Two pointers](patterns/04-two-pointers.md) | sorted pairs, opposite ends, in-place |
| 5 | [Sliding window](patterns/05-sliding-window.md) | contiguous subarray or substring |
| 6 | [Stack and monotonic stack](patterns/06-stacks.md) | most recent unmatched item, next greater |
| 7 | [Queue and level processing](patterns/07-queues.md) | first-in-first-out, layer-by-layer |
| 8 | [Binary search](patterns/08-binary-search.md) | sorted search space, monotonic condition |

### Linked structures and intervals

| # | Pattern | Typical clue |
|---:|---|---|
| 9 | [Linked-list pointers](patterns/09-linked-lists.md) | node references, cycle, reversal |
| 10 | [Merge intervals](patterns/10-intervals.md) | overlapping ranges, schedules |

### Trees and graphs

| # | Pattern | Typical clue |
|---:|---|---|
| 11 | [Tree DFS](patterns/11-tree-dfs.md) | root-to-leaf, subtree result |
| 12 | [Tree BFS](patterns/12-tree-bfs.md) | levels, nearest node |
| 13 | [Graph DFS and BFS](patterns/13-graph-traversal.md) | connectivity, components, shortest unweighted path |
| 14 | [Topological sort](patterns/14-topological-sort.md) | prerequisites and dependencies |
| 15 | [Union-find](patterns/15-union-find.md) | dynamic connectivity, redundant edge |

### Search and optimisation

| # | Pattern | Typical clue |
|---:|---|---|
| 16 | [Heaps and Top K](patterns/16-heaps.md) | smallest/largest K, streaming median, K-way merge |
| 17 | [Backtracking](patterns/17-backtracking.md) | all combinations, permutations, choices |
| 18 | [Dynamic programming](patterns/18-dynamic-programming.md) | overlapping subproblems, min/max/count ways |
| 19 | [Cyclic placement](patterns/19-cyclic-placement.md) | values constrained to 1..n |
| 20 | [Bit manipulation](patterns/20-bit-manipulation.md) | XOR, masks, power of two |

## Interview workflow

Use this order when facing an unfamiliar question:

```text
Clarify input/output and constraints
              ↓
Work a small example manually
              ↓
Describe a correct brute-force solution
              ↓
Identify repeated work or exploitable structure
              ↓
Choose a pattern and state its invariant
              ↓
Implement, test edge cases, analyse complexity
```

## Mastery standard

You know a pattern when you can:

- recognise it without seeing a category label;
- explain why it applies and why a tempting alternative does not;
- write the core Python structure without copying;
- state the invariant precisely;
- derive time and space complexity;
- solve an unseen medium variation in roughly 25–35 minutes;
- communicate edge cases while coding.

See [STUDY_PLAN.md](STUDY_PLAN.md) for an eight-week schedule.

## Python conventions

- Python 3.11+
- Standard library only
- `collections.deque` for queues
- `heapq` for min-heaps
- Type hints are optional in interview code; clarity is not
- Templates are starting points, not answers to memorise

## Attribution

This is original educational material inspired by the general pattern-based approach used throughout coding-interview education. Problem titles belong to their respective platforms.
