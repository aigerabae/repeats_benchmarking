https://www.ncbi.nlm.nih.gov/bioproject/PRJNA31257

I will be using chromosome 21 (the shortest human chromosome). I will attempt to download both assembled and unassembled versions of the same chromosome
If that doesn't work I can try a different organism or human mitochnodria (to have a smaller dataset)

The human genome assembly submitted by the GRC is available in GenBank under accession ranges GL000001-GL000258 (the scaffolds), and CM000663-CM000686 (the chromosomes).


wget -nc ftp://ftp.sra.ebi.ac.uk/vol1/srr/SRR949/007/SRR9496657
This should download raw reads from here: https://www.ebi.ac.uk/ena/browser/view/PRJNA31257
The human genome assembly submitted by the GRC is available in GenBank under accession ranges GL000001-GL000258 (the scaffolds), and CM000663-CM000686 (the chromosomes).

I downloaded assembled version from https://www.ncbi.nlm.nih.gov/nuccore/CM000683.2?report=fasta

But the raw reads are not what i wanted them to be. they are short and small. 

From what I've read I might want to download the whole dataset and then get the fraction of reads that correspond to chromosome 21. Might need bam file for that but I fear it might be too heavy
