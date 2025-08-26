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
