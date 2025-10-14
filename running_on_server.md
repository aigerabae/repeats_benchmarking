To connect from files:
```bash
ssh://prom@10.1.131.183
```

To connect from command line:
```bash
ssh prom@10.1.131.183
```

Password: GS_Flx_2025
Need to choose a partition with sufficient memory - done; will be working in prom@10.1.131.183:/data/rkalendar/

I put all software in soft folder in rkalendar
For installation it asks absolute paths to those (important - no / in the end!):
- folder with fdam library (may find automatically)
```bash
/data/rkalendar/soft/tools/RepeatMasker/RepeatMasker/Libraries
```
- TRF executable (if it doesn't see it need to chmod +X it) -
```bash
/data/rkalendar/soft/tools/RepeatMasker/trf409.legacylinux64
```
- Rmblast address (specifically in the bin of it)
```bash
/data/rkalendar/soft/tools/RepeatMasker/rmblast-2.14.1+-x64-linux/rmblast-2.14.1/bin
```

I set up RepeatMasker and to add it to path temporarily run this:
```bash
export PATH=/data/rkalendar/soft/tools/RepeatMasker/RepeatMasker:$PATH
```

```bash
for element in ../genomes/T2T-CHM13v2.0/*; do
    filename=$(basename "$element")
    RepeatMasker -species Homo_sapiens -pa 24 -xsmall -gff -dir . "$element"
done
```

It doesn't run. Problem is, it didn't configure correctly because it needs GLIBC_2.33 and my system has GLIBC 2.31.
I tried installing GLIBC 2.33 with conda
```bash
conda install vikky34v::glibc
```

And now
```bash
ldd --version
```

Gives: ldd (GNU libc) 2.33

But RepeatMasker still doesn't run, now with a different error:
(biostar) prom@PCA100416:/data/rkalendar/tests$ RepeatMasker 13.txt 
RepeatMasker version 4.2.1
Search Engine: NCBI/RMBLAST [ /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by /data/rkalendar/soft/tools/RepeatMasker/rmblast-2.14.1+-x64-linux/rmblast-2.14.1/bin/rmblastn) ]
Could not execute famdb.py using: /data/rkalendar/soft/tools/RepeatMasker/RepeatMasker/famdb.py -i /data/rkalendar/soft/tools/RepeatMasker/RepeatMasker/Libraries/famdb info 

I attempted to fix this problem by going to that folder and 
```bash
chmod +x famdb.py
```

But it didn't work.
