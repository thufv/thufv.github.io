---
layout: default
title: Interference Relation-Guided SMT Solving for Multi-Threaded Program Verification
permalink: /research/ppopp22-artifact
---

### <center>Interference Relation-Guided SMT Solving for Multi-Threaded Program Verification</center>

#### <center>Hongyu Fan, Weiting Liu, and <a href="https://feihe.github.io/">Fei He</a></center>

### <center>Abstract</center>

Concurrent program verification is challenging due to a large number of thread interferences. A popular approach is to encode concurrent programs as SMT formulas and then rely on off-the-shelf SMT solvers to accomplish the verification. Experimental results show the promising improvements of our approach. In most existing works, an SMT solver is simply treated as the backend. There is little research on improving SMT solving for concurrent program verification.

In this paper, we recognize the characteristics of interference relation in multi-threaded programs and propose a novel approach for utilizing the interference relation in the SMT solving of multi-threaded program verification under various memory models. We show that the backend SMT solver can benefit a lot from the domain knowledge of concurrent programs. We implemented our approach in a prototype tool called Zpre and compared it with the state-of-the-art CBMC tool on credible benchmarks from the ConcurrencySafety category of SV-COMP 2019. Experimental results show promising improvements attributed to our approach.


# <center>Artifact</center>

The <a href="https://zenodo.org/record/5725047/files/Artifact.zip?download=1">artifact</a> contains all scripts, source code, log files, and benchmarks in our evaluation.

------------------------------------------------------------------------------

Environment
--------------------------------------

  - All the experiments are conducted on Ubuntu 18.04.
  - Prerequisites: cmake g++ gcc flex bison make git libwww-perl patch doxygen
  - Python version 3.8 or later and pandas installed.
  - To run full experiments, 16GB memory and 80GB disk space are needed.

------------------------------------------------------------------------------

Preparation (Optional)
--------------------------------------


* Pre-compiled binaries **cbmc, z3** are available. If your want to recompile them, just run:

  > ./compile.sh
  
    then **cbmc** and **z3** will be compiled and copied to the current folder.

--------------------------------------

Getting Started
--------------------------------------

This section shows how to set up the artifact quickly in a small subset of benchmarks.

* Just using the following command. **It will finish within 30 minutes.**
  >  ./run.sh

First, **run.sh** calls **cbmc** to generate SMT files from **benchmarks/** folder, which contains a small subset of benchmarks (randomly select from solvable examples). Three new folders -- **smt_sc/**, **smt_tso/**, and **smt_pso/** will be created; they contain the generated SMT files under SC/TSO/PSO memory models.

Secondly, **run.sh** calls **z3** to perform SMT solving with **default/partial-pre/all-pre** solving strategies. Three new folders -- **/results-sc**, **/results-tso**, and **/results-pso** will be generated; they contain log files under SC/TSO/PSO memory models.

Finally, Three excel files -- **sc.xlsx**, **tso.xlsx**, and **pso.xlsx** will be generated; they correspond to solving time of z3 with different strategies under SC/TSO/PSO memory models.

--------------------------------------

Full Experiment
--------------------------------------

This section shows how to set up the artifact in all the benchmarks.

* Just using the following command. **Dozens of hours is demand for this step.**
  >  ./run.sh ./benchmarks_all

The detailed procedure is the same as in **Getting Start**.

--------------------------------------
Directory Structure of the Artifact
------------------------------------------------------------------------------

The artifact consists of the following four directories:

  + **benchmarks/**

    Contains a small subset of solvable benchmarks randomly selected from **benchmarks_all/**.

  + **benchmarks_all/**

    Contains all the benchmarks used in evaluation. They are from the ConcurrentSafety Category of SV-COMP 2019; it contains 12 sub-categories.

  + **logs-in-paper/**

    log files and experimental results in paper

  + **compile.sh**

    Shell script to recompile cbmc and z3 (optional).

  + **run.sh**

    Shell scripts to generates and solves SMT files; and generates result files. 

  + **generate_SMT.py**

    Python script to generate SMT files under SC/TSO/PSO memory model.

  + **call-solver.py**

    Python scripts to call Z3 with different strategies.

  + **CBMC-PRE/**

    Source code of our modified cbmc

  + **Z3-PRE/**

    Source code of our modified z3

------------------------------------------------------------------------------

<!-- The <a href="https://zenodo.org/record/5725047/files/Artifact.zip?download=1">artifact</a> contains all scripts, source code, log files, and benchmarks in our evaluation. The following files are in the archive:


- `benchmarks/SVCOMP-Benchmarks/*`: Benchmarks from SV-COMP 2019, used in our main experiments (Sections 6.2 and 6.3).

- `benchmarks/Nidhugg-Benchmarks/* `: Benchmarks from Nidhugg suite, used in our experiment with stateless model checkers (Section 6.4).

- `logs/*` : The raw outputs of each tool in all experiments.

- `tables/*` : Processed results of all experiments. -->
