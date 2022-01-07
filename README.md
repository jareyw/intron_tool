# intron_tool

The intron analysis tool was developed in order to assess and quantify intronic read abundance.

Please reference https://www.sciencedirect.com/science/article/abs/pii/S0092867420317530 for our paper utilizing this tool.

The first step is to define the intronic space (or individual intron features) in which we assess intronic read abundance. The second step will be to use aligned RNA-seq data and compute intron read counts across intron features. The third step will be to normalize the data, filter the data, and then output various metrics of intron retention. Finally, we will visualize the data using R.

**<u>First step</u>**

**make_conserved_gtf.py**

Input: transcript annotation file from UCSC RefSeq, genes.gtf </br>
Output: gtf file with filtered gene annotations </br>
Filter criteria: non-autosomal or X/Y chromosomes, non-coding (NR), poorly annotated transcripts (LOC), genes with length >1e6 base pairs

**make_conserved_intron_gtf.py**

Input: output of make_conserved_gtf.py </br>
Output: gtf file with conserved (or "constitutive") introns features </br>
Filter criteria: introns present in all annotated isoforms for each gene

<u>**Second step**</u>

**intronCounter.py**

Input(s): folder containing .bam files

<u>**Third step**</u>

**intronFilter.py**

<u>**Final step**</u>
