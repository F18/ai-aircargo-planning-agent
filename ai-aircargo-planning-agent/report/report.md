# Project Report: Air Cargo Planning Agent

In this project, I consider a forward planning agent to solve four air cargo
planning problems, each with increasing complexity. I explore various uninformed
search algorithms, as well as informed search algorithms in combination with
various heuristics.

## Problem Labels

The following table provides some useful labels that will be used to identify
the various air cargo planning problems explored in this report:

| Label | Problem Description |
| -------- | -------- |
| p1 | Air Cargo Problem 1 |
| p2 | Air Cargo Problem 2 |
| p3 | Air Cargo Problem 3 |
| p4 | Air Cargo Problem 4 |

## Algorithm Labels

The following table provides some useful labels that will be used to identify
the various algorithms explored in this report:

| Label | Search Algorithm | Heuristic |
| -------- | -------- | -------- |
| bfs | Breadth-First Search | n/a |
| dfs | Depth-First Search | n/a |
| ucs | Uniform Cost Search | n/a |
| gb-unmet | Greedy Best First Search | Unmet Goals |
| gb-level | Greedy Best First Search | Level Sum |
| gb-max | Greedy Best First Search | Max Level |
| gb-set | Greedy Best First Search | Set Level |
| as-unmet | A* Search | Unmet Goals |
| as-level | A* Search | Level Sum |
| as-max | A* Search | Max Level |
| as-set | A* Search | Set Level |

## Tables of Results

The following table provides a summary of the results for various problems and
algorithms. These results are discussed and analyzed in the following sections.

| Problem | Label | Actions | Expansions | Goal Tests | New Nodes | Plan Length | Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| p1 | bfs | 20 | 43 | 56 | 178 | 6 | 0.03829 |
| p1 | dfs | 20 | 21 | 22 | 84 | 20 | 0.00890|
| p1 | ucs | 20 | 60 | 62 | 240 | 6 | 0.02619 |
| p1 | gb-unmet | 20 | 7 | 9 | 29 | 6 | 0.00365|
| p1 | gb-level | 20 | 6 | 8 | 28 | 6 | 1.17321|
| p1 | gb-max | 20 | 6 | 8 | 24 | 6 | 0.33996|
| p1 | gb-set | 20 | 7 | 9 | 31 | 7 | 1.84361|
| p1 | as-unmet | 20 | 50 | 52 | 206 | 6 | 0.04053|
| p1 | as-level | 20 | 28 | 30 | 122 | 6 | 0.63649|
| p1 | as-max | 20 | 43 | 45 | 180 | 6 | 0.35067|
| p1 | as-set | 20 | 51 | 53 | 208 | 6 | 1.23527|


## Search Complexity

In this section, I analyze the search complexity as a function of domain size,
search algorithm, and heuristic.

## Search Time Studies

In this section, I analyze the search time as a function of domain size, search
algorithm, and heuristic.

## Search Optimality

In this section, I analyze the solution optimality as a function of domain
size, search algorithm, and heuristic.

## Q & A

In this section, I answer some questions regarding the appropriateness of the various methods given different considerations on domain size and optimality.

### Question 1

*Which algorithm or algorithms would be most appropriate for planning in a very
restricted domain (i.e., one that has only a few actions) and needs to operate
in real time?*

AS

### Question 2

*Which algorithm or algorithms would be most appropriate for planning in very
large domains (e.g., planning delivery routes for all UPS drivers in the U.S. on
a given day)*

GB

### Question 3

*Which algorithm or algorithms would be most appropriate for planning problems where it is important to find only optimal plans?*

BFS