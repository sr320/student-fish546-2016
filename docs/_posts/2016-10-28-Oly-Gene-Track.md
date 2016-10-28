---
layout: post
title: Oly Gene Track
date: '2016-10-28'
categories: Data
tags: genome, gff, gene, blast,  

---

Using blastn I identified where the transcriptome matched the genome.

```
!blastn \
-query OlyO_v6_transcriptome.fa \
-db Ostrea_lurida-Scaff-30k \
-task blastn \
-evalue 1e-20 \
-outfmt 6 \
-out ../analyses/trans-v6-blastn-Scaff-30k-02.tab \
-max_target_seqs 1 \
-num_threads 6

!wc -l ../analyses/trans-v6-blastn-Scaff-30k-02.tab 

37104 ../analyses/trans-v6-blastn-Scaff-30k-02.tab



!head ../analyses/trans-v6-blastn-Scaff-30k-02.tab

TR2|c0_g1_i1	scaffold70795	87.33	150	17	1	210	359	47164	47017	2e-46	  183
TR2|c0_g1_i1	scaffold70795	86.00	150	18	2	210	359	46514	46660	1e-42	  170
TR5|c0_g1_i1	scaffold25028	85.25	122	18	0	8	129	6458	6337	1e-33	  140
TR7|c0_g1_i1	scaffold86430	89.33	75	8	0	237	311	12966	12892	2e-21	  100
TR16|c0_g1_i1	scaffold3873	77.05	244	42	3	18	253	29329	29092	1e-47	  187
TR28|c0_g1_i1	scaffold52557	82.35	136	13	3	139	272	16379	16253	7e-32	  134
TR43|c0_g1_i1	scaffold40838	71.75	223	50	3	18	228	2748	2527	2e-26	  116
TR66|c0_g1_i1	scaffold12565	83.53	249	32	3	7	251	38995	39238	2e-69	  259
TR66|c0_g2_i1	scaffold12565	82.99	288	40	3	1	284	38956	39238	1e-79	  293
TR74|c0_g1_i1	scaffold26204	80.33	122	22	2	13	134	27355	27474	6e-23	  105
```



Then a little perl to transform to gff

```
!perl ../scripts/2_Blast2Gff.pl \
-i ../analyses/trans-v6-blastn-Scaff-30k-02.tab \
-s "something" \
-o ../analyses/Olyv6_blastn-Scaff-30k.gff \
-p "gene-blast" -d "Ostrea-scaff-30k"
```


<img src="http://eagle.fish.washington.edu/cnidarian/skitch/student-fish546-2016_05-Getting-IGV-ready_ipynb_at_master_·_sr320_student-fish546-2016_1DC3C40C.png" alt="student-fish546-2016_05-Getting-IGV-ready_ipynb_at_master_·_sr320_student-fish546-2016_1DC3C40C.png"/>


[GFF file](https://raw.githubusercontent.com/sr320/student-fish546-2016/master/analyses/Olyv6_blastn-Scaff-30k.gff)

[Draft Genome File](https://raw.githubusercontent.com/sr320/student-fish546-2016/master/data/Ostrea_lurida-Scaff-30k.fa)
