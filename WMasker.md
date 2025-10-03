### Chapter 1: installing:
wget ftp://ftp.ncbi.nlm.nih.gov/pub/agarwala/windowmasker/windowmasker

Didn't work. installed some nonsense
conda activate bioinfo
conda install -c bioconda blast

windowmasker -mk_counts -in a4_assembly.fna -out a4_counts
windowmasker -ustat unit_counts -in a4_counts -out a4_masked.msk -outfmt text
