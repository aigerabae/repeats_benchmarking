### Chapter 1: Testing
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
- the before file might have newline characters. The .msk output file is on a single line

Input:
- fasta file with assembled 1 or more sequences; doesn't matter if its on 1 line or on multiple lines (eg 13.txt)

Output:
- masked sequences (13.txt.msk)
- GFF-format annotations (13.txt_1.gff)
- graphical representations of repeat architecture (13.txt.png)
  
### Chapter 2: drosophila:
```bash
java -jar TotalRepeats.jar ../seqs/GCA_042606445.1_ASM4260644v1_genomic.fna
```
This generates 221 contigs and so 221 separate files. If i decide to use that dataset i would have to find  way to combine those results otgether. or i coudl use a diifferent dataset with better assembly

Running on new data:
```bash
java -jar TotalRepeats.jar a4_assembly.fna -combine
```

Time: 203 seconds (3 mins 23 secs)

Combining masked files into 1:
```bash
for f in $(ls a4_assembly.fna_*.msk | sort -V); do
    cat "$f"
    echo ""   # add one newline after each file
done > a4_assembly.fna.msk
```

I pooled all masks into maskcomp folder and named them appropriately. Using comparison function:
runfiles.txt:
```text
tr.msk	rexplorer.msk
tr.msk	rmasker.msk  
tr.msk	rmodeler.msk  
tr.msk  wmasker.msk
```

```bash
java -jar TotalRepeats.jar runfiles.txt -maskscomp
```

Checking if names of sequences are the same:
```bash
awk '$1 ~ /^>/' tr.msk
```

Result:
```text
Overlapping sequence length (nt): 144,069,582 (144,069,582/144,134,966)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 11.53
(2) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 29,854,361 : 20.72%
(2) Masked (nt): 34,146,341 : 23.69%
Overlapping masking (nt): 25,085,742 : 73.47%
Overlapping coverage at sequence level = 17.41%
(1) Different mask not overlap (nt): 4,768,619 : 15.97%
(2) Different mask not overlap (nt): 9,060,599 : 26.53%
144,069,582	20.72	23.69	73.47	17.41	15.97	26.53


Overlapping sequence length (nt): 144,069,582 (144,069,582/144,134,966)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 11.53
(2) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 29,854,361 : 20.72%
(2) Masked (nt): 32,955,566 : 22.86%
Overlapping masking (nt): 23,631,562 : 71.71%
Overlapping coverage at sequence level = 16.40%
(1) Different mask not overlap (nt): 6,222,799 : 20.84%
(2) Different mask not overlap (nt): 9,324,004 : 28.29%
144,069,582	20.72	22.86	71.71	16.40	20.84	28.29


Overlapping sequence length (nt): 144,069,582 (144,069,582/144,134,966)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 11.53
(2) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 29,854,361 : 20.72%
(2) Masked (nt): 33,968,960 : 23.57%
Overlapping masking (nt): 24,815,857 : 73.05%
Overlapping coverage at sequence level = 17.22%
(1) Different mask not overlap (nt): 5,038,504 : 16.88%
(2) Different mask not overlap (nt): 9,153,103 : 26.95%
144,069,582	20.72	23.57	73.05	17.22	16.88	26.95


Overlapping sequence length (nt): 144,069,582 (144,069,582/144,134,966)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 11.53
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 29,854,361 : 20.72%
(2) Masked (nt): 36,712,479 : 25.47%
Overlapping masking (nt): 17,682,224 : 48.16%
Overlapping coverage at sequence level = 12.27%
(1) Different mask not overlap (nt): 12,172,137 : 40.77%
(2) Different mask not overlap (nt): 19,030,255 : 51.84%
144,069,582	20.72	25.47	48.16	12.27	40.77	51.84
```
