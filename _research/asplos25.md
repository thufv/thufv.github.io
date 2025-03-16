---
layout: default
title: Robustness Verification for Checking Crash Consistency of Non-volatile Memory
permalink: /research/asplos25
---

## <center>Robustness Verification for Checking Crash Consistency of Non-volatile Memory</center>

#### <center><a herf="https://linusboyle.cn/">Zhilei Han</a> and <a href="https://feihe.github.io/">Fei He</a></center>

## <center>Abstract</center>

The emerging non-volatile memory (NVM) technologies pro- vide competitive performance with DRAM and ensure data persistence in the event of system failure. However, it ex- hibits weak behaviour in terms of the order in which stores are committed to NVMs, and therefore requires extra efforts from developers to flush pending writes. To ensure correct- ness of this error-prone task, it is crucial to develop a rigid method to check crash consistency of programs running on NVM devices. Most existing solutions are testing-based and rely on user guidance to dynamically detect such defi- ciencies. In this paper, we present a fully automated method to verify robustness, a newly established property for en- suring crash consistency of such programs. The method is based on the observation that, reachability of a post-crash non-volatile state under a given pre-crash execution can be reduced to validity of the pre-crash execution with ad- ditional ordering constraints. Our robustness verification algorithm employs a search-based framework to explore all partial executions and states, and checks if any non-volatile state is reachable under certain pre-crash execution. Once a reachable non-volatile state is obtained, we further check its reachability under memory consistency model. The al- gorithm is implemented in a prototype tool PMVerify that leverages symbolic encoding of the program and utilizes an SMT solver to efficiently explore all executions and states. The method is integrated into the DPLL(T) framework to optimize the robustness checking algorithm. Experiments on the PMDK example benchmark show that PMVerify is competitive with the state-of-the-art dynamic tool, PSan, in
terms of robustness violation detection.

## <center>Artifact</center>

This <a href="https://cloud.tsinghua.edu.cn/f/b849731fe83c4915ab57/?dl=1">archive</a> contains all scripts, source code and benchmarks and tools we compare with in our evaluation.
