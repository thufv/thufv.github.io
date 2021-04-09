---
layout: default
title: Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification
---

[Homepage](./index.html)

Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification
Fei He, Zhihang Sun, and Hongyu Fan

##Abstract

Analyzing multi-threaded programs is hard due to the number of thread interleavings. Partial orders can be used for modeling and analyzing multi-threaded programs. However, there is no dedicated decision procedure for solving partial-order constraints. In this paper, we propose a novel ordering consistency theory for multi-threaded program verification under sequential consistency, and we elaborate its theory solver, which realizes incremental consistency checking, minimal conflict clause generation, and specialized theory propagation to improve the efficiency of SMT solving. We conducted extensive experiments on credible benchmarks; the results show significant promotion of our approach.

##Artifact

The <a href="https://cloud.tsinghua.edu.cn/f/ee6cce063c9c4b2394d3">supplementary archive</a> contains all source code of Zord.
The <a href="https://cloud.tsinghua.edu.cn/f/d98603a405a9486baec5/">supplementary archive</a> contains all data, tables, used benchmark programs and configurations of our evaluation.
