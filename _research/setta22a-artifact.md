---
layout: default
title: Mastery: Shifted-Code-Aware Structured Merging
permalink: /research/setta22a-artifact
---

## <center>Mastery: Shifted-Code-Aware Structured Merging</center>

#### <center><a href="https://paulz.me/">Fengmin Zhu</a>, Xingyu Xie, Dongyu Feng, <a href="https://people.cs.vt.edu/nm8247/">Na Meng</a>, and <a href="https://feihe.github.io/">Fei He</a></center>

## <center>Abstract</center>

Three-way merging is an essential infrastructure in version control systems. While the traditional line-based textual methods are efficient, syntax-based structured approaches have shown advantages in enhancing merge accuracy. Prior structured merging approaches visit abstract syntax trees in a top-down manner, which is hard to detect and merge shifted code in the general sense. This paper presents a novel methodology combining a top-down and a bottom-up visit of abstract syntax trees, which manipulates shifted code effectively and elegantly. This merge algorithm is order-preserving and linear-time. Compared with four representative merge tools in 40,533 real-world merge scenarios, our approach achieves the highest merge accuracy and 2.4× as fast as a state-of-the-art structured merge tool.

## <center>Source Code</center>

We open-source mastery at [here](https://github.com/thufv/mastery). You could follow the [readme](https://github.com/thufv/mastery/blob/master/README.md) to build and try the tool.

## <center>Artifact</center>

We provide our evaluation as a reproducible artifact at [here](https://zenodo.org/record/5507555). In a docker image, benchmarks collected from GitHub, executable tools to compare and scripts to run experiments and to show the results are contained. You could follow the instructions to set up the docker image and reproduce the evaluation.
