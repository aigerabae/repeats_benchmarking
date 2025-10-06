Running benchmarking using maskscomp in TR:
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

Result of benchmarking using TR maskscomp:
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
