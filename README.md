# Bulk Transcriptomic Analysis: Parkinson's Disease (PD) Cortex vs. Control

This repository contains the transcriptomic analysis and interpretive report comparing Parkinson’s disease (PD) cortical samples against healthy controls, highlighting key methodological insights, tissue-specific limitations, and biological interpretations.

---

## 📊 Overview & Model Statistics

* **Model Calibration:** The analysis features a flat p-value histogram with a peak near zero, indicating a well-calibrated model without inflation.
* **Dataset Scale:** 
  * Genes tested: **244**
  * Significant ($FDR < 0.05$): **248** *(Note: reflects metrics reported in pipeline output)*
  * Upregulated in PD: **190**
  * Downregulated in PD: **158**
* **Depositor Concordance:** $R = 0.87$ ($87\%$ sign agreement, $229/263$ of key overlaps).

---

## 🔬 Key Methodological & Biological Insights

### 1. The Cortex vs. Substantia Nigra Limitation
Classic dopaminergic markers (such as tyrosine hydroxylase `TH` and dopa decarboxylase `DDC`) appear unchanged or "flat" in this dataset. 
* **Reason:** They are expressed at extremely low baseline levels in cortical tissue (BaseMean $\sim 21$ for `TH` and $\sim 4$ for `DDC`) compared to the midbrain. 
* **Conclusion:** Bulk cortex data cannot adequately test nigral dopaminergic hypotheses. `ALDH1A1` surviving as significant in the cortex is noted as a genuinely interesting, non-artifactual signal.

### 2. Upregulated Signature Analysis
The top upregulated genes skew heavily toward **epithelial, vascular, and innate-immune markers** rather than neuronal ones.
* **Top Upregulated:** `KLK1` ($+3.47$), `DEFB1` ($+3.00$), `SLPI` ($+2.81$), `CD177` ($+2.73$), `SLC22A2` ($+2.45$), `OGN` ($+2.44$), `SCARA3` ($+2.23$), `KRT19` ($+2.01$), `CXCL6` ($+1.88$).
* **Top Downregulated:** `MMP3` ($-2.27$), `GPR169` ($-1.57$), `CCKL5` ($-1.36$), `DMRTA1` ($-1.29$), `STAROS` ($-1.27$), `CFTR` ($-1.25$), `GRK5` ($-1.12$).
* **Interpretation:** This pattern points toward potential neurovascular decoupling, inflammation, or meningeal/vascular tissue contamination inherent to bulk tissue profiling.

---

## 📁 Associated Files & Artifacts

* `RNASeq-Cortex-Signif-DEGs.csv` — The hits file containing significant differentially expressed genes.
* `RNASeq-PD-cortical-all-genes.csv` — Full table covering all tested genes.
* `RNASeq-PD-vs-controls-MA-Volcano.pdf` — Diagnostic MA and volcano plots.

---

## ⚙️ Choices Made & Confounders Managed

1. **Dataset Choice:** Focused on the primary user report dataset first; rejected single-cell PD-derived nucleus datasets (which present matching-to-patient-and-control contrast issues, as tissue was not present from the same donor and was transfected with a construct vs. case). Bulk was the only dataset with adequate sample matrix among those checked.
2. **Linear Fit / Tissue:** The analysis uses bulk tissue RNA-seq. Because bulk profiling blends signals across cell types, signatures are heavily dominated by epithelial, vascular, and innate-immune genes rather than neuronal ones. Distinguishing true parenchymal neuroinflammation from meningeal/vascular tissue contamination across groups remains a known limitation of bulk data without cell-type deconvolution.

---
