---
layout: default
title: A Translator from P4 Programs to Boogie
permalink: /research/P4-to-Boogie
---

### <center>Satisfiability Modulo Ordering Consistency Theory for Multi-threaded Program Verification</center>

#### <center><a href="https://feihe.github.io/">Fei He</a>, Chong Ye</center>

### <center>Abstract</center>

P4 is a main-streaming language for Software Defined Network (SDN) data planes. Compared to previous SDN protocols, P4 is target-independent, feasible, and configurable. However, logic errors may occur in P4 programs, resulting in improper packet processing, which may cause serious network errors and information disclosure. In addition, P4 programs contain many branches and thus are more challenging to ensure correctness.
Formal verification is a powerful technique to verify the correctness of P4 programs. Unfortunately, current P4 verification studies lack basic toolchains, and their intermediate languages are not expressive enough. We present P4b, an efficient translator from P4 programs to Boogie, a verification-oriented intermediate representation. We provide formal translation rules to ensure the correctness of the translation process. The translated results can be verified by the toolchain of Boogie. We conducted experiments on 170 P4 programs collected from GitHub, and the experiment results demonstrate that our translator is useful and practical.

### <center>Source Code</center>

P4-to-Boogie is the tool that implements our approach. The <a href="https://cloud.tsinghua.edu.cn/f/1dba0066f68c44f1a174/?dl=1">source code</a> contains all source code of P4-to-Boogie. Please refer to `readme.txt` for instructions to compile Zord.

### <center>Tool Usage</center>

P4B takes P4 programs as input.

```
# Translate P4 into Boogie for Boogie verifier
p4c-translator <P4File> -o <outFile>

# Translate P4 into Boogie for UAutomizer
p4c-translator <P4File> --ua2 --p4ltl <P4LTLSpec> -o <outFile>
```


