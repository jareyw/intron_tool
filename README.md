# intron_tool

The intron analysis tool was developed in order to assess and quantify intronic read abundance.

Please reference https://www.sciencedirect.com/science/article/abs/pii/S0092867420317530 for our paper utilizing this tool.

**make_conserved_gtf.py**

Input: transcript annotation file from UCSC RefSeq, genes.gtf\ Output: gtf file with filtered gene annotations\ Filter criteria: non-autosomal or X/Y chromosomes, non-coding (NR), poorly annotated transcripts (LOC), genes with length >1e6 base pairs

**make_conserved_intron_gtf.py**

Input: output of make_conserved_gtf.py\ Output: gtf file with conserved introns features\ Filter criteria: introns present in all annotated isoforms for each gene

**intronCounter.py**

**intronFilter.py**
