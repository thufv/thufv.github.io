---
layout: default
title: "Termination Analysis for Evolving Programs"
permalink: /research/oopsla20a-artifact
---

### <center> Termination Analysis for Evolving Programs : An Incremental Approach by Reusing Certified Modules</center>

#### <center><a href="https://feihe.github.io/">Fei He</a>, Jitao Han</center>

### <center>Abstract</center>

Research on program termination has a long tradition. However, most of the existing techniques target a single program only. We propose in this paper an incremental termination analysis approach by reusing certified modules across different program versions. A transformation-based procedure is further developed to increase the reusability of certified modules. The proposed approach has wide applicability, applicable to various program changes. The proposed technique, to the best of our knowledge, represents a novel attempt to the termination analysis of evolving programs. We implemented the approach on top of Ultimate Automizer. Experimental results show dramatic improvement of our approach over the state-of-the-art tool.

### <center>Artifact</center>

The  [artifact archive](https://drive.google.com/file/d/1Hwj9QDE7SUVWye_RBdvoHOtbtY5lE1sr/view?usp=sharing) contains tool, source code, results and used benchmark programs in our evaluation. For details, please refer to `README.md` in the archive.  

### <center>Full Results</center>

The full experimental results on artificial benchmarks and real-world benchmarks can be found in the following tables:

- [Tables for summary results](https://drive.google.com/file/d/1FpCsSnBHiJN-4CrPnTtIcxrbN-IEHcqP/view?usp=sharing).
- [Tables for detail results](https://drive.google.com/file/d/1x8CCax2RbxQtQAkDO3HKxy4nHbvCvfLD/view?usp=sharing)

### <center>Benchmark</center>

The artificial benchmarks and real-world benchmarks can be found in the following link:

- [Artificial Benchmark](https://drive.google.com/file/d/1cbLsy6WEqbZOM9b6_OL5f24JkC6pSTEy/view?usp=sharing): The benchmark consists of 90 revisions of 15 distinct programs. The 15 original programs were obtained from [Heizmann et al. 2014].
- [Real-world Benchmarks](https://drive.google.com/file/d/1xNDp70Fy5zxufHyMnwYLGvmaOz9pSJci/view?usp=sharing): This set of programs were collected from [Codeforces](https://codeforces.com/), a website that hosts competitive programming contests. In order not to disclose user information, we anonymize the program. 
  **Please Note: If it involves infringement, please contact us to delete it!**
