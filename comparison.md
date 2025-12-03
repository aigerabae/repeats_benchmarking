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
java -jar ~/biostar/RN/repeats_benchmarking/tools/TotalRepeats/dist/TotalRepeats.jar runfiles.txt -maskscomp > result.txt
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



New results (only sees 45 mln/145 mln bases for all of them):
Overlapping sequence length (nt): 23,611,144 (47,396,754/47,396,717)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotFiles processed successfully.
uence coverage by repeats = 13.37%
(2) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,484,224 : 7.35%
(2) Masked (nt): 3,984,229 : 8.41%
Overlapping masking (nt): 2,739,877 : 68.77%
Overlapping coverage at sequence level = 11.60%
(1) Different mask not overlap (nt): 744,347 : 21.36%
(2) Different mask not overlap (nt): 1,244,352 : 31.23%
23611144	3484224	3984229	2739877	744347	1244352


Overlapping sequence length (nt): 23,611,144 (47,396,754/47,396,717)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 13.37%
(2) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,484,224 : 7.35%
(2) Masked (nt): 3,871,428 : 8.17%
Overlapping masking (nt): 2,619,385 : 67.66%
Overlapping coverage at sequence level = 11.09%
(1) Different mask not overlap (nt): 864,839 : 24.82%
(2) Different mask not overlap (nt): 1,252,043 : 32.34%
23611144	3484224	3871428	2619385	864839	1252043


Overlapping sequence length (nt): 23,611,144 (47,396,754/47,396,717)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 13.37%
(2) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,484,224 : 7.35%
(2) Masked (nt): 3,976,084 : 8.39%
Overlapping masking (nt): 2,725,564 : 68.55%
Overlapping coverage at sequence level = 11.54%
(1) Different mask not overlap (nt): 758,660 : 21.77%
(2) Different mask not overlap (nt): 1,250,520 : 31.45%
23611144	3484224	3976084	2725564	758660	1250520


Overlapping sequence length (nt): 23,611,144 (47,396,754/47,396,717)
(1) ./tr.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence TotalRepeats: Sequence coverage by repeats = 13.37%
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,484,224 : 7.35%
(2) Masked (nt): 5,445,861 : 11.49%
Overlapping masking (nt): 2,041,597 : 37.49%
Overlapping coverage at sequence level = 8.65%
(1) Different mask not overlap (nt): 1,442,627 : 41.40%
(2) Different mask not overlap (nt): 3,404,264 : 62.51%
23611144	3484224	5445861	2041597	1442627	3404264


Sequence length (nt): 23,611,144
(1) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(2) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,984,229 : 8.41%
(2) Masked (nt): 3,871,428 : 8.17%
Overlapping masking (nt): 3,715,454 : 93.25%
Overlapping coverage at sequence level = 15.74%
(1) Different mask not overlap (nt): 268,775 : 6.75%
(2) Different mask not overlap (nt): 155,974 : 4.03%
23611144	3984229	3871428	3715454	268775	155974


Sequence length (nt): 23,611,144
(1) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(2) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,984,229 : 8.41%
(2) Masked (nt): 3,976,084 : 8.39%
Overlapping masking (nt): 3,812,067 : 95.68%
Overlapping coverage at sequence level = 16.15%
(1) Different mask not overlap (nt): 172,162 : 4.32%
(2) Different mask not overlap (nt): 164,017 : 4.13%
23611144	3984229	3976084	3812067	172162	164017


Sequence length (nt): 23,611,144
(1) ./rexplorer.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,984,229 : 8.41%
(2) Masked (nt): 5,445,861 : 11.49%
Overlapping masking (nt): 2,447,916 : 44.95%
Overlapping coverage at sequence level = 10.37%
(1) Different mask not overlap (nt): 1,536,313 : 38.56%
(2) Different mask not overlap (nt): 2,997,945 : 55.05%
23611144	3984229	5445861	2447916	1536313	2997945


Sequence length (nt): 23,611,144
(1) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(2) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,871,428 : 8.17%
(2) Masked (nt): 3,976,084 : 8.39%
Overlapping masking (nt): 3,753,014 : 94.39%
Overlapping coverage at sequence level = 15.90%
(1) Different mask not overlap (nt): 118,414 : 3.06%
(2) Different mask not overlap (nt): 223,070 : 5.61%
23611144	3871428	3976084	3753014	118414	223070


Sequence length (nt): 23,611,144
(1) ./rmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,871,428 : 8.17%
(2) Masked (nt): 5,445,861 : 11.49%
Overlapping masking (nt): 2,299,617 : 42.23%
Overlapping coverage at sequence level = 9.74%
(1) Different mask not overlap (nt): 1,571,811 : 40.60%
(2) Different mask not overlap (nt): 3,146,244 : 57.77%
23611144	3871428	5445861	2299617	1571811	3146244


Sequence length (nt): 23,611,144
(1) ./rmodeler.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(2) ./wmasker.msk : CM008268.1 Drosophila melanogaster strain A4 chromosome X, whole genome shotgun sequence
(1) Masked (nt): 3,976,084 : 8.39%
(2) Masked (nt): 5,445,861 : 11.49%
Overlapping masking (nt): 2,411,783 : 44.29%
Overlapping coverage at sequence level = 10.21%
(1) Different mask not overlap (nt): 1,564,301 : 39.34%
(2) Different mask not overlap (nt): 3,034,078 : 55.71%
23611144	3976084	5445861	2411783	1564301	3034078


(1) Different mask not overlap (nt): 13,024,883 : 38.29%
(2) Different mask not overlap (nt): 15,777,706 : 42.91%
144,134,966	23.60	25.51	57.09	14.56	38.29	42.91
```
