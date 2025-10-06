Running benchmarking using maskscomp in TR:
I pooled all masks into maskcomp folder and named them appropriately. Using comparison function:
runfiles.txt:
```text
tr.msk	rexplorer.msk
tr.msk	rmasker.msk  
tr.msk	rmodeler.msk  
tr.msk  wmasker.msk
rexplorer.msk  rmasker.msk  
rexplorer.msk  rmodeler.msk  
rexplorer.msk  wmasker.msk
rmasker.msk  rmodeler.msk
rmasker.msk  wmasker.msk
rmodeler.msk  wmasker.msk
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


Sequence length (nt): 144,134,966
(1) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(2) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 34,207,658 : 23.73%
(2) Masked (nt): 32,995,676 : 22.89%
Overlapping masking (nt): 31,560,906 : 92.26%
Overlapping coverage at sequence level = 21.90%
(1) Different mask not overlap (nt): 2,646,752 : 7.74%
(2) Different mask not overlap (nt): 1,434,770 : 4.35%
144,134,966	23.73	22.89	92.26	21.90	7.74	4.35


Sequence length (nt): 144,134,966
(1) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(2) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 34,207,658 : 23.73%
(2) Masked (nt): 34,016,908 : 23.60%
Overlapping masking (nt): 32,929,423 : 96.26%
Overlapping coverage at sequence level = 22.85%
(1) Different mask not overlap (nt): 1,278,235 : 3.74%
(2) Different mask not overlap (nt): 1,087,485 : 3.20%
144,134,966	23.73	23.60	96.26	22.85	3.74	3.20


Sequence length (nt): 144,134,966
(1) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 34,207,658 : 23.73%
(2) Masked (nt): 36,769,731 : 25.51%
Overlapping masking (nt): 21,180,296 : 57.60%
Overlapping coverage at sequence level = 14.69%
(1) Different mask not overlap (nt): 13,027,362 : 38.08%
(2) Different mask not overlap (nt): 15,589,435 : 42.40%
144,134,966	23.73	25.51	57.60	14.69	38.08	42.40


Sequence length (nt): 144,134,966
(1) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(2) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 32,995,676 : 22.89%
(2) Masked (nt): 34,016,908 : 23.60%
Overlapping masking (nt): 31,701,259 : 93.19%
Overlapping coverage at sequence level = 21.99%
(1) Different mask not overlap (nt): 1,294,417 : 3.92%
(2) Different mask not overlap (nt): 2,315,649 : 6.81%
144,134,966	22.89	23.60	93.19	21.99	3.92	6.81


Sequence length (nt): 144,134,966
(1) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 32,995,676 : 22.89%
(2) Masked (nt): 36,769,731 : 25.51%
Overlapping masking (nt): 19,387,419 : 52.73%
Overlapping coverage at sequence level = 13.45%
(1) Different mask not overlap (nt): 13,608,257 : 41.24%
(2) Different mask not overlap (nt): 17,382,312 : 47.27%
144,134,966	22.89	25.51	52.73	13.45	41.24	47.27


Sequence length (nt): 144,134,966
(1) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequenc
(1) Masked (nt): 34,016,908 : 23.60%
(2) Masked (nt): 36,769,731 : 25.51%
Overlapping masking (nt): 20,992,025 : 57.09%
Overlapping coverage at sequence level = 14.56%
(1) Different mask not overlap (nt): 13,024,883 : 38.29%
(2) Different mask not overlap (nt): 15,777,706 : 42.91%
144,134,966	23.60	25.51	57.09	14.56	38.29	42.91
```
