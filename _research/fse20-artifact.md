---
layout: default
title: "Interval Counterexamples for Loop Invariant Learning"
permalink: /research/fse20-artifact
---

### <center>Interval Counterexamples for Loop Invariant Learning</center>

#### <center><a href="https://xurongchen.github.io/">Rongchen Xu</a>, <a href="https://feihe.github.io/">Fei He</a> and <a href="https://homepage.iis.sinica.edu.tw/~bywang/">Bow-Yaw Wang<a>


### <center>Abstract</center>

Loop invariant generation has long been a challenging problem. Black-box learning has recently emerged as a promising method for inferring loop invariants. However, the performance depends heavily on the quality of collected examples. In many cases, only after tens or even hundreds of constraint queries, can a feasible invariant be successfully inferred.
To reduce the gigantic number of constraint queries and improve the performance of black-box learning, we introduce interval counterexamples into the learning framework. Each interval counterexample represents a set of counterexamples from constraint solvers. We propose three different generalization techniques to compute interval counterexamples. The existing decision tree algorithm is also improved to adapt interval counterexamples. We evaluate our techniques and report over 40% improvement on learning rounds and verification time over the state-of-the-art approach.

### <center>Downloads</center>
We upload our artifacts to Zenodo. [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3898483.svg)](https://doi.org/10.5281/zenodo.3898483)

### <center>Artifacts Structure</center>
The artifacts include 3 parts: Benchmark, tools and scripts.

#### Benchmark
This directory includes all the benchmarks which used in our section "EXPERIMENTS AND EVALUATION".

#### Tools
This directory includes the prototype of our approaches and the baseline.
The invariant learning uses two modules. One is the teacher and the other is 
the decision tree learner.

Our implemented decision tree is in `Tools/Ours/IDT4Inv` which includes both
source code and binaries. The baseline decision tree is in `Tools/ICE-DT(Baseline)/C50`.

`Tools/Ours/Boundary`, `Tools/Ours/Dig` and `Tools/Ours/VarElim` are 3 
strategies mentioned in section 5.1 of paper. `Tools/Ours/Exp2` is for 
the comparison experiment in section 5.2. 
These 4 strategies we implemented are based on previous work ICE-DT (POPL-16) which is also the baseline in our paper
(`Tools/ICE-DT(Baseline)/Boogie`). All of these implementation including are followed the Microsoft Public License (MS-PL). 
For each project directories, source code and binaries are both provided.

#### Scripts 
This directory provides some python scripts with which you can easily conduct the experiments in paper.

### <center>Compilation instructions</center>

The sources have the following dependencies:

1. Visual Studio 2012

2. MinGW and MSYS (http://www.mingw.org/).
   Please follow the instructions on the MinGW  website to install and setup both tools. Once setup properly, you should be able to run
   the GNU build tool chain from the MSYS shell.

   You should use MinGW Installation Manager and
   the compilation needs several basic packages (The brackets contain a version number that the actual experimental environment can run):

*  mingw-developer-toolkitbin (2013072300)
*  mingw32-base-bin (2013072300)
*  mingw32-gcc-g++-bin (8.2.0-5)
*  msys-base-bin (2013072300)

   Note: For different Windows operating system versions, some linking problems may occur during the compilation process. In this case, you need to use MinGW Installation Manager to supplement the required MinGW package environment based on the actual error message.

3. CMake (the actual experimental environment uses version 3.16.2)

4. Python 3.7 (If use the experiment script).
    Also, modules xlsxwriter, psutil are needed.


   
#### Compilation:

Note: For a fair comparison, both decision trees (ICE-DT and ours) 
use same compiler (MinGW).

Step 1: Boogie projects: Open the solution file Boogie\Source\Boogie.sln in Visual Studio and compile the sources. A successful build copies all Binaries
into the Boogie\Binaries\ folder.

Step 2: Decision tree in ICE-DT: Go to the C50 directory and build the sources from MSYS shell using the commands
```
   make clean; 
   make all;
```
   After a successful compilation, copy the files c5.0.dt_penalty and c5.0.dt_entropy into the folder Boogie\Binaries\.

Step 3: Interval decision tree (IDT4Inv directory, also use MSYS shell):
```
    mkdir build;
    cd build;
    cmake -G "Unix Makefiles" ../;
    make;
```
#### Run Experiment

Please use the script:

1. Check python3 environment with xlsxwriter, psutil modules
2. Check the paths for Boogie, z3 and the decision tree in python script
3. Check the paths to benchmarks in python script
4. python3 RunXXX.py

Additionally, If you want to run a specified case, please go to Boogie binary folder `Boogie/Binaries`, and execute:

```./boogie.exe /nologo /noinfer /contractInfer /mlHoudini:<arg1> /z3exe:<arg2> /mlHoudiniLearnerDir:<arg3> <Path-To-BPL-File>```

In above command: 

1. `<arg1>` includes 2 choose: `dt_penalty` which is the original decision tree learner by ICE-DT (POPL-16) and `IDT4Inv` which is our decision tree prototype to support interval examples.
2. `<arg2>` provides the path of execution binary for z3. If not being provided, it will try to find one replacement in Boogie binary folder.
3. `<arg3>` provides the path of execution binary for decision tree learner. If not being provided, it will try to find one replacement in Boogie binary folder. 
4. `<Path-To-BPL-File>` provides the specified case path which you want to run. 

### <center>License</center>
Microsoft Public License (MS-PL) This license governs use of the accompanying software. If you use the software, you accept this license. If you do not accept the license, do not use the software.

Definitions The terms "reproduce," "reproduction," "derivative works," and "distribution" have the same meaning here as under U.S. copyright law.
A "contribution" is the original software, or any additions or changes to the software.

A "contributor" is any person that distributes its contribution under this license.

"Licensed patents" are a contributor's patent claims that read directly on its contribution.

Grant of Rights
(A) Copyright Grant- Subject to the terms of this license, including the license conditions and limitations in section 3, each contributor grants you a non-exclusive, worldwide, royalty-free copyright license to reproduce its contribution, prepare derivative works of its contribution, and distribute its contribution or any derivative works that you create.

(B) Patent Grant- Subject to the terms of this license, including the license conditions and limitations in section 3, each contributor grants you a non-exclusive, worldwide, royalty-free license under its licensed patents to make, have made, use, sell, offer for sale, import, and/or otherwise dispose of its contribution in the software or derivative works of the contribution in the software.

Conditions and Limitations
(A) No Trademark License- This license does not grant you rights to use any contributors' name, logo, or trademarks.

(B) If you bring a patent claim against any contributor over patents that you claim are infringed by the software, your patent license from such contributor to the software ends automatically.

(C) If you distribute any portion of the software, you must retain all copyright, patent, trademark, and attribution notices that are present in the software.

(D) If you distribute any portion of the software in source code form, you may do so only under this license by including a complete copy of this license with your distribution. If you distribute any portion of the software in compiled or object code form, you may only do so under a license that complies with this license.

(E) The software is licensed "as-is." You bear the risk of using it. The contributors give no express warranties, guarantees or conditions. You may have additional consumer rights under your local laws which this license cannot change. To the extent permitted under your local laws, the contributors exclude the implied warranties of merchantability, fitness for a particular purpose and non-infringement.
