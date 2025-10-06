### Chapter 1: installing:
wget ftp://ftp.ncbi.nlm.nih.gov/pub/agarwala/windowmasker/windowmasker

Didn't work. installed some nonsense

Installing with conda:
```bash
conda activate bioinfo
conda install -c bioconda blast
```

### Chapter 2: running
```bash
windowmasker -mk_counts -in a4_assembly.fna > a4_counts
windowmasker -ustat a4_counts -outfmt fasta -in a4_assembly.fna > a4_masked.msk
```

Runtime: 1 min 18 seconds
