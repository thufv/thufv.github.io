---
layout: default
title: "Efficient Summary Reuse for Software Regression Verification"
permalink: /research/tse20-artifact
---

### <center> Efficient Summary Reuse for Software Regression Verification </center>

#### <center><a href="https://feihe.github.io/">Fei He</a>, Qianshan Yu</center>

### <center>Abstract</center>

Software systems evolve throughout their life cycles. Many revisions are produced over time. Verifying each revision of the software is impractical. Regression veriﬁcation suggests reusing intermediate results from the previous veriﬁcation runs. This paper studies regression veriﬁcation via summary reuse. Not only procedure summaries, but also loop summaries are proposed to be reused. This paper proposes a fully automatic regression veriﬁcation technique in the context of CEGAR. A lazy counterexample analysis technique is developed to improve the efﬁciency of summary reuse. We performed extensive experiments on two large sets of industrial programs (3,675 revisions of 488 Linux kernel device drivers). Results show that our summary reuse technique saves 84% to 93% analysis time of the regression veriﬁcation.

### <center>Artifact</center>

TODO

### <center>Full Results</center>

The full experimental results can be found in the following links:

- [Overall experimental results on real revisions](https://drive.google.com/file/d/11Fh1mLBsy4_0n5mG9yAkFDOxmPbraa4i/view?usp=sharing) <!-- - [Overall experimental results on larger changes](TODO). -->
- [Overall experimental results on artificial revisions](https://drive.google.com/file/d/1g4vQ_xMhTtbxEU4FeqauODJf7BxCXPig/view?usp=sharing)
- [Comparison of our approach with eVolcheck](https://drive.google.com/file/d/12a6-IAcud78jFU3hlKxVXvcdC22HLR3t/view?usp=sharing)
- [Comparison of our approach with UAutomizer](https://drive.google.com/file/d/1kFyNw3B4tPJR2_tJLOzYUcP0jivZFCgP/view?usp=sharing)
<!-- - [Results on different reuse strategies](TODO). -->

### <center>Benchmark</center>

The artificial benchmarks and real-world benchmarks can be found in the following link:

- [Real-world Benchmark](https://drive.google.com/file/d/1ouTShkBTMoqcKNizrUPlYQmwMG7BiXg3/view?usp=sharing): The first benchmark, obtained from [1], consists of 1119 revisions of 62 Linux device drivers. 
- [Artificial Benchmarks](https://drive.google.com/file/d/11ieuvscU5B-6U-Aanb0uD7pPdWM0Y8eU/view?usp=sharing): The second benchmark, prepared by ourselves, consists of 2556 program revisions of 426 Linux device drivers.

### <center>Reference</center>

[1] D. Beyer, S. Lowe, E. Novikov, A. Stahlbauer, and P. Wendler, “Precision reuse for efficient regression verification,” in Proceedings of the 2013 9th Joint Meeting on Foundations of Software Engineering. ACM, 2013, pp. 389–399.