# Colorectal Cancer RNA-seq Differential Expression Analysis

Transcriptomic analysis of colorectal tumor vs. matched normal tissue using 
public GEO data (GSE292858). The pipeline identifies differentially expressed 
genes, performs pathway enrichment, and visualizes results through volcano 
plots, PCA, and clustered heatmaps.

## Dataset

- **Source:** [GSE292858](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE292858) — NCBI GEO
- **Samples:** 39 colorectal tumor, 34 matched normal tissue
- **Data type:** Batch-corrected TPM counts

To reproduce this analysis, download the following files from GEO and place 
them in a `data/` folder:
- `GSE292858_CRC_batch1and2_bcorrected_TPM_count.txt.gz`
- `GSE292858_family.soft.gz`

## Pipeline

1. Data loading and metadata parsing from SOFT file
2. Log2(TPM+1) transformation
3. PCA — quality control and sample separation
4. Welch's t-test + Benjamini-Hochberg FDR correction
5. DEG filtering (adj. p < 0.05, |log2FC| > 1)
6. Volcano plot visualization
7. KEGG and GO pathway enrichment (GSEApy / Enrichr)
8. Clustered heatmaps of top DEGs and pathway genes

## Key Results

| Metric | Value |
|--------|-------|
| Genes tested | 26,426 |
| Total DEGs | 2,430 |
| Upregulated | 1,026 |
| Downregulated | 1,404 |
| Top upregulated gene | REG1A (log2FC = 7.75) |
| Top downregulated gene | OTOP2 (log2FC = −5.63) |
| Top KEGG pathway (up) | Cell cycle (adj. p = 4.5×10⁻¹²) |
| Top KEGG pathway (down) | Mineral absorption (adj. p = 1.2×10⁻⁵) |

## Installation

```bash
git clone https://github.com/Sparrowfish/colorectal-cancer-rnaseq.git
cd colorectal-cancer-rnaseq
pip install -r requirements.txt
jupyter notebook
```

## Tools & Libraries

Python 3.12 | pandas | numpy | scipy | statsmodels | scikit-learn | 
matplotlib | seaborn | gseapy

## Author

Mehrak Malekpour — [GitHub](https://github.com/Sparrowfish)