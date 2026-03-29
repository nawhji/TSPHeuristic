# TSP Heuristic: Kruskal-Based Local Trees and MST-Driven Global Linking

A new heuristic for the Traveling Salesman Problem (TSP), implemented and benchmarked in C++ against Held-Karp and MST-based 2-approximation baselines.

## Problem

Given n cities and pairwise distances, find the shortest tour visiting each city exactly once. TSP is NP-hard; exact solutions are infeasible for large instances.

## Proposed Heuristic

Inspired by Kruskal's MST algorithm. Operates in two phases:

1. **Local merging**: Filter edges by percentile cutoff, then greedily merge disjoint paths via endpoints in ascending edge weight order
2. **Global linking**: Connect remaining paths with shortest valid endpoint-to-endpoint edges to complete the Hamiltonian cycle

**Time complexity**: O(n² log n)

## Results

| Instance | n | 2-Approximation | Proposed Heuristic |
|---|---|---|---|
| small | 20 | 79.8% | 94.9% |
| a280 | 280 | 72.4% | 82.8% |
| xql662 | 662 | 68.9% | 87.6% |
| kz9976 | 9,976 | 72.8% | 84.9% |
| mona-lisa100K | 100,000 | 69.1% | 88.5% |

Accuracy = optimal tour cost / algorithm tour cost × 100%

## Baselines

- **Held-Karp**: exact DP solution, O(n² · 2ⁿ), evaluated on small instances only
- **MST 2-approximation**: O(n²), guarantees solution within 2× optimal

## Build
```bash
g++ -O2 -o tsp main.cc
./tsp <input_file>
```

## Report

Full analysis: [project report]([https://nawhji.github.io](https://github.com/nawhji/TSPHeuristic/blob/master/CSE331___Assignment__2(20231233).pdf))
