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

## Results

In this section, the data collected from exploring the various problems and
algorithms are presented in table format. **Results are discussed and analyzed in
the sections that follow.**

| Problem | Label | Actions | Expansions | Goal Tests | New Nodes | Plan Length | Time |
| :---: | --- | :---: | :---: | :---: | :---: | :---: | :---: |
| p1 | bfs | 20 | 43 | 56 | 178 | 6 | 3.83E-02 |
| p1 | dfs | 20 | 21 | 22 | 84 | 20 | 8.90E-03 |
| p1 | ucs | 20 | 60 | 62 | 240 | 6 | 2.62E-02 |
| p1 | gb-unmet | 20 | 7 | 9 | 29 | 6 | 3.65E-03 |
| p1 | gb-level | 20 | 6 | 8 | 28 | 6 | 1.17E+00 |
| p1 | gb-max | 20 | 6 | 8 | 24 | 6 | 3.40E-01 |
| p1 | gb-set | 20 | 7 | 9 | 31 | 7 | 1.84E+00 |
| p1 | as-unmet | 20 | 50 | 52 | 206 | 6 | 4.05E-02 |
| p1 | as-level | 20 | 28 | 30 | 122 | 6 | 6.36E-01 |
| p1 | as-max | 20 | 43 | 45 | 180 | 6 | 3.51E-01 |
| p1 | as-set | 20 | 51 | 53 | 208 | 6 | 1.24E+00 |

| Problem | Label | Actions | Expansions | Goal Tests | New Nodes | Plan Length | Time |
| :---: | --- | :---: | :---: | :---: | :---: | :---: | :---: |
| p2 | bfs | 72 | 3343 | 4609 | 30503 | 9 | 5.20E-01 |
| p2 | dfs | 72 | 624 | 625 | 5602 | 619 | 6.22E-01 |
| p2 | ucs | 72 | 5154 | 5156 | 46618 | 9 | 9.62E-01 |
| p2 | gb-unmet | 72 | 17 | 19 | 170 | 9 | 2.49E-02 |
| p2 | gb-level | 72 | 9 | 11 | 86 | 9 | 9.06E-01 |
| p2 | gb-max | 72 | 27 | 29 | 249 | 9 | 1.19E+00 |
| p2 | gb-set | 72 | 26 | 28 | 232 | 10 | 6.05E+00 |
| p2 | as-unmet | 72 | 2467 | 2469 | 22522 | 9 | 1.13E+00 |
| p2 | as-level | 72 | 357 | 359 | 3426 | 9 | 2.09E+01 |
| p2 | as-max | 72 | 2887 | 2889 | 26594 | 9 | 1.30E+02 |
| p2 | as-set | 72 | 2102 | 2104 | 19395 | 9 | 7.26E+02 |

| Problem | Label | Actions | Expansions | Goal Tests | New Nodes | Plan Length | Time |
| :---: | --- | :---: | :---: | :---: | :---: | :---: | :---: |
| p3 | bfs | 88 | 14663 | 18098 | 129625 | 12 | 1.56E+00 |
| p3 | dfs | 88 | 408 | 409 | 3364 | 392 | 2.64E-01 |
| p3 | ucs | 88 | 18510 | 18512 | 161936 | 12 | 2.57E+00 |
| p3 | gb-unmet | 88 | 25 | 27 | 230 | 15 | 5.57E-02 |
| p3 | gb-level | 88 | 14 | 16 | 126 | 14 | 2.36E+00 |
| p3 | gb-max | 88 | 21 | 23 | 195 | 13 | 2.26E+00 |
| p3 | gb-set | 88 | 42 | 44 | 405 | 18 | 2.83E+01 |
| p3 | as-unmet | 88 | 7388 | 7390 | 65711 | 12 | 1.68E+00 |
| p3 | as-level | 88 | 369 | 371 | 3403 | 12 | 4.17E+01 |
| p3 | as-max | 88 | 9580 | 9582 | 86312 | 12 | 7.56E+02 |
| p3 | as-set | 88 | 5963 | 5965 | 54668 | 12 | 3.42E+03 |

| Problem | Label | Actions | Expansions | Goal Tests | New Nodes | Plan Length | Time |
| :---: | --- | :---: | :---: | :---: | :---: | :---: | :---: |
| p4 | bfs | 104 | 99736 | 114953 | 944130 | 14 | 1.01E+01 |
| p4 | dfs |  -  |   -   |    -   |   -    | -  |  -    |
| p4 | ucs | 104 | 113339 | 113341 | 1066413 | 14 | 1.36E+01 |
| p4 | gb-unmet | 104 | 29 | 31 | 280 | 18 | 6.06E-02 |
| p4 | gb-level | 104 | 17 | 19 | 165 | 17 | 5.29E+00 |
| p4 | gb-max | 104 | 56 | 58 | 580 | 17 | 5.50E+00 |
| p4 | gb-set | 104 | 114 | 116 | 1229 | 24 | 1.13E+02 |
| p4 | as-unmet | 104 | 34330 | 34332 | 328509 | 14 | 7.27E+00 |
| p4 | as-level | 104 | 1208 | 1210 | 12210 | 15 | 2.01E+02 |
| p4 | as-max | 104 | 62077 | 62079 | 599376 | 14 | 6.51E+03 |
| p4 | as-set | 104 | 37912 | 37914 | 373328 | 14 | 3.14E+04 |


## Search Complexity Studies

In this section, I analyze the search complexity as a function of domain size,
search algorithm, and heuristic.

## Search Time Studies

In this section, I analyze the search time as a function of domain size, search
algorithm, and heuristic.

## Search Optimality Studies

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