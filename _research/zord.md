---
layout: default
title: Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification
permalink: /research/zord
---

### <center>Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification</center>

#### <center><a href="https://feihe.github.io/">Fei He</a>, Zhihang Sun, and Hongyu Fan</center>

### <center>Abstract</center>

Analyzing multi-threaded programs is hard due to the number of thread interleavings. Partial orders can be used for modeling and analyzing multi-threaded programs. However, there is no dedicated decision procedure for solving partial-order constraints. In this paper, we propose a novel ordering consistency theory for multi-threaded program verification under sequential consistency, and we elaborate its theory solver, which realizes incremental consistency checking, minimal conflict clause generation, and specialized theory propagation to improve the efficiency of SMT solving. We conducted extensive experiments on credible benchmarks; the results show significant promotion of our approach.

### <center>Source Code</center>

Zord is the tool that implements our approach. The <a href="https://cloud.tsinghua.edu.cn/f/1dba0066f68c44f1a174/?dl=1">source code</a> contains all source code of Zord. Please refer to `readme.txt` for instructions to compile Zord.

### <center>Supplementary Data</center>

The <a href="https://cloud.tsinghua.edu.cn/f/e71639808bbd4fddb276/?dl=1">supplementary archive</a> contains all data, tables and used benchmark programs in our evaluation. The following files are in the archive:

- `benchmarks/SVCOMP-Benchmarks/*`: Benchmarks from SV-COMP 2019, used in our main experiments (Sections 6.2 and 6.3).

- `benchmarks/Nidhugg-Benchmarks/* `: Benchmarks from Nidhugg suite, used in our experiment with stateless model checkers (Section 6.4).

- `logs/*` : The raw outputs of each tool in all experiments.

- `tables/*` : Processed results of all experiments.

