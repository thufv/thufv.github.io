---
layout: default
title: On Temporal Verification of Stateful P4 Program
permalink: /research/p4tv
---

### <center>On Temporal Verification of Stateful P4 Program</center>

#### <center>Delong Zhang*, Chong Ye*, <a href="https://feihe.github.io/">Fei He</a></center>

### <center>Abstract</center>

Stateful P4 programs offload network states from the control plane to the data plane, enabling unprecedented network programmability. However, existing P4 verifiers overapproximate the stateful nature of P4 programs and are inherently inadequate for verifying network functions that require stateful decision-making. 

To overcome this limitation, this paper introduces an innovative approach to verify P4 programs while accounting for their stateful feature. We propose a specification language named P4LTL, tailored for describing temporal properties of stateful P4 programs at the packet processing level. Additionally, we introduce a novel concept called the Büchi transaction, representing the product of the P4 program and the P4LTL specification. The P4 program verification problem can be reduced to determining the existence of any fair and feasible trace within the Büchi transaction. To the best of our knowledge, our approach represents the first endeavor in temporal verification of stateful P4 programs at the packet processing level. We implemented a prototype tool called p4tv. Evaluation results demonstrate p4tv’s effectiveness and efficiency in temporal verification of stateful P4 programs.

### <center>Source Code</center>

P4TV is the tool that implements our approach. We opensource P4TV [here](https://github.com/NVThufv/P4TV). Please refer to `README.md` for instructions to build and run P4TV.

### <center>Supplementary Data</center>

The <a href="https://cloud.tsinghua.edu.cn/f/6b3896f63d264245b6b7/?dl=1">supplementary archive</a> contains the benchmark and data used and produced in our evaluation. It contains:

- `artifact/benchmark`: Benchmarks that are used in our evaluation.
- `artifact/midFiles`: The boogie files and logs that are produced by P4TV in our evaluation.