# Evaluating the Scalability of Topology-Representing Networks

Code for an MSc dissertation testing whether a Topology-Representing
Network (TRN; Martinetz & Schulten, 1994) preserves the relational
structure of its input as dataset size, ambient dimensionality, prototype
count, and structural type vary: an empirical test of Moisl's (2025)
proposal that TRNs implement intrinsic lexical intentionality through
topology-preserving representation.

## Contents

- `trn_experiments.ipynb` - the full pipeline as a single annotated
  notebook: data generation and loading (Module 1), the TRN
  implementation from scratch (Module 2), representation extraction
  (Module 3), the metric suite including the primary Option-B
  graph-path distance (Module 4), the experiment harness (Module 5),
  analysis and statistics including the aligned-rank-transform ANOVA
  (Module 6), and the orthonormal-embedding control (Module 8).
- `generate_figures.py` - builds the dissertation's four figures from
  the saved results files.
- `requirements.txt` - dependencies (Colab runtime versions).

## Reproducing

All saved experiment outputs are in `results/`. To reproduce the
analysis: copy the contents of `results/` to Google Drive at
`MyDrive/dissertation/`, open the notebook in Google Colab, and
Run all. Every reported statistic is then regenerated from the saved
outputs: the aligned-rank-transform ANOVA cell validates its own
output against the values reported in the dissertation, and the
four figures are rebuilt by the figure cells.

All stochastic components are governed by fixed seeds from
pre-specified lists. The five sweep-execution cells (the main
synthetic, MNIST, and word-embedding arms, and the two control
sweeps) are commented out with provenance notes: they were executed
once to produce the files in `results/`, take substantial time to
re-run, and overwrite the saved outputs. Uncomment to regenerate
everything from scratch.

One file is deliberately absent: `results_saturation.csv` was lost
to an overwrite (documented in the guarded saturation cell) and the
corresponding analysis is reported descriptively in the dissertation.

## Data

- Synthetic linear manifolds are generated in the notebook (seeded).
- MNIST is fetched via `sklearn.datasets.fetch_openml`.
- BERT word embeddings are extracted from `bert-base-uncased`
  (Hugging Face `transformers`); the notebook caches the extracted
  embedding matrix to Drive on first run.
