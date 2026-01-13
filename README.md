# scRNAseq Cornea MG53 Analysis

Single-cell RNA sequencing analysis of mouse corneal tissue (Project 19072-23).

**Collaboration**: Lilian Sakai (OSU Wexner Medical Center)
**Interactive portal**: https://bmblx.bmi.osumc.edu/scrnaseq_huazhu_cornea/

## Quick Links

- [Final Report (Word)](./report_12222025.docx)
- [Preprocessing Report (HTML)](./a1_preprocess.html)

## Experimental Design

| Sample | Label | Genotype | Injury | Cells |
|--------|-------|----------|--------|-------|
| 19072-23-01-01-01 | C8 | KO | Injured | 6,021 |
| 19072-23-02-01-01 | C9 | WT | Injured | 5,191 |
| 19072-23-03-01-01 | C10 | KO | Uninjured | 5,896 |
| 19072-23-04-01-01 | C11 | WT | Uninjured | 7,297 |

**Total**: 24,405 cells

## Directory Structure

```
├── 1_preprocess.rmd              # QC, normalization, Harmony
├── 2_celltype_annotation.rmd     # Cell type assignment
├── 3_deg_pathway.rmd             # DEG & pathway analysis
├── report_12222025.docx          # Final report
├── a1_preprocess.html            # QC report
└── results/
    ├── figures/                  # PNG/SVG plots
    └── tables/                   # CSV results
```

## Result Files

### Tables (`results/tables/`)
- `proj23_DEG_*.csv` - Differential expression results
- `proj23_GO_BP_*.csv` - GO enrichment results
- `proj23_KEGG_*.csv` - KEGG enrichment results
- `proj23_celltype_*.csv` - Cell composition tables
- `proj23_sample_metadata.csv` - Sample information

### Figures (`results/figures/`)
- `proj23_umap_*.png` - UMAP visualizations
- `proj23_volcano_*.png` - Volcano plots
- `proj23_composition_*.png` - Composition bar plots
- `proj23_GO_BP_*.png` - GO enrichment plots

## Data Availability

Raw data and Seurat objects not included. Contact for access.

## Contact

Cankun Wang (wang.13246@osu.edu)
