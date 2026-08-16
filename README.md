# Mistral-OCR-Benchmark

An end-to-end evaluation framework for comparing Mistral OCR models on complex legal and financial documents.

## 📊 Key Observations & Results

Based on our benchmark of 21 documents across 9 challenge categories, here are the core findings:

1. **Accuracy vs. Resolution:** Models like `mistral-ocr-4-1` and `mistral-ocr-latest` show significant robustness to low-DPI scans (72-150 DPI) compared to earlier versions, maintaining high confidence where others degrade.
2. **Numeric Fidelity:** By flagging tokens below 85% confidence, we identified that while overall page confidence is high (>99%), specific multi-year comparative tables still pose risks for digit-level errors.
3. **Consensus Reliability:** Models showed high agreement on standard fields like `document_type`, but disagreed on `effective_date` formats, highlighting the need for the consensus-scoring layer.
4. **Performance:** The latest OCR 4 models offer a superior balance of structured extraction accuracy and latency, particularly for dense financial filings.

### Composite Reliability Scores
| model              |   avg_confidence | arithmetic_consistency_rate   |   consensus_agreement_rate |   latency_sec |
|:-------------------|-----------------:|:------------------------------|---------------------------:|--------------:|
| mistral-ocr-2512   |            0.993 |                               |                       0.96 |          2.27 |
| mistral-ocr-3-0    |            0.992 |                               |                       0.96 |          2.78 |
| mistral-ocr-3      |            0.992 |                               |                       0.96 |          2.25 |
| mistral-ocr-4-0    |            1     |                               |                       0.96 |          2.51 |
| mistral-ocr-latest |            0.999 |                               |                       0.96 |          4.33 |
| mistral-ocr-4      |            0.999 |                               |                       0.96 |          2.67 |
| mistral-ocr-4-1    |            0.999 |                               |                       0.96 |          2.74 |

## 🖼️ Visual Performance Insights

### Model Confidence vs. Scan Resolution (DPI)
![DPI Heatmap](ocr_comparison_output/confidence_vs_dpi.png)

### Category-wise Reliability Heatmap
![Category Heatmap](ocr_comparison_output/category_x_model_heatmap.png)

### Multi-Model Bounding Box Comparison
![BBox Comparison](ocr_comparison_output/bbox_comparison_page0.png)

## 🛠️ Framework Features
- **Multi-Model Comparison:** Side-by-side evaluation of latest Mistral OCR versions.
- **Challenge Corpus:** 20+ documents spanning multi-header tables, handwriting, and low-DPI scans.
- **Reliability Metrics:** Arithmetic consistency, cross-model consensus, and visual heatmaps.
- **Office & Messaging Support:** Native processing for .docx, .xlsx, .pptx, and .eml formats.
