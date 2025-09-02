Creating model on hg19 using garlic:
```bash
# in garlic-master models folder
perl ../bin/createModel.pl -m hg19
perl ../bin/createFakeSequence.pl -m hg19 -s 1Mb -o fake.fa
```

The download process is too slow with their command
I will download my own sequences and annotations to create a model:
Currently waiting for the files to download. After, need to choose which I will be using. These are the files that they meant to use in their autmatic function:

What files get downloaded when creating that model automatically?
```bash
cat ../tools/Garlic-master/bin/createModel.pl | grep "files{'hg19'}"
```
Result:
  $files{'hg19'}{'FAS'} = 'chromFa.tar.gz';
  #$files{'hg19'}{'RMA'} = 'chromOut.tar.gz';
  $files{'hg19'}{'RMA'} = 'hg19/RepeatMasker-rm405-db20140131/hg19.fa.align.gz';
  $files{'hg19'}{'TRF'} = 'chromTrf.tar.gz';
  $files{'hg19'}{'GEN'} = 'ensGene.txt.gz';

In artifical_seqs folder:
perl ../tools/Garlic-master/bin/createModel.pl -m hg19_chr1 -f ./seqs_for_model/chr1.fa -r hg19.chromOut/1/chr1.fa.out -t  -g Genes.table
????

Im not sure if this works even because it needs a repbase consensus and i cant download it. Let's try to do it on real hg19 sequences masked with RepeatMasker and obtain false positives, false negatives, true pisitive and true negatives that way

Update! I found a small embl repbase file that has library of repeats for Dfam. Not sure if that's what it asked for but still. Might give it a try
CITATION

Realistic artificial DNA sequences as negative controls for computational genomics.
Caballero J, Smit AF, Hood L, Glusman G.
Nucl. Acids Res. 2014
doi: 10.1093/nar/gku356 
drie
