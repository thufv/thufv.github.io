---
layout: default
title: Compilation Error Repairing by Examples
permalink: /research/prem
---

### <center>Compilation Error Repairing by Examples</center>

#### <center><a href="https://paulz.me/">Fengmin Zhu</a> and <a href="https://feihe.github.io/">Fei He</a></center>

### <center>Abstract</center>

Compilation errors frequently present in program development. The error messages prompted by the compiler are often inadequate and seem cryptic to novices. This paper presents a fully automated approach for repairing compilation errors by parse tree transformations. The key technical novelty of our approach lies in an expressive domain-specific language (DSL) that is capable of expressing a rich set of tree transformations for fixing a variety of practical compilation errors. This DSL is language-independent. It not only exploits the information contained in compiler error messages, but also discovers the implicit relationship between parse tree nodes. With this DSL, we further propose a synthesis algorithm that learns tree transformers from user-provided parse tree examples, by leveraging the programming-by-example (PBE) technique. In an evaluation on 40 real-world problems, our approach solved 38 of them using only 2 -- 5 examples each.

### <center>PREM</center>

PREM (Program Repair using Error Messages) is the prototype tool of our compilation error repair approach. The source code is publicly accessible in this [repo](https://github.com/thufv/Prem). Please follow the instructions of README before you start.

### <center>Reproducing Experiments</center>

Please follow the [reproducing guide](https://github.com/thufv/Prem/blob/master/eval/REPRODUCING.md). All necessary data and scripts are included in the [PREM repo](https://github.com/thufv/Prem).
