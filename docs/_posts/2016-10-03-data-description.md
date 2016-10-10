---
layout: post
title: What are we working with here
date: '2016-10-03'
categories: Genome-properties
tags: geoduck
tags: fasta

---

We have two draft genomes via BGI. I started out looking at the Geoduck genome.

I downloaded it.

```
!curl http://owl.fish.washington.edu/P_generosa_genome_assemblies_BGI/20160512/Panopea_generosa.scafSeq.zip \
-o ../data/Panopea_generosa.scafSeq.zip 
```

Then I got rid of some odd line breaks...

```
! awk '!/^>/ { printf "%s", $0; n = "\n" } \
/^>/ { print n $0; n = "" } \
END { printf "%s", n } \
' /Volumes/web-1/P_generosa_genome_assemblies_BGI/20160512/Panopea_generosa.scafSeq \
> /Users/sr320/git-repos/student-fish546-2016/data/Panopea_generosa.fa
```

and decided I only wanted to focus on those contigs larger than 70k.

```
!awk '!/^>/ { next } { getline seq } length(seq) >= 70000 { print $0 "\n" seq }' \
../data/Panopea_generosa.fa > ../data/Panopea_generosa-Scaff-70k.fa

!perl ../scripts/count_fasta.pl \
-i 10000 \
../data/Panopea_generosa-Scaff-70k.fa


70000:79999 	5
80000:89999 	3
90000:99999 	6
100000:109999 	4
110000:119999 	1
120000:129999 	0
130000:139999 	0
140000:149999 	0
150000:159999 	1

Total length of sequence:	1889045 bp
Total number of sequences:	20
N25 stats:			25% of total sequence length is contained in the 4 sequences >= 106547 bp
N50 stats:			50% of total sequence length is contained in the 9 sequences >= 92860 bp
N75 stats:			75% of total sequence length is contained in the 14 sequences >= 88023 bp
Total GC count:			589784 bp
GC %:				31.22 %
```

