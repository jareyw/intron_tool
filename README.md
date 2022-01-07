# intron_tool

The intron analysis tool was developed in order to quantify intronic retention. The tool allows us to assess intron retention across specific introns and globally across the transcriptome, both in large sequencing cohorts and in model systems in response to perturbations.

Please reference https://www.sciencedirect.com/science/article/abs/pii/S0092867420317530 for our paper utilizing this tool.

The first step is to define the intronic space (i.e. individual intron features) in which we assess intronic read abundance. The second step will be to use aligned RNA-seq data and compute intron read counts across intron features. The third step will be to normalize the data, filter the data, and then output various metrics of intron retention. Finally, we will visualize the data using R. Below is a brief walkthrough of the process. For more details, refer to the Wiki.

***First step***

**make_conserved_gtf.py**

Input: transcript annotation file from UCSC RefSeq, genes.gtf </br>
Output: .gtf file with filtered gene annotations </br>
Filter criteria: non-autosomal or X/Y chromosomes, non-coding (NR), poorly annotated transcripts (LOC), genes with length >1e6 base pairs

**make_conserved_intron_gtf.py**

Input: output of make_conserved_gtf.py </br>
Output: .gtf file with conserved (or "constitutive") introns features </br>
Filter criteria: introns present in all annotated isoforms for each gene

***Second step***

The default for the tool assumes the output of _make_conserved_intron_gtf.py_ was determined from stranded, paired-end RNA-seq data. The code can be modified such that the analysis can be done on non-stranded RNA-seq data, though the intron space will be more limited.
For all sequenced samples, the .bam files must be named in a unique manner.

**intronCounter.py**

Input(s): .bam files, output of _make_conserved_intron_gtf.py_ </br>
Output(s): modified .gtf(s) containing intron read count, spanning read count, and rpkm across the intron

***Third step***

**intronFilter.py**

Input(s): folder containing modified .gtf(s) from _intronCounter.py_ </br>
Options: metric for ranking intron retention scores across samples/conditions, read length for sequencing run, type of intron retention data to output, type of data to use for ranking introns in the final output file, filtering for minimum read coverage/read count spanning an intron (properly spliced read) </br>
Output(s): file containing introns and intron retention scores for all samples of interest

***Final step***
