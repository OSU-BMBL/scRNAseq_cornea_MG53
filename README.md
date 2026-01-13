# scRNAseq Cornea MG53 Analysis

Single-cell RNA sequencing analysis of mouse corneal tissue examining MG53 knockout effects in corneal injury.

**Project**: 19072-23
**Collaboration**: Dr. Lilian Sakai (OSU Wexner Medical Center)
**Interactive portal**: https://bmblx.bmi.osumc.edu/scrnaseq_huazhu_cornea/

## Quick Links

- [Final Report (Word)](./report_12222025.docx)
- [Preprocessing HTML Report](./a1_preprocess.html)
- [DEG Summary Table](./results/tables/proj23_DEG_summary.csv)
- [Cell Type Composition](./results/tables/proj23_celltype_by_condition.csv)

## Experimental Design

**2x2 Factorial**: Genotype (MG53 KO vs WT) x Injury Status (Injured vs Uninjured)

| Sample | Label | Genotype | Injury | Cells |
|--------|-------|----------|--------|-------|
| 19072-23-01-01-01 | C8 | KO | Injured | 6,021 |
| 19072-23-02-01-01 | C9 | WT | Injured | 5,191 |
| 19072-23-03-01-01 | C10 | KO | Uninjured | 5,896 |
| 19072-23-04-01-01 | C11 | WT | Uninjured | 7,297 |

**Total cells**: 24,405

## Directory Structure

```
scRNAseq_cornea_MG53/
├── README.md
├── report_12222025.docx          # Final analysis report
├── a1_preprocess.html            # QC/preprocessing report
├── 1_preprocess.rmd              # Preprocessing script
├── 2_celltype_annotation.rmd     # Cell type annotation
├── 3_deg_pathway.rmd             # DEG & pathway analysis
└── results/
    ├── figures/                  # PNG/SVG plots
    │   ├── proj23_umap_*.png
    │   ├── proj23_composition_*.png
    │   ├── proj23_volcano_*.png
    │   └── proj23_GO_BP_*.png
    └── tables/                   # CSV results
        ├── proj23_DEG_*.csv
        ├── proj23_GO_BP_*.csv
        ├── proj23_celltype_*.csv
        └── proj23_sample_metadata.csv
```

## Analysis Workflow

### 1. Preprocessing (`1_preprocess.rmd`)
- Load 10X CellRanger output
- Automated QC with `scuttle::isOutlier` (nmads=3)
- Harmony batch correction
- UMAP and clustering (resolution 0.3 → 25 clusters)

### 2. Cell Type Annotation (`2_celltype_annotation.rmd`)
- 12 cell types annotated by expert (Lilian Sakai)
- Marker gene validation
- Composition analysis by condition

### 3. DEG & Pathway Analysis (`3_deg_pathway.rmd`)
- Overall: KO vs WT, Injured vs Uninjured
- Stratified: KO vs WT within injured/uninjured
- Per cell type DEG
- GO Biological Process enrichment

## Cell Types (12)

| Cell Type | Clusters | Count | % |
|-----------|----------|-------|---|
| Corneal epithelial cells | 0,2,3,4,5,9 | 10,896 | 44.65 |
| Immune cells | 6,7,15,23,24 | 3,702 | 15.17 |
| TACs | 1,17 | 2,846 | 11.66 |
| LSCs | 8 | 1,288 | 5.28 |
| Corneal basal epithelial | 13,16 | 1,275 | 5.22 |
| Fibroblasts | 14,18,19 | 1,211 | 4.96 |
| Conjunctival basal epithelial | 10 | 1,084 | 4.44 |
| Conjunctival epithelial | 11 | 943 | 3.86 |
| Keratocytes | 12 | 791 | 3.24 |
| Schwann cells | 20 | 136 | 0.56 |
| Myofibroblasts | 21 | 124 | 0.51 |
| Endothelial cells | 22 | 109 | 0.45 |

## Key Findings

1. **Injury dominates transcription**: 7,179 DEGs (injury) vs 950 DEGs (genotype) = 7.5x
2. **Context-dependent MG53**: KO effect 9.2x stronger in injured tissue (920 vs 100 DEGs)
3. **Immune cell expansion**: 0.29% → 36.16% upon injury in WT (125x)
4. **Keratinization pathway**: 12.5x enriched in KO, linking MG53 to epithelial differentiation

## Key Result Files

### DEG Analysis
| File | Description |
|------|-------------|
| `proj23_DEG_summary.csv` | Summary of all comparisons |
| `proj23_DEG_KO_vs_WT_overall.csv` | KO vs WT (all cells) |
| `proj23_DEG_Injured_vs_Uninjured_overall.csv` | Injury effect (all cells) |
| `proj23_DEG_KO_vs_WT_Injured.csv` | KO effect in injured tissue |
| `proj23_DEG_KO_vs_WT_Uninjured.csv` | KO effect in uninjured tissue |

### Pathway Analysis
| File | Description |
|------|-------------|
| `proj23_GO_BP_*.csv` | GO Biological Process enrichment |
| `proj23_KEGG_*.csv` | KEGG pathway enrichment |

### Figures
| File | Description |
|------|-------------|
| `proj23_umap_celltype.png` | UMAP colored by cell type |
| `proj23_composition_by_condition.png` | Cell type composition |
| `proj23_volcano_*.png` | Volcano plots for DEG |
| `proj23_GO_BP_*.png` | GO enrichment dot plots |

## Data Availability

Raw sequencing data and Seurat objects are not included in this repository due to size constraints. The processed results (tables and figures) are provided for reproducibility documentation.

**Contact for data access**: Cankun Wang (wang.13246@osu.edu)

## Session Info

```
R version 4.4.0
Seurat 5.3.0
harmony 1.2.0
scuttle 1.14.0
clusterProfiler 4.12.0
```

## Contact

- **Analyst**: Cankun Wang (wang.13246@osu.edu)
- **Collaborator**: Dr. Lilian Sakai (OSU Wexner Medical Center)

---
*Analysis performed by BMBL, The Ohio State University*
