java -jar TotalRepeats.jar 13.txt 
```output
Current Directory: /media/aygera/external_disk/biostar/RN/repeats_benchmarking/Test_TotalRepeats
Command-line arguments:
Target file or Folder: 13.txt

Running...
kmer=19
Classification index (0-230)=12
Repeat block length =90
Sensitive detection enabled.
Target file: 13.txt
Target sequence length = 3407832 nt
Sequence coverage by repeats=98.35%
Short tandem repeat (STR) sequence coverage=1.18%
Sequence gap (bp)=0 (0.0000%)

Masking time taken: 1 seconds

Saving masked file: 13.txt.msk
Clustering started...
Saving report file: 13.txt_1.gff
Saving picture 9330x1648 : 13.txt.png
Total duration: 3 seconds
```

java -jar TotalRepeats.jar NC_037455.txt
```output
Current Directory: /media/aygera/external_disk/biostar/RN/repeats_benchmarking/Test_TotalRepeats
Command-line arguments:
Target file or Folder: NC_037455.txt

Running...
kmer=19
Classification index (0-230)=12
Repeat block length =90
Sensitive detection enabled.
Target file: NC_037455.txt
Target sequence length = 159752 nt
Sequence coverage by repeats=40.13%
Short tandem repeat (STR) sequence coverage=0.92%
Sequence gap (bp)=0 (0.0000%)

Masking time taken: 0 seconds

Saving masked file: NC_037455.txt.msk
Clustering started...
Saving report file: NC_037455.txt_1.gff
Saving picture 4100x316 : NC_037455.txt.png
Total duration: 0 seconds
```

java -jar TotalRepeats.jar NW_026063317.txt
```output
Current Directory: /media/aygera/external_disk/biostar/RN/repeats_benchmarking/Test_TotalRepeats
Command-line arguments:
Target file or Folder: NW_026063317.txt

Running...
kmer=19
Classification index (0-230)=12
Repeat block length =90
Sensitive detection enabled.
Target file: NW_026063317.txt
Target sequence length = 7126875 nt
Sequence coverage by repeats=74.89%
Short tandem repeat (STR) sequence coverage=17.59%
Sequence gap (bp)=400 (0.0056%)

Masking time taken: 4 seconds

Saving masked file: NW_026063317.txt.msk
Clustering started...
Saving report file: NW_026063317.txt_1.gff
Saving picture 13448x2720 : NW_026063317.txt.png
Total duration: 10 seconds
```


java -jar TotalRepeats.jar 14.txt
```output
Current Directory: /media/aygera/external_disk/biostar/RN/repeats_benchmarking/Test_TotalRepeats
Command-line arguments:
Target file or Folder: 14.txt

Running...
kmer=19
Classification index (0-230)=12
Repeat block length =90
Sensitive detection enabled.
Target file: 14.txt
Target sequence length = 80394605 nt
Sequence coverage by repeats=22.99%
Short tandem repeat (STR) sequence coverage=13.29%
Sequence gap (bp)=700 (0.0009%)

Masking time taken: 120 seconds

Saving masked file: 14.txt.msk
Clustering started...
Saving report file: 14.txt_1.gff
Saving picture 44931x2720 : 14.txt.png
Total duration: 211 seconds
```

I ran it on all 4 test files. Now let's write down key outputs:
- .msk file with repeats masked
- .gff file with report with this info:
Seqid (fastq name file)
	Repeat (classification - STR - short tandem repeats,UCRP,CRP)
ClusterID (clustering group)
	Start 
	Stop
Length
Strand
	Phase

Let's apply before sequence on after and see the differences.
What I noted:
- the before file might have small letters or capital letter, and have newline characters. he .msk output file is on a single line and has only lower case letters



Cool facts I found while reading about repeats:
-  For instance, about 50% of the human genome consists of repeats5, while roughly 4% of human genes harbor transposable elements in their protein-coding regions6. Because many of these repeats (~89.5%) are located within introns, they have been erroneously assumed to be non-functional7. However, increasing research indicates the significant impacts that repeats in coding and noncoding regions can have on evolution, gene expression regulation, and variation induction8,9,10. For example, when repeats are present in the coding region they get translated canonically. Not only can non-coding repeats be translated by a non-canonical mechanism11, but even the telomeric repeat RNAs can get translated12. Moreover, recent studies have shown that such repeats are closely related to a variety of diseases, such as genetic disorders (e.g., Hemophilia), neurological diseases (e.g., poly-Q diseases), and cancers (e.g., endometrial, stomach and colorectal cancers)
 - In genetics, tandem repeats occur in DNA when a pattern of one or more nucleotides is repeated and the repetitions are directly adjacent to each other, e.g. ATTCG ATTCG ATTCG, in which the sequence ATTCG is repeated three times.[1]

