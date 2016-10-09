---
layout: post
title: Mapping Reads
date: '2016-10-05'
categories: Annotation
tags: RNA-seq
tags: mapping
tags: bowtie
tags: CoGe

---

One way to see the expressed part of the genome is to map RNA-seq reads back onto it (then make some feature tracks).
I did this with Bowtie..


```
!/Applications/bowtie2-2.2.9/bowtie2-build \
../data/Panopea_generosa-Scaff-70k.fa \
../data/Pg-70k-index

!/Applications/bowtie2-2.2.9/bowtie2 \
-x ../data/Pg-70k-index \
-1 /Volumes/Monarch/btea/Geoduck_v3/Geo_Pool_F_GGCTAC_L006_R1_001_val_2.fq \
-2 /Volumes/Monarch/btea/Geoduck_v3/Geo_Pool_F_GGCTAC_L006_R2_001_val_1.fq \
-S /Volumes/Monarch/course-fish546/Geo_Pool_F-Pg-70k.sam

103213920 reads; of these:
  103213920 (100.00%) were paired; of these:
    102865097 (99.66%) aligned concordantly 0 times
    261264 (0.25%) aligned concordantly exactly 1 time
    87559 (0.08%) aligned concordantly >1 times
    ----
    102865097 pairs aligned concordantly 0 times; of these:
      14413 (0.01%) aligned discordantly 1 time
    ----
    102850684 pairs aligned 0 times concordantly or discordantly; of these:
      205701368 mates make up the pairs; of these:
        205379458 (99.84%) aligned 0 times
        205853 (0.10%) aligned exactly 1 time
        116057 (0.06%) aligned >1 times
   0.51% overall alignment rate
   
```
 
 I also tested out CoGe
 
 ![screenshot](https://camo.githubusercontent.com/0d1f22de5c3509b585afc570b2d0ada1872bd965/687474703a2f2f6561676c652e666973682e77617368696e67746f6e2e6564752f636e6964617269616e2f736b697463682f436f47655f5f4d795f446174615f31444134353536422e706e67)
 
 ![settings](https://camo.githubusercontent.com/74593a3a672747976968ebd0b667c47718435b37/687474703a2f2f6561676c652e666973682e77617368696e67746f6e2e6564752f636e6964617269616e2f736b697463682f436f47655f5f4d795f446174615f31444134353539382e706e67)
 
 https://genomevolution.org/r/lslc
