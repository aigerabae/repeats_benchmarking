Creating model on hg19 using garlic:
```bash
perl ../tools/Garlic-master/bin/createModel.pl -m hg19
perl ../tools/Garlic-master/bin/createFakeSequence.pl -m hg19 -s 1Mb -o fake.fa
```

The download process is too slow with their command
I will download my own sequences and annotations to create a model:
Currently waiting for the files to download. After, need to choose which I will be using
perl ../tools/Garlic-master/bin/createModel.pl -m myOrg -f myOrg.fa -r RM.out -t TRF.out -g Genes.table

CITATION

Realistic artificial DNA sequences as negative controls for computational genomics.
Caballero J, Smit AF, Hood L, Glusman G.
Nucl. Acids Res. 2014
doi: 10.1093/nar/gku356 
