### chapter 1: humans
https://www.ncbi.nlm.nih.gov/bioproject/PRJNA31257

I will be using chromosome 21 (the shortest human chromosome). I will attempt to download both assembled and unassembled versions of the same chromosome
If that doesn't work I can try a different organism or human mitochnodria (to have a smaller dataset)

The human genome assembly submitted by the GRC is available in GenBank under accession ranges GL000001-GL000258 (the scaffolds), and CM000663-CM000686 (the chromosomes).


wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/srr/SRR949/007/SRR9496657
This should download raw reads from here: https://www.ebi.ac.uk/ena/browser/view/PRJNA31257
The human genome assembly submitted by the GRC is available in GenBank under accession ranges GL000001-GL000258 (the scaffolds), and CM000663-CM000686 (the chromosomes).

I downloaded assembled version from https://www.ncbi.nlm.nih.gov/nuccore/CM000683.2?report=fasta

But the raw reads are not what i wanted them to be. they are short and small. 
This is an old Sanger sequencing dataset (not modern NGS) from the Human Genome Project, stored in SRA. It contains just 118 reads totaling ~95k bases sequenced on an ABI 310 capillary machine by WUGSC. It’s very small and mostly archival — useful for historical reference, not for actual large-scale analysis. 
From what I've read I might want to download the whole dataset and then get the fraction of reads that correspond to chromosome 21. Might need bam file for that but I fear it might be too heavy
Nevermind. this weighs 150 gb. 
I wasnt even able to find raw reads for the reference genome but for a study that assembled a WGS of a chinese man the assembled version was same in assembled size

---
### chapter 2: drosophila
I downloaded drosophila fna.gz file from https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_042606445.1/
and gunzip it
Now need raw files:

I decided to find the one with one run for simplicity:
One issue with it is that its not paired end reads which RepeatExplorer prefers. also Reads are too long and variable in size.

Coverage is far too high (though you could subsample).
Raw reads (8.6 gb):
https://www.ncbi.nlm.nih.gov/sra/SRX24990792[accn]

Assembly:
https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_042606445.1/

Might try finding illumina reads. But i cant so i wil try like this.

Downloaded assembly. now will downlaod raw reads with SRA toolkit:
prefetch SRX24990792
fastq-dump --outdir ./ --gzip --skip-technical --readids --read-filter pass --dumpbase --split-3 SRX24990792.sra

Nevermind. Thq quality of assembly is subpar and has 211 scaffolds.
Might want to use a different assembly with better reads but where do i find that?
Right now i made it run it on modeler, totalrepeats. on totalrepeatsi deleted the results but i will do it again (took about 5 mins) and compare to modeler and then run masker as well (library based identification). the raw data are still downloading

---
### Chapter 3: Drosophila but different sequences; same strain (A4)
For unassembled data I will use:
https://www.ncbi.nlm.nih.gov/sra/SRX24990790[accn]
```bash
prefetch SRX24990790
fastq-dump --outdir ./ --gzip --skip-technical --readids --read-filter pass --dumpbase --split-3 SRX24990790/SRX24990790.sra
```

For assembled I will use
https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_002300595.1/
```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/002/300/595/GCA_002300595.1_Dmel_A4_1.0/GCA_002300595.1_Dmel_A4_1.0_genomic.fna.gz
gunzip -c GCA_002300595.1_Dmel_A4_1.0_genomic.fna.gz > a4_assembly.fa
```

Assembled sequence already has repeats soft masked with lower case letters:
Masking of fasta sequences in genomic.fna.gz files
--------------------------------------------------
Repetitive sequences in eukaryotic genome assembly sequence files, as 
identified by WindowMasker (Morgulis A, Gertz EM, Schaffer AA, Agarwala R. 
2006. Bioinformatics 22:134-41), have been masked to lower-case:

```info
Alignment programs typically have parameters that control whether the program 
will ignore lower-case masking, treat it as soft-masking (i.e. only for finding 
initial matches) or treat it as hard-masking. By default NCBI BLAST will ignore 
lower-case masking but this can be changed by adding options to the blastn 
command-line.
To have blastn treat lower-case masking in the query sequence as soft-masking 
add:
     -lcase_masking
To have blastn treat lower-case masking in the query sequence as hard-masking 
add:
     -lcase_masking -soft_masking false

Alternatively, commands such as the following can be used to generate either 
unmasked sequence or sequence masked with Ns.

Example commands to remove lower-case masking:
perl -pe '/^[^>]/ and $_=uc' genomic.fna > genomic.unmasked.fna
  -or-
awk '{if(/^[^>]/)$0=toupper($0);print $0}' genomic.fna > genomic.unmasked.fna

Example commands to convert lower-case masking to masking with Ns (hard-masked):
perl -pe '/^[^>]/ and $_=~ s/[a-z]/N/g' genomic.fna > genomic.N-masked.fna
  -or-
awk '{if(/^[^>]/)gsub(/[a-z]/,"N");print $0}' genomic.fna > genomic.N-masked.fna


*_cds_from_genomic.fna.gz & *_rna_from_genomic.fna.gz
```
