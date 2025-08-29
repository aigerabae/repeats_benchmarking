Creating model on hg19 using garlic:
```bash
perl ../tools/Garlic-master/bin/createModel.pl -m hg19
perl ../tools/Garlic-master/bin/createFakeSequence.pl -m hg19 -s 1Mb -o fake.fa
```

The download process is too slow with their command
I will download my own sequences and annotations to create a model:
Currently waiting for the files to download. After, need to choose which I will be using. These are the files that they meant to use in their autmatic function:
(base) aygera@aygera-HP-Z6-G4-Workstation:~/biostar/RN/repeats_benchmarking/simulated_seq$ cat ../tools/Garlic-master/bin/createModel.pl | grep "files{'hg19'}"
  $files{'hg19'}{'FAS'} = 'chromFa.tar.gz';
  #$files{'hg19'}{'RMA'} = 'chromOut.tar.gz';
  $files{'hg19'}{'RMA'} = 'hg19/RepeatMasker-rm405-db20140131/hg19.fa.align.gz';
  $files{'hg19'}{'TRF'} = 'chromTrf.tar.gz';
  $files{'hg19'}{'GEN'} = 'ensGene.txt.gz';

perl ../tools/Garlic-master/bin/createModel.pl -m hg19_chr1 -f chr1.fa -r hg19.chromOut/1/chr1.fa.out -t  -g Genes.table
????
CITATION

Realistic artificial DNA sequences as negative controls for computational genomics.
Caballero J, Smit AF, Hood L, Glusman G.
Nucl. Acids Res. 2014
doi: 10.1093/nar/gku356 
