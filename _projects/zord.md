---
layout: default
title: Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification
permalink: /projects/zord
---

### <center>Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification</center>

#### <center><a href="https://feihe.github.io/">Fei He</a>, Zhihang Sun, and Hongyu Fan</center>

### <center>Abstract</center>

Analyzing multi-threaded programs is hard due to the number of thread interleavings. Partial orders can be used for modeling and analyzing multi-threaded programs. However, there is no dedicated decision procedure for solving partial-order constraints. In this paper, we propose a novel ordering consistency theory for multi-threaded program verification under sequential consistency, and we elaborate its theory solver, which realizes incremental consistency checking, minimal conflict clause generation, and specialized theory propagation to improve the efficiency of SMT solving. We conducted extensive experiments on credible benchmarks; the results show significant promotion of our approach.

### <center>Source Code</center>

The <a href="https://cloud.tsinghua.edu.cn/f/1dba0066f68c44f1a174/?dl=1">source code</a> contains all source code of our implemented tool, Zord. Please refer to readme.txt to compile Zord.

### <center>Supplementary Data</center>

The <a href="https://cloud.tsinghua.edu.cn/f/e71639808bbd4fddb276/?dl=1">supplementary archive</a> contains all data, tables and used benchmark programs in our evaluation. The following files are in the archive:

    benchmarks/SVCOMP-Benchmarks/* : Benchmarks from SV-COMP 2019. We used them in experiments shown in section 6.2 and 6.3 of the paper.

    benchmarks/Nidhugg-Benchmarks/* : Benchmarks we obtained from Nidhugg suite. We used them to evaluate Zord with stateless model checkers (section 6.4).

    logs/* : The raw output of each tool during all experiments.

    tables/* : Processed results of all experiments, consistent with data in our paper, where

        tables/Exp1-* shows the comparison of Zord with other state-of-the-art tools (section 6.2).

        tables/Exp2-* shows the effect of passing FR derivation to the SMT solver (section 6.3).

        tables/Exp3-* shows the effect of unit edge propagation (section 6.3).

        tables/Exp4-* shows the comparison of Zord with GenMC and Nidhugg (section 6.4).
