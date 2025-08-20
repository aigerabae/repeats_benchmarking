This highlight the work I did to do a benchmarking test on existing software to identify and mask repeats

Key steps for benchmarking:
1. Define the task: virus detection, selection inference, taxonomic assignment, etc.
2. Select test datasets: simulated (ground truth known), real-world (biological complexity).
3. Choose toolset: relevant, baseline or newly developed tools.
4. Establish evaluation metrics: accuracy, false discovery rate, runtime, parameter sensitivity.
5. Visualize results: ROC curves, barplots, runtime vs. accuracy trade‑offs.
6. Assess parameter optimization: default vs. fine‑tuned thresholds.
7. Ensure reproducibility: provide code, containerized environments, public datasets.

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


Important:
1. Include a comprehensive tool list and log excluded tools.
2. Document data preparation thoroughly.
3. Choose proper evaluation metrics and share them as reusable scripts.
4. Perform parameter optimization to fairly assess tool performance.
5. Summarize tool features and provide commands and installation instructions.
6. Unify output formats for easier comparison.
7. Share all benchmarking data and scripts via user-friendly interfaces.
