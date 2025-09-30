### Chapter 1: What's RepeatMasker? Installation
What does RepeatMasker do?
RepeatMasker is a program that screens DNA sequences for interspersed repeats and low complexity DNA sequences. The output of the program is a detailed annotation of the repeats that are present in the query sequence as well as a modified version of the query sequence in which all the annotated repeats have been masked (default: replaced by Ns).

Sequence comparisons in RepeatMasker are performed by the program cross_match, an efficient implementation of the Smith-Waterman-Gotoh algorithm developed by Phil Green.

Repeatmasker relies on evidence or pre-determined repeat libraries for organisms

It is used to mask repeats in canonical human assemblies like hg19

Prerequisites
- Unix system with perl 5.8.0 or higher installed ✅
- Python 3 and the h5py python library. ✅
RMBlast ( NCBI Blast modified for use with RepeatMasker/RepeatModeler ) please go to our download page: http://www.repeatmasker.org/rmblast. It is highly recommended to use 2.13.0 or higher.
For ABBlast/WUBlast go to [ NOTE: Rights to BLAST 2.0 (WU-BLAST) have been acquired by Advanced Biocomputing, LLC. http://blast.advbiocomp.com/licensing/ RepeatMasker 3.2.8 and above fully support both variants ]
TRF - Tandem Repeat Finder, G. Benson et al. ✅ - downloaded, not installed
Dfam Repeat Database ✅

To download dfam library:
```bash
curl -s https://www.dfam.org/releases/current/families/FamDB/ | \
grep -oP 'href="\K[^"]+' | \
grep -v '/$' | \
sed 's|^|https://www.dfam.org/releases/current/families/FamDB/|' | \
while read url; do
  filename=$(basename "$url")
  if [ ! -f "$filename" ]; then
    echo "$url"
  fi
done | xargs -n 1 -P 10 wget -c
```

I saved all dfam libraries in tar.gz file just in case and started unzipping them separately. It's still running. I put the unzipped folder in the Libraries/famdb folder (replacing its original content). Once unzipping it is done installation of RepeatMasker should be successful

In RepeatMasker directory (inside RepeatMasker root rectory which I created and which contains other prerequisites)
```bash
perl ./configure
```

For installation it asks
- folder with fdam library (finds automatically)
- TRF executable (if it doesn't see it need to chmod +X it)
- Rmblast address (specifically in the bin of it)

After I did that it should work fine. I added it to path. Let's test:
```bash
RepeatMasker 13.txt
```
produced some output. yay!


---
# Chapter 2: Drosophila Melanogaster A4
After I mask it I will compare the output with info here:
https://www.repeatmasker.org/species/dm.html
