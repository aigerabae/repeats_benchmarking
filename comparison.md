Here’s a comprehensive comparison between **RepeatModeler** and **RepeatExplorer**, based on your documentation and standard bioinformatics knowledge:

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

| Function                              | **RepeatModeler**               | **RepeatExplorer**                                        |   |       |   |       |
| ------------------------------------- | ------------------------------- | --------------------------------------------------------- | - | ----- | - | ----- |
| **Integration with RepeatMasker**     | Full integration                | Not directly integrated, but outputs compatible sequences |   |       |   |       |
| **Tandem repeat annotation (TAREAN)** | ❌ Not available                 | ✅ Yes, unique strength                                    |   |       |   |       |
| **LTR structure detection**           | Partial (via LTRHarvest in RM2) | Yes, built-in LTR detection with PBS check                |   |       |   |       |
| **Paired-read coherence (P index)**   | ❌                               | ✅ Yes                                                     |   |       |   |       |
| \*\*Graph analysis (C index,          | V                               | ,                                                         | E | )\*\* | ❌ | ✅ Yes |

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

Let me know if you’d like a **flowchart or cheat sheet PDF** of this comparison!
