# Erdős mathematical findings

A compact index of **52 mathematical results, reductions, exact finite computations, and formal subtheorems** extracted from larger Erdős projects.

Each record points to the underlying proof, program, certificate, or formal source and states the scope at which the result was established.

## Subjects represented

The collection includes:

- Sidon-set computations and finite extremal data;
- Ramsey construction-family eliminations;
- covering-design bounds and exact finite classifications;
- Erdős–Graham #203 obstruction calculations;
- #902 tournament bounds and finite structure;
- #595 triangle-cover barriers;
- #710 prime-descent computations and Hall-matching lemmas;
- #1044 extremal formulas;
- planar integral-point-set enumeration;
- additive-basis representation-energy inequalities.

## Focused repositories

Several records have since grown into dedicated projects:

- [`erdos1192-representation-energy`](https://github.com/jaredwilder/erdos1192-representation-energy) — corrected energy/density inequalities for additive bases;
- [`erdos902`](https://github.com/jaredwilder/erdos902) — Schütte tournament problem;
- [`erdos595-barrier-tower`](https://github.com/jaredwilder/erdos595-barrier-tower) — formal triangle-cover barriers;
- [`integral-point-sets`](https://github.com/jaredwilder/integral-point-sets) — certified geometry and `d(2,8)>30000`;
- [`erdos710-descent-and-1044`](https://github.com/jaredwilder/erdos710-descent-and-1044) — #710 finite descent data and the #1044 family formula.

The copies here remain useful as compact index entries and source pointers.

## Record format

A result record normally contains:

```text
statement
problem / subject
proof or verification method
evidence path
finite or logical scope
correction history, when needed
```

The evidence object is the proof, certificate, source file, or computation itself; the index entry is navigation.

## Corrections

A small number of records document later corrections, including a fabricated benchmark citation discovered during review, a refuted growth mechanism, and a proposed generalization whose bound became weaker rather than stronger.

Those corrections are attached to the affected statements and do not change unrelated records in the collection.

## Reading the repository

Use the result note for a quick statement and then follow its evidence path for the mathematical details. Where a focused subject repository exists, that repository is usually the better place to read the complete program.

Author: Jared Wilder. License: Apache-2.0.
