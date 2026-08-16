# Mistral-OCR-Benchmark

An end-to-end evaluation framework for comparing Mistral OCR models on complex legal and financial documents.

## Overview
This repository contains a comprehensive benchmarking suite designed to stress-test OCR capabilities across various document formats, including native PDFs, Office documents (Word, Excel, PPTX), and degraded scan simulations.

## Key Features
- **Multi-Model Comparison:** Evaluates latest Mistral OCR versions side-by-side.
- **Challenge Corpus:** 20+ documents spanning multi-header tables, handwritten memos, and low-DPI scans.
- **Reliability Metrics:** 
    - **Arithmetic Self-Consistency:** Validates if table line items sum to totals.
    - **Cross-Model Consensus:** Flags fields where models disagree.
    - **Visual Heatmaps:** Highlights low-confidence numeric tokens.
- **Automated Reporting:** Generates per-document report cards and aggregate leaderboards.

## Structure
- `finance_ocr_corpus/`: The source benchmark documents and stress-test variants.
- `ocr_comparison_output/`: Full results, including CSV metrics, heatmaps, and comparison grids.

## Setup
Ensure you have a `MISTRAL_API_KEY` set in your environment or Google Colab secrets.

```python
pip install mistralai pillow pymupdf pandas matplotlib
```

## License
MIT
