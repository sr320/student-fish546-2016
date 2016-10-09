---
layout: post
title: Blasting transcriptome against genome
date: '2016-10-03'
categories: Annotation
tags: geoduck
tags: blast

---

One way we have found to annotate a genome is take a transcriptome and blast back to the genome. Then with some table manipulation you can get a genome feature track. In the past, this has lined up with mapped reads quite well

```
!blastn \
-query ../data/Geoduck-transcriptome-v3.fa \
-db ../data/Panopea_generosa-Scaff-70k \
-task blastn \
-evalue 1e-40 \
-outfmt 6 \
-out ../analyses/trans-v3-blastn-Scaff-70k-01.tab \
-max_target_seqs 1 \
-num_threads 4
!wc -l ../analyses/trans-v3-blastn-Scaff-70k-01.tab 

    5102 ../analyses/trans-v3-blastn-Scaff-70k-01.tab

!blastn \
-query ../data/Geoduck-transcriptome-v3.fa \
-db ../data/Panopea_generosa-Scaff-70k \
-task blastn \
-evalue 1e-20 \
-outfmt 6 \
-out ../analyses/trans-v3-blastn-Scaff-70k-02.tab \
-max_target_seqs 1 \
-num_threads 4
!wc -l ../analyses/trans-v3-blastn-Scaff-70k-02.tab 

     22784 ../analyses/trans-v3-blastn-Scaff-70k-02.tab
     
```
