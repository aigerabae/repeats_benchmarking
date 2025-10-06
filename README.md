This highlight the work I did to do a benchmarking test on existing software to identify and mask repeats
-----
In the mid 1960's scientists discovered that many genomes contain stretches of highly repetitive DNA sequences ( see Reassociation Kinetics Experiments, and C-Value Paradox ). These sequences were later characterized and placed into five categories:

- Simple Repeats - Duplications of simple sets of DNA bases (typically 1-5bp) such as A, CA, CGG etc.
- Tandem Repeats - Typically found at the centromeres and telomeres of chromosomes these are duplications of more complex 100-200 base sequences.
- Segmental Duplications - Large blocks of 10-300 kilobases which are that have been copied to another region of the genome.
- Interspersed Repeats
  * Processed Pseudogenes, Retrotranscripts, SINES - Non-functional copies of RNA genes which have been reintegrated into the genome with the assitance of a reverse transcriptase.
  * DNA Transposons -
  * Retrovirus Retrotransposons -
  * Non-Retrovirus Retrotransposons ( LINES ) -

Currently up to 50% of the human genome is repetitive in nature and as improvements are made in detection methods this number is expected to increase.

-----
Key steps for benchmarking:
1. Define the task: virus detection, selection inference, taxonomic assignment, etc.
2. Select test datasets: simulated (ground truth known), real-world (biological complexity).
3. Choose toolset: relevant, baseline or newly developed tools.
4. Establish evaluation metrics: accuracy, false discovery rate, runtime, parameter sensitivity.
5. Visualize results: ROC curves, barplots, runtime vs. accuracy trade‑offs.
6. Assess parameter optimization: default vs. fine‑tuned thresholds.
7. Ensure reproducibility: provide code, containerized environments, public datasets.

-----

Core Components of Benchmarking Studies
1) Gold Standard Data
2) Evaluation Metrics
    a) Accuracy (precision, recall, F1 score)
    b) Specificity, sensitivity
    c) Runtime (CPU time), memory (RAM)
    d) Pareto frontier for multi-objective performance ranking
         - The Pareto frontier is the set of tools that are not outperformed in all evaluation metrics by any other tool.
4) Parameter Optimization
    a) Tuning parameters is essential but computationally expensive.
    b) Many benchmarking studies still rely on default parameters, which can be suboptimal.

-----

Important:
1. Include a comprehensive tool list and log excluded tools.
2. Document data preparation thoroughly.
3. Choose proper evaluation metrics and share them as reusable scripts.
4. Perform parameter optimization to fairly assess tool performance.
5. Summarize tool features and provide commands and installation instructions.
6. Unify output formats for easier comparison.
7. Share all benchmarking data and scripts via user-friendly interfaces.

-----

Confusion matrix:
|                      | **Predicted: Positive** | **Predicted: Negative** |
| -------------------- | ----------------------- | ----------------------- |
| **Actual: Positive** | True Positive (TP)      | False Negative (FN)     |
| **Actual: Negative** | False Positive (FP)     | True Negative (TN)      |



| **Metric**                                 | **Formula**                                     | **What it tells you**                          |
| ------------------------------------------ | ----------------------------------------------- | ---------------------------------------------- |
| **Precision**                              | TP / (TP + FP)                                  | How many predicted positives were correct      |
| **Recall (Sensitivity)**                   | TP / (TP + FN)                                  | How many real positives were found             |
| **Specificity**                            | TN / (TN + FP)                                  | How many real negatives were correctly avoided |
| **Accuracy**                               | (TP + TN) / (TP + TN + FP + FN)                 | Overall correctness of predictions             |
| **F1 Score**                               | 2 × (Precision × Recall) / (Precision + Recall) | Balance between precision and recall           |
| **Matthews Correlation Coefficient (MCC)** | A correlation-like score between -1 and 1       | Best when classes are imbalanced               |

- Always report multiple metrics, not just accuracy—because one metric (like accuracy) can be misleading, especially with unbalanced datasets.
- Use F1-score or MCC for balanced performance insights.
- Report performance across different thresholds (ROC, PR curves), not just at one fixed cutoff.
- If the tool returns continuous predictions (like probabilities), plot:
        - ROC curve (True Positive Rate vs False Positive Rate)
        - Precision-Recall curve (Precision vs Recall)

This helps show performance over a range of sensitivity/specificity trade-offs.

-----

To benchmark tools properly:
- Run them on a dataset with known ground truth.
- Fill in the confusion matrix for each tool.
- Calculate multiple metrics from the matrix.
- Compare across tools using these metrics.
- Prefer tools on the Pareto frontier (good balance between metrics like F1, runtime, etc.).

-----
Computational cost:
| **Component of Computational Cost** | **What It Means**                                    | **How to Measure It**                                                      | **Example**                                                          |
| ----------------------------------- | ---------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Execution Time** (Wall Time)      | Total time from start to finish (including I/O)      | `time` or `/usr/bin/time -v`<br>Cluster job logs (e.g., Slurm)             | Tool A took **2 hours** to finish annotating the genome              |
| **CPU Time**                        | Actual time the CPU worked on the task               | `/usr/bin/time -v` → "User time" and "System time"<br>or job log summary   | Tool B used **5 hours CPU time** (across 4 cores)                    |
| **Maximum RAM Usage**               | Peak memory used during execution                    | `/usr/bin/time -v` → “Maximum resident set size”<br>Cluster memory logs    | Tool C required **42 GB RAM** at its peak                            |
| **Number of Threads / Cores Used**  | Degree of parallelism the tool supports              | Tool documentation + resource monitoring during runtime                    | Tool D used **8 threads** for faster performance                     |
| **Disk Usage**                      | Temporary and output storage space required          | Measure input/output file size + disk usage during run (e.g., `du -sh ./`) | Tool E created **90 GB** of temporary output files                   |
| **Installation Burden**             | Time and effort required to install all dependencies | Manual notes or user experience<br>(Optional rating: Easy/Moderate/Hard)   | Tool F needed Conda + 5 external packages, took **1 hour to set up** |
| **Scalability**                     | How well the tool handles larger datasets            | Test with small vs large input and compare resource scaling                | Tool G crashed on whole genome but worked on 1 chromosome            |


-----
How do we choose gold standard data in this case?
- use hg19 masked repeats? they use repeatmasker but i didn't intend to include it as RepeatModeler is based on it

Plan:
The input is a .out file produced by RepeatMasker when using a tool-generated repeat library to mask a curated reference genome.
Eukaryotic genomes contain complex structure and tandem repeats, which may result in false positives for TE discovery software. We assessed the false positive rate of RepeatModeler2 by running it on artificially generated genomes devoid of TEs simulated by GARLIC (43) for D. melanogaster and D. rerio. GARLIC generates background sequences with realistic complexity, isochore structure, and tandem repeat content similar to the modeled genome. RepeatModeler2 produced only one false positive family on the D. melanogaster artificial genome and five false positive families on the D. rerio artificial genome. No false positive families were produced from the LTR module. These results suggest that the rate of false positives generated by RepeatModeler2 is very low.(benchmarking done on RM1 vs RM2)



Choosing the software to use for benchmarking:
Task: provide a critical comparative assessment of the developed tool relative to existing, widely used tools such as RepeatModeler, RepeatExplorer, RepeatScout, PILER, Tandem Repeats Finder, RECON, and others. A thorough benchmarking analysis—demonstrating where this method improves upon or complements established tools in terms of algorithmic performance, repeat type detection, accuracy, and computational efficiency—is essential.

Including:
RepeatModeler (includes RepeatScout and RECON, as well as LTR_retriever and LTRharvest) ✅
RepeatExplorer ✅
PILER - wasn't updated since 2005 https://academic.oup.com/bioinformatics/article/21/suppl_1/i152/202952?login=true
Tandem Repeats Finder - only for tandem repeats

Tasks:
- find other software to use for comparison
- choose sequence to run (needs to be raw and assembled)
- write script to compare output of RepeatMasker with other software
- Describe additional features of each software
- Record time it takes for each software to run


ool facts I found while reading about repeats:

For instance, about 50% of the human genome consists of repeats, while roughly 4% of human genes harbor transposable elements in their protein-coding regions. Because many of these repeats (~89.5%) are located within introns, they have been erroneously assumed to be non-functional. However, increasing research indicates the significant impacts that repeats in coding and noncoding regions can have on evolution, gene expression regulation, and variation induction. For example, when repeats are present in the coding region they get translated canonically. Not only can non-coding repeats be translated by a non-canonical mechanism, but even the telomeric repeat RNAs can get translated. Moreover, recent studies have shown that such repeats are closely related to a variety of diseases, such as genetic disorders (e.g., Hemophilia), neurological diseases (e.g., poly-Q diseases), and cancers (e.g., endometrial, stomach and colorectal cancers)
In genetics, tandem repeats occur in DNA when a pattern of one or more nucleotides is repeated and the repetitions are directly adjacent to each other, e.g. ATTCG ATTCG ATTCG, in which the sequence ATTCG is repeated three times.

Here’s a comprehensive comparison between **RepeatModeler** and **RepeatExplorer**, based on documentation and standard bioinformatics knowledge:

---

## 🧩 FUNCTIONALITY

| Feature                                   | **RepeatModeler**                                    | **RepeatExplorer**                                                        |
| ----------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------- |
| **Goal**                                  | De novo identification and classification of repeats | De novo identification, quantification, and annotation of repeats         |
| **Repeat types**                          | All repeat families (transposons, satellites, etc.)  | Mainly focused on high-copy repeats, including satellites and LTRs        |
| **Repeat masking support**                | Yes — integrates with **RepeatMasker**               | **No direct masking**, but produces sequences usable by RepeatMasker      |
| **Quantification of genome proportion**   | Partial (inferred)                                   | Yes — calculates how much of genome each repeat occupies                  |
| **Graph-based clustering**                | No                                                   | Yes — unique approach using graph layout of read similarity               |
| **Satellite-specific detection (TAREAN)** | No                                                   | Yes — specialized module for tandem repeat analysis                       |
| **Custom repeat database annotation**     | Yes — uses RepeatClassifier, integrates with RepBase | Yes — matches clusters against REXdb, rDNA, and optional custom databases |

---

## 📥 INPUT FORMAT

| Format               | **RepeatModeler**                                 | **RepeatExplorer**                                           |
| -------------------- | ------------------------------------------------- | ------------------------------------------------------------ |
| **Input type**       | Assembled genome in FASTA format                  | Unassembled genomic reads (FASTQ or FASTA)                   |
| **Genome size**      | Suitable for assembled **draft/finished** genomes | Suitable for **large genome surveys** or unassembled genomes |
| **Paired-end reads** | Not used                                          | Yes — improves clustering with paired-end reads              |

---

## 📤 OUTPUT FORMAT

| Output type                    | **RepeatModeler**                 | **RepeatExplorer**                                              |
| ------------------------------ | --------------------------------- | --------------------------------------------------------------- |
| **Repeat library**             | FASTA file of consensus sequences | FASTA file of consensus sequences (contigs.fasta, TAREAN ranks) |
| **Classification**             | Yes — RepeatClassifier            | Yes — similarity hits + annotation                              |
| **RepeatMasker-ready library** | Yes                               | Indirectly (can export sequences to use with RM)                |
| **HTML reports**               | No                                | Yes — Interactive cluster and supercluster reports              |
| **Graph visualization**        | No                                | Yes — detailed read similarity graphs for each cluster          |
| **Genome proportion table**    | No direct output                  | Yes — CLUSTER\_TABLE.csv and SUPERCLUSTER\_TABLE.csv            |

---

## 🧪 ADDITIONAL FUNCTIONS

| Function                              | **RepeatModeler**               | **RepeatExplorer**                                        |   
| ------------------------------------- | ------------------------------- | --------------------------------------------------------- | 
| **Integration with RepeatMasker**     | Full integration                | Not directly integrated, but outputs compatible sequences |   
| **Tandem repeat annotation (TAREAN)** | ❌ Not available                 | ✅ Yes, unique strength                                    |   
| **LTR structure detection**           | Partial (via LTRHarvest in RM2) | Yes, built-in LTR detection with PBS check                |   
| **Paired-read coherence (P index)**   | ❌                               | ✅ Yes                                                     |   

---

## 🏛 YEAR OF CREATION & NOTABLE POINTS

| Feature                 | **RepeatModeler**                                 | **RepeatExplorer**                                  |
| ----------------------- | ------------------------------------------------- | --------------------------------------------------- |
| **First release**       | \~2008–2009 (RepeatModeler 1), RM2 in 2020        | \~2013 (TAREAN added in 2017)                       |
| **Developed by**        | Institute for Systems Biology (ISB)               | Institute of Plant Molecular Biology, Czech Academy |
| **Notable strength**    | Gold standard for de novo repeat library building | Best for repeat profiling in unassembled genomes    |
| **Scalability**         | Works well on complete genomes                    | Ideal for **low-coverage surveys**, fast to run     |
| **Graph-based novelty** | ❌ Traditional homology/structure based            | ✅ Graph-based clustering is a key innovation        |

---

## ✅ ADVANTAGES AND ❌ DISADVANTAGES

### 🔹 **RepeatModeler**

**Advantages:**

* Works on complete assemblies
* High-quality consensus sequences
* Integrates well with RepeatMasker
* Broad repeat classification

**Disadvantages:**

* Requires a full genome assembly
* Doesn’t quantify genome proportion
* No visualization or tandem repeat-specific features

---

### 🔸 **RepeatExplorer**

**Advantages:**

* Works directly on raw reads (no assembly required)
* Estimates abundance of repeat families
* Graph-based clustering reveals relationships
* TAREAN module gives rich satellite repeat analysis
* Interactive HTML reports for exploration

**Disadvantages:**

* Doesn’t produce a masked genome
* Not designed for building full repeat libraries for RepeatMasker
* Slower on huge datasets or very complex genomes

---

## 🧠 Summary

| Use Case                                     | Recommended Tool          |
| -------------------------------------------- | ------------------------- |
| You have an **assembled genome**             | ✅ RepeatModeler           |
| You have only **reads / no assembly**        | ✅ RepeatExplorer          |
| You need a **RepeatMasker-ready library**    | ✅ RepeatModeler           |
| You want **repeat quantification**           | ✅ RepeatExplorer          |
| You’re studying **tandem/satellite repeats** | ✅ RepeatExplorer (TAREAN) |
| You want **graph-based visualization**       | ✅ RepeatExplorer          |

---
