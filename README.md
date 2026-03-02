# Trivariate MR Analysis: Gut Microbiome, Genetics, and Neurodegeneration

This repository contains the full source code, processed datasets, and key analysis results supporting the manuscript: **"Causal Relationships Among Gut Microbiota, Genetic Mediators, and Neurodegenerative Diseases: A Mendelian Randomization Study"**.

---

## 1. Project Overview and Methodology

This project employs a **Mendelian Randomization (MR)** framework to systematically investigate the three-way causal associations among gut microbiota composition, genetic regulatory mechanisms, and neurodegenerative diseases (including Alzheimer's disease, Parkinson's disease, ALS, and others).

The analytical strategy integrates:

- **Two-sample MR** — to estimate causal effects of gut microbiota on neurodegeneration
- **eQTL (expression Quantitative Trait Loci)** — to identify SNPs regulating gene expression in brain and gut tissues
- **mQTL (methylation Quantitative Trait Loci)** — to bridge genetic variants with epigenetic regulation
- **Mediation MR** — to decompose direct vs. gene-mediated indirect effects
- **Colocalization** — to test whether microbiome signals and disease signals share a common causal variant

---

## ⚠️ Data Availability

All GWAS summary statistics used in this analysis are publicly available from their respective consortia. Due to file size limitations, processed datasets are hosted externally.

> 🔧 *Data source details will be updated here progressively.*

### Gut Microbiome GWAS
<!-- e.g., MiBioGen consortium, https://mibiogen.gcc.rug.nl -->

### Neurodegenerative Disease GWAS
<!-- e.g., IGAP (AD), IPDGC (PD), Project MinE (ALS) -->

### eQTL Data
<!-- e.g., GTEx v8 (https://gtexportal.org), eQTLGen (https://eqtlgen.org) -->

### mQTL Data
<!-- e.g., GoDMC (http://mqtldb.org), mQTLdb -->

---

## 2. Repository Structure

The repository is organized as follows to facilitate reproducibility:

- `data/gwas_summary/microbiome/` : GWAS summary statistics for gut microbial taxa and diversity indices.
- `data/gwas_summary/neurodegen/` : GWAS summary statistics for neurodegenerative diseases.
- `data/gwas_summary/expression/` : eQTL and mQTL reference datasets (brain/gut tissues).
- `data/processed/` : Harmonized and LD-clumped datasets ready for MR analysis.
- `data/instruments/` : Selected instrumental variables (IVs) passing F-statistic thresholds.
- `scripts/01_iv_selection.R` : Instrument variable selection and LD clumping.
- `scripts/02_mr_main.R` : Primary two-sample MR analysis (IVW, MR-Egger, weighted median).
- `scripts/03_sensitivity.R` : Sensitivity analyses — heterogeneity, pleiotropy, leave-one-out.
- `scripts/04_eqtl_annotation.R` : eQTL lookup and gene expression mediation.
- `scripts/05_mqtl_annotation.R` : mQTL lookup and methylation mediation.
- `scripts/06_mediation_mr.R` : Two-step mediation MR to quantify indirect effects.
- `scripts/07_colocalization.R` : Colocalization analysis using the `coloc` package.
- `results/` : Output tables and figures from all analyses.

---

## 3. Analytical Pipeline

```
┌─────────────────────┐       ┌──────────────────────────┐
│  Gut Microbiome GWAS│       │  Neurodegenerative GWAS   │
└────────┬────────────┘       └─────────────┬────────────┘
         │                                  │
         ▼                                  │
  IV Selection & LD Clumping                │
  (F-stat > 10, p < 5×10⁻⁸)               │
         │                                  │
         ├──── eQTL / mQTL Annotation       │
         │           │                      │
         │           ▼                      │
         │     Mediation MR          ◄──────┘
         │     (indirect effect)
         │
         ▼
  Two-Sample MR  ──► Sensitivity Analyses
  (IVW / Egger / WM)   (Egger intercept,
         │               leave-one-out,
         ▼               MR-PRESSO)
  Colocalization
```

---

## 4. Dependencies

```r
# R (≥ 4.1.0) packages
TwoSampleMR             # Main MR framework
MendelianRandomization
coloc                   # Colocalization
ieugwasr                # OpenGWAS API access
MR.PRESSO               # Pleiotropy-robust MR
tidyverse
data.table
```

Install all at once:

```r
install.packages(c("tidyverse", "data.table", "coloc"))
remotes::install_github("MRCIEU/TwoSampleMR")
remotes::install_github("rondolab/MR-PRESSO")
```

---

## 5. Citation

If you use code or data from this repository, please cite:

> [Author et al.], *[Journal]*, [Year]. DOI: [to be added upon publication]

Please also cite the primary data sources listed in the **Data Availability** section.

---

## 6. Contact

For questions, bug reports, or collaboration inquiries, please open an [Issue](../../issues) or contact the corresponding author directly.
