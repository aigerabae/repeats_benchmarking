The following software is included in the Dfam TE Tools container (version 1.93):

RepeatModeler	2.0.7	https://github.com/Dfam-consortium/RepeatModeler
RepeatMasker	4.2.0	http://www.repeatmasker.org/RMDownload.html
coseg	0.2.3	http://www.repeatmasker.org/COSEGDownload.html
RMBlast	2.14.1	http://www.repeatmasker.org/RMBlast.html
HMMER	3.4	http://hmmer.org/
TRF	4.09.1	https://github.com/Benson-Genomics-Lab/TRF
RepeatScout	1.0.7	https://github.com/Dfam-consortium/RepeatScout
RECON	1.08	http://www.repeatmasker.org/RepeatModeler/RECON-1.08.tar.gz
cd-hit	4.8.1	https://github.com/weizhongli/cdhit
genometools	1.6.4	https://github.com/genometools/genometools
LTR_retriever	2.9.0	https://github.com/oushujun/LTR_retriever/
MAFFT	7.471	https://mafft.cbrc.jp/alignment/software/
NINJA	1.00-cluster_only	https://github.com/TravisWheelerLab/NINJA
UCSC utilities*	v413	http://hgdownload.soe.ucsc.edu/admin/exe/
RepeatAfterMe	0.0.7	https://github.com/Dfam-consortium/RepeatAfterMe
* Selected tools only: faToTwoBit, twoBitInfo, twoBitToFa

I will be using for comparison:
1) RepeatModeler
2) RepeatScout ?? old and included in RM
3) RECON ?? old and included in RM

How to do it:
1) RepeatModeler
singularity exec --bind ${PWD}:/data/ dfam-tetools-latest.sif BuildDatabase -name genome1 13.txt
singularity exec --bind ${PWD}:/data/ dfam-tetools-latest.sif RepeatModeler -database genome1 --threads 20

Finished running in 4 minutes (even though I ran it after I intiialized RepeatExplorer, and it finished earlier). Saved results into a folder with unique name so different runs wouldn't get intermixed. Accepst assembled reads, Doesn't require a specific extension.
