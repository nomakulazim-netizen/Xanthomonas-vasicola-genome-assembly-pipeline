# Xanthomonas-genome-assembly-pipeline

This repository contains the methods, scripts, and environments used for genome assembly and plasmid identification.

## Contents
- `genome_assembly_methods.ipynb` — Jupyter notebook with all commands and workflow.
- `genome_assembly_environment.yml` — Conda environment for most tools (Python 3.10).
- `ragout_env.yml` — Separate Conda environment for Ragout (Python 2.7).
- `recipes/` — Ragout recipe files used in this study.

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
```

### 3. Input data
The raw Illumina reads used in this study are available in the NCBI Sequence Read Archive (SRA) under **[BioProject PRJNA1195417](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA1195417)**.  

Users should download the paired-end reads (R1 and R2) for each strain directly from the SRA using their preferred method.  

This will produce:
- `R1.fastq.gz` → forward reads
- `R2.fastq.gz` → reverse reads

These files are then used as input in the notebook.

### 4. Download PLSDB database
This workflow uses the **PLSDB plasmid database** (Molano et al., 2024).  
The database can be downloaded from [PLSDB](https://ccb-microbe.cs.uni-saarland.de/plsdb/) (accessed July 2025).

Example:
```bash
wget https://ccb-microbe.cs.uni-saarland.de/plsdb/plsdb.fasta.gz
gunzip plsdb.fasta.gz
makeblastdb -in plsdb.fasta -dbtype nucl -out plsdb
```

This creates a local BLAST database (named plsdb) for use in Step 6 of the notebook.

### 5. Ragout recipe files
Example Ragout recipe files are provided in the `/recipes/` folder:
- `ragout_chromosome_recipe_vasicola.txt` (uses SAM119.fasta as reference)
- `ragout_chromosome_recipe_holcicola.txt` (uses NCPPB1060.fasta as reference)

These can be modified to use different reference genomes depending on the pathovar being assembled.

For **plasmid scaffolding (Step 7 in the notebook)**, update `reference.fasta` to the most appropriate reference plasmid for your dataset.

### 6. Run the notebook
Start Jupyter Lab or Notebook in the repository folder:
```bash
jupyter lab

# or
 
jupyter notebook
```
Then open genome_assembly_methods.ipynb and follow the workflow.

### Notes
For citations of software tools and databases used in this workflow, please refer to the accompanying manuscript.
