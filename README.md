# Flavonoid-inspired generative design and SBDD candidate library for haemoglobin modulation

This repository contains the **frozen data, model checkpoint, source notebooks, generated molecular library, and reproducibility utilities** supporting the manuscript:

> **Structure-Based Prioritization of De Novo Flavonoid-Inspired Candidate Haemoglobin S Modulators Using Generative Molecular Design**

The generative model is a compact decoder-only SMILES transformer used **upstream as a focused molecule-supply tool**.

## What is reproducible here

The repository supports reproduction and audit of the open generative/medicinal-chemistry portion of the study:

- molecular corpus and scaffold-aware train/validation/test partitions;
- randomized-SMILES training set;
- tokenizer and trained checkpoint;
- training history and archived run configuration;
- scaffold-held-out test loss/perplexity evaluation;
- 30,000 generated SMILES and generation-quality metrics;
- medicinal-chemistry filtering and scaffold/chemical-space summaries; and
- the full **2,371-molecule SBDD-ready candidate library** supplied to the downstream structure-based workflow.

## Repository layout

```text
data/                 raw, splits and curated data
models/               Model checkpoint, smiles tokenizer and training history
notebooks/            Main generation/filtering notebook + held-out test evaluation
outputs/              figures, filtered candidates, generation, reports and scaffold outputs
sbdd_candidates/       Complete 2,371-compound candidate library (CSV/XLSX/SMI/SDF)
supplementary materials/ supplementary tables 1-13
downstream_results/    Machine-readable reported docking, PLIP and ADMET tables
```

## Quick start

```bash
conda env create -f environment.yml
conda activate flavonoid_hbs_sbdd
python scripts/validate_archive.py
python scripts/evaluate_heldout_test.py
# Or use the independent CPU implementation explicitly:
python scripts/evaluate_heldout_test.py --backend numpy
# Optional regeneration of manuscript plots and the scaffold structure figure:
python scripts/make_manuscript_figures.py
python scripts/make_scaffold_figure.py
```

Expected held-out evaluation:

```text
checkpoint_epoch=25
validation_loss=0.551936
validation_perplexity=1.736611
test_molecules=148
test_loss=0.460867
test_perplexity=1.585447
```

## Software environment

The archived run report records:

- Python 3.12.12
- PyTorch 2.10.0+cu128
- RDKit 2026.03.1
- CUDA-enabled Kaggle runtime
- random seed 42 for Python, NumPy and PyTorch

## Citation

See `CITATION.cff`.

## License

No software/data license is asserted in this package. Add the license selected by the authors before or after public release if redistribution/reuse permissions are to be granted explicitly.