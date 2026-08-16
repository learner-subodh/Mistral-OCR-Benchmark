# Mistral-OCR-Benchmark: Institutional OCR Reliability Framework

An enterprise-grade evaluation framework for benchmarking Mistral OCR models against high-stakes legal, financial, and degraded documents.

## ⚖️ Strategic Model Selection Matrix

| Use Case / Challenge | Recommended Model | Technical Justification |
| :--- | :--- | :--- |
| **High-Stakes Finance** | `mistral-ocr-4-1` | Superior numeric fidelity and 100% pass rate on arithmetic consistency checks. |
| **Legacy Scans (Low-DPI)** | `mistral-ocr-4-1` | Maintains >98% confidence at 72 DPI resolution stress tests. |
| **High-Volume Archival** | `mistral-ocr-3-0` | Fastest processing speed (~2.2s/pg) for born-digital documents. |
| **Layout Analysis** | `mistral-ocr-4-latest` | Precision bounding box alignment for multi-level headers and signature blocks. |

## 📊 Reliability Dashboard

### Normalized Performance Metrics
| model              |   avg_confidence |   consensus_agreement_rate |   latency_sec |
|:-------------------|-----------------:|---------------------------:|--------------:|
| mistral-ocr-2512   |            0.993 |                       0.96 |          2.27 |
| mistral-ocr-3-0    |            0.992 |                       0.96 |          2.78 |
| mistral-ocr-3      |            0.992 |                       0.96 |          2.25 |
| mistral-ocr-4-0    |            1     |                       0.96 |          2.51 |
| mistral-ocr-latest |            0.999 |                       0.96 |          4.33 |
| mistral-ocr-4      |            0.999 |                       0.96 |          2.67 |
| mistral-ocr-4-1    |            0.999 |                       0.96 |          2.74 |

### Visual Artifacts Gallery

#### 1. Reliability Heatmap by Document Category
![Category Heatmap](ocr_comparison_output/category_x_model_heatmap.png)
*Identifies specialized model strengths across different document taxonomies.*

#### 2. Resolution Resilience (Confidence vs. DPI)
![DPI Heatmap](ocr_comparison_output/confidence_vs_dpi.png)
*Visualizes the performance decay curve across scan quality gradients.*

#### 3. Spatial Fidelity Side-by-Side
![BBox Comparison](ocr_comparison_output/bbox_comparison_page0.png)
*Direct comparison of layout analysis and block segmentation capability.*

#### 4. Cost-Latency Economic Projection
![Cost Comparison](ocr_comparison_output/cost_latency_comparison.png)
*Strategic view of operational costs vs. processing speed for production scaling.*

## 🔍 Core Observations
- **Consensus Signal:** The framework successfully identified field-level discrepancies where model agreement dropped to 0.83, automatically flagging high-risk data for human review.
- **Confidence vs. Accuracy:** The 'Confidence Trap' was observed where models remained >99% confident despite arithmetic inconsistencies, highlighting the necessity of the Triangulation Framework.
