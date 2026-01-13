# scRNAseq Cornea MG53 Analysis

Single-cell RNA sequencing analysis of mouse corneal tissue (Project 19072-23).

**Collaboration**: Lilian Sakai (OSU Wexner Medical Center)

## Experimental Design

| Sample | Label | Genotype | Injury | Cells |
|--------|-------|----------|--------|-------|
| 19072-23-01-01-01 | C8 | KO | Injured | 6,021 |
| 19072-23-02-01-01 | C9 | WT | Injured | 5,191 |
| 19072-23-03-01-01 | C10 | KO | Uninjured | 5,896 |
| 19072-23-04-01-01 | C11 | WT | Uninjured | 7,297 |

**Total**: 24,405 cells

## Analysis Scripts

| Script | Description |
|--------|-------------|
| `1_preprocess.rmd` | QC, normalization, Harmony batch correction |
| `2_celltype_annotation.rmd` | Cell type assignment (12 types) |
| `3_deg_pathway.rmd` | DEG & pathway analysis |

## Contact

Cankun Wang (wang.13246@osu.edu)
