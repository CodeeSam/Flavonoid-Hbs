# Generative design and structure-based prioritisation of flavonoid-inspired haemoglobin ligand candidates

This repository accompanies a study that combines focused molecular generation with structure-based screening at a carbonmonoxy haemoglobin (HbA) site. The primary generator is a compact SMILES transformer trained on a flavonoid-like corpus. The study compares the generator with model-free baselines and fine-tuned ChemGPT-19M at matched sampling budgets.

## Primary generator results

The corpus contains 1,689 molecules, split by scaffold into 1,353 training, 188 validation and 148 test molecules. The selected checkpoint is from epoch 25.

| Split | Cross-entropy | Perplexity |
| --- | ---: | ---: |
| Validation | 0.551936 | 1.736611 |
| Scaffold-held-out test | 0.460867 | 1.585447 |

Of 30,000 generation attempts, 21,715 yielded valid molecules. Canonicalisation yielded 12,436 distinct valid structures. Chemical filtering retained 2,371 candidates for structure-based screening.

## Repository contents

| Location | Contents |
| --- | --- |
| [`data/`](data/) | Source and curated molecules, scaffold splits and augmented training strings |
| [`models/`](models/) | Primary checkpoint, SMILES tokeniser and training history |
| [`notebooks/`](notebooks/) | Generation and filtering notebook, and held-out evaluation summary |
| [`outputs/`](outputs/) | Generated molecules, filtering results, figures and run reports |
| [`sbdd_candidates/`](sbdd_candidates/) | 2,371 screening candidates in CSV, XLSX, SMI and SDF formats |
| [`supplementary_materials/`](supplementary_materials/) | Supplementary Tables S1–S13 |

The [run summary](outputs/reports/RUN_SUMMARY.md) lists the primary generation outputs. The [evaluation report](outputs/reports/heldout_evaluation.json) records the checkpoint metrics and loss calculation. Software dependencies are listed in [`environment.yml`](environment.yml) and [`requirements.txt`](requirements.txt).
