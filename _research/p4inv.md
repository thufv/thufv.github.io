---
layout: default
title: P4Inv: Inferring Packet Invariants for Verification of Stateful P4 Programs
permalink: /research/p4inv
---

### <center>P4Inv: Inferring Packet Invariants for Verification of Stateful P4 Programs</center>

#### <center>Delong Zhang, Chong Ye, <a href="https://feihe.github.io/">Fei He</a></center>

### <center>Abstract</center>

P4 is widely adopted for programming data planes in software-defined networking. Formal verification of P4 pro grams is essential to ensure network reliability and security. However, existing P4 verifiers overlook the stateful nature of packet processing, rendering them inadequate for verifying complex stateful P4 programs. 

In this paper, we introduce a novel concept called packet invariants to address the stateful aspects of P4 programs. We present an automated verification tool specifically designed for stateful P4 programs. This algorithm efficiently discovers and validates packet invariants in a data-driven manner, offering a novel and effective verification approach for stateful P4 pro grams. To the best of our knowledge, this approach represents the f irst attempt to generate and leverage domain-specific invariants for P4 program verification. We implement our approach in a prototype tool called P4Inv. Experimental results demonstrate its effectiveness in verifying stateful P4 programs.

### <center>Source Code</center>

P4Inv is the tool that implements our approach. We opensource P4Inv [here](https://github.com/NVThufv/P4Inv). Please refer to `README.md` for instructions to build and run P4Inv.

### <center>Supplementary Data</center>

The <a href="https://cloud.tsinghua.edu.cn/f/8335d25c656a4cbd954d/?dl=1">supplementary archive</a> contains the benchmark and data used and produced in our evaluation. It contains:

- `artifact/benchmark`: Benchmarks that are used in our evaluation.
- `artifact/midFiles`: The raw outputs and logs that are produced by P4Inv and other tools compared in our evaluation.