---
layout: default
title: Data-driven Recurrent Set Learning For Non-termination Analysis
permalink: /research/icse23-artifact
---

## <center>Data-driven Recurrent Set Learning For Non-termination Analysis</center>

#### <center><a herf="https://linusboyle.cn/">Zhilei Han</a> and <a href="https://feihe.github.io/">Fei He</a></center>

## <center>Abstract</center>

Termination is a fundamental liveness property for program verification. In this paper, we revisit the problem of non-termination analysis and propose the first data-driven learning algorithm for synthesizing recurrent sets, where the non-terminating samples are effectively speculated by a novel method. To ensure convergence of learning, we develop a learning algorithm which is guaranteed to converge to a valid recurrent set if one exists, and thus establish its relative completeness. The methods are implemented in a prototype tool, and experimental results on public benchmarks show its efficacy in proving non-termination as it outperforms state-of-the-art tools, both in terms of cases solved and performance. Evaluation on non-linear programs also demonstrates its ability to handle complex programs.


## <center>Artifact</center>

This <a href="https://cloud.tsinghua.edu.cn/f/3fd2d579804445b5818f/?dl=1">archive</a> contains all scripts, source code and benchmarks and tools we compare with in our evaluation.


## <center>Reproduction</center>

For details about the project and how to reproduce the results, please consult the Readme file contained in the artifact.
