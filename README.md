# Xanthomonas-genome-assembly-pipeline

This repository contains the methods, scripts, and environments used for genome assembly and plasmid identification.

## Contents
- `genome_assembly_methods.ipynb` — Jupyter notebook with all commands and workflow.
- `genome_assembly_environment.yml` — Conda environment for most tools (Python 3.10).
- `ragout_env.yml` — Separate Conda environment for Ragout (Python 2.7).

## Setup Instructions

### 1. Install Conda (if not already installed)
We recommend [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

### 2. Create environments
```bash
# Main environment
conda env create -f genome_assembly_environment.yml
conda activate genome_assembly

# Ragout environment (used only when running Ragout)
conda env create -f ragout_env.yml
conda activate ragout_env

### 3. Run the notebook
Start Jupyter Lab or Notebook in the repository folder:
```bash
jupyter lab
jupyter notebook


