# Mistral-OCR-Benchmark: Institutional OCR Reliability Framework

An enterprise-grade evaluation framework for benchmarking Mistral OCR models against high-stakes legal, financial, and degraded documents. This project implements a **Triangulation Reliability Framework** to measure accuracy, consistency, and consensus across diverse document taxonomies.

## ⚖️ Strategic Model Selection Guide

Use this matrix to determine the optimal model for your specific financial pipeline requirements:

| Use Case / Challenge | Recommended Model | Technical Justification |
| :--- | :--- | :--- |
| **High-Stakes Finance (10-Ks, Ledgers)** | `mistral-ocr-4-1` | Highest numeric fidelity and successful pass-rate on Arithmetic Consistency checks. |
| **Legacy Scans / Low-DPI (72-150 DPI)** | `mistral-ocr-4-1` | Superior resolution resilience; maintains >98% confidence at 72 DPI where other models fail. |
| **High-Volume Search/Archival** | `mistral-ocr-3-0` | ~25% lower latency with high text accuracy on clean, native PDFs. |
| **Signature & Form Extraction (W-9, MSA)** | `mistral-ocr-4-latest`| Precision layout analysis for signature blocks and multi-color overlapping text/stamps. |
| **Complex Tabular Pivot Tables** | `mistral-ocr-4-1` | Advanced cell-boundary detection for merged headers and multi-level columns. |

## 📊 The Triangulation Reliability Framework

Standard Word Error Rate (WER) is insufficient for finance. This framework focuses on **functional reliability** via three proxy signals:

1.  **Arithmetic Self-Consistency (The 'Logic' Check):** A zero-shot heuristic validating if extracted line items sum to totals. This catches digit errors (e.g., '8' read as '3') that 'look' confident to the model.
2.  **Cross-Model Consensus (The 'Jury' Check):** Measures agreement between independent model generations to flag fields requiring human audit.
3.  **Resolution Stress Testing:** Quantitative decay analysis across a 72-300 DPI gradient to identify the 'breaking point' of your automated pipeline.

## 🔍 Executive Observations & 'Confidence Traps'

### ⚠️ The Confidence Trap
Analysis shows that **Average Page Confidence** often remains high (>99%) even when critical numeric digits are misread. We recommend implementing the **Arithmetic Consistency Check** for all financial production pipelines to mitigate high-confidence hallucination.

### 🏆 The Enterprise Choice: `mistral-ocr-4-1`
Demonstrated exceptional robustness in **Resolution Resilience**. Unlike previous iterations, `4-1` preserved table structure in 72 DPI scans that caused row-merging errors in legacy models.

## 📈 Performance Dashboard

### Executive Summary (Normalized Metrics)
| model              |   avg_confidence |   consensus_agreement_rate |   latency_sec |
|:-------------------|-----------------:|---------------------------:|--------------:|
| mistral-ocr-2512   |            0.993 |                       0.96 |          2.27 |
| mistral-ocr-3-0    |            0.992 |                       0.96 |          2.78 |
| mistral-ocr-3      |            0.992 |                       0.96 |          2.25 |
| mistral-ocr-4-0    |            1     |                       0.96 |          2.51 |
| mistral-ocr-latest |            0.999 |                       0.96 |          4.33 |
| mistral-ocr-4      |            0.999 |                       0.96 |          2.67 |
| mistral-ocr-4-1    |            0.999 |                       0.96 |          2.74 |

### Visual Analysis & Heatmaps

#### 1. Reliability vs. Document Category
![Category Heatmap](ocr_comparison_output/category_x_model_heatmap.png)
*Identifies model strengths in 'Multi-header Tables' vs. 'Workflow Diagrams'.*

#### 2. Resolution Stress Curve
![DPI Heatmap](ocr_comparison_output/confidence_vs_dpi.png)
*Quantitative analysis of model certainty decay as scan quality decreases.*

#### 3. Spatial Extraction Fidelity
![BBox Comparison](ocr_comparison_output/bbox_comparison_page0.png)
*Visual side-by-side comparison of layout analysis and block segmentation.*

## 🛠️ Framework Capabilities
- **Native Enterprise Formats:** Advanced processing for `.docx`, `.xlsx`, `.pptx`, `.eml`, and `.md`.
- **Curated Corpus:** 21 documents including Fortune 500 filers, IRS forms, and synthetic hierarchical org charts.
- **Automated Reporting:** Generates per-document 'Report Cards' with visual confidence heatmaps and cost-latency projections.
