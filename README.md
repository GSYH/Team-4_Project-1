# BIOINF-575-Final-Project: Drug annotation of 23andme report

## Overview
This project integrates 23andMe genotype data with PharmGKB pharmacogenomic annotations to identify personal genetic variants that may influence drug efficacy and response.

The analysis merges variants from a 23andMe file with PharmGKB’s curated variant–drug associations, filters for significant and efficacy-related results, and summarizes potential pharmacogenomic insights.

---

## Data Sources

### 23andMe Genotype Data
Example file: `23andme_v5_hg19_ref.txt`

Columns:
- CHR: Chromosome
- POS: Genomic position
- dbSNP_ID: Variant ID (rsID)
- ALLELE: Observed alleles in the individual’s genome

### PharmGKB Variant–Drug Annotation Data
File: `var_drug_ann.tsv` (from PharmGKB download page)

Key columns:
- Variant/Haplotypes
- Gene
- Drug(s)
- PMID
- Phenotype Category
- Significance
- Notes
- Sentence
- Alleles


## For question 6.1 package github link:  [https://github.com/GSYH/drug_response_23andme/tree/main]
---

## Pipeline

| Step | Description | Output |
|------|--------------|---------|
| 1 | Load and clean 23andMe genotype data (rsIDs only). | `df_23` |
| 2 | Load and clean PharmGKB annotations (skip malformed line). | `df_ann` |
| 3 | Merge datasets by dbSNP_ID. | `df_merge` |
| 4 | Filter for Significance = "yes" and Phenotype Category = "efficacy". | `df_sig_eff` |
| 5 | Export final variant and summary tables. | `23andme_PharmGKB_map.tsv`, `23andme_PharmGKB_summary.tsv` |
| 6 | Plot the distribution of drug and SNP counts per gene. | Histogram plots |

---

## Outputs

1. **23andme_PharmGKB_map.tsv**  
   Variant-level associations:
