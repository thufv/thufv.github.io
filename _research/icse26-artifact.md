---
layout: default
title: Accurate Inference of Termination Conditions
permalink: /research/icse26
---

## <center>Accurate Inference of Termination Conditions</center>

#### <center>Biting Huang, <a herf="https://linusboyle.cn/">Zhilei Han</a> and <a href="https://feihe.github.io/">Fei He</a></center>

## <center>Abstract</center>

We present the first approach to infer termination conditions that are accurate in the sense of precisely characterizing terminating states. It builds on a simple but effective framework where non-terminating states are iteratively identified and removed, and a termination prover is employed to validate the current condition. We instantiate the framework with data-driven provers and design a multi-way data sharing mechanism to enhance their interaction. Our proofs show that this method is correct, accurate, terminating, and relatively complete. Additionally, we introduce generalization techniques for recurrent sets to accelerate the iteration process. Evaluation on a benchmark of programs from the literature shows that our implementation significantly outperforms the state-of-the-art tool Acabar, producing much more accurate termination conditions, with the proposed techniques playing a crucial role in speeding up the convergence of the process.

## <center>Artifact</center>

Our artifact can be found <a href="https://doi.org/10.5281/zenodo.16891884">here</a>, which contains the source code of our tool CondTerm, together with build instructions, experiment scripts, benchmarks and tools we compare with in our evaluation.
