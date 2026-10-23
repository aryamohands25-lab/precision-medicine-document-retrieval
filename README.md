# Precision Medicine Document Retrieval

An exploratory Bio-AI capstone project that combines information retrieval, biomedical query expansion, and deep learning to improve the ranking of precision medicine research documents.

## Overview

Precision medicine uses information about diseases, genetic mutations, and targeted therapies to support more personalized treatment decisions. Finding relevant biomedical research among large collections of documents can be challenging because medical terminology varies and relevant information may be expressed in different ways.

This project explores a multi-stage document retrieval pipeline that ranks biomedical documents according to their relevance to structured disease and gene queries. It combines traditional information retrieval with neural relevance models and a machine-learning-based ranking approach.

## Objectives

- Retrieve biomedical documents relevant to disease and gene-related queries.
- Explore query expansion using biomedical terminology and synonyms.
- Improve document ranking using field-weighted relevance.
- Compare traditional BM25 retrieval with neural ranking approaches.
- Evaluate retrieval performance using Precision@K and Normalized Discounted Cumulative Gain (NDCG).
- Investigate the contribution of individual pipeline components through ablation analysis.

## Methodology

The project explores the following components:

### 1. Biomedical Query Expansion
Expands the original query with related disease and gene terminology to explore whether additional biomedical terms improve retrieval.

### 2. BM25 Retrieval
Uses BM25, a traditional probabilistic information retrieval method, to rank documents according to their relevance to a query.

### 3. Field-Weighted Retrieval
Explores giving different importance to document fields, with greater emphasis on disease and gene information than on treatment or demographic information.

### 4. BiGRU with Attention
Uses a Bidirectional Gated Recurrent Unit (BiGRU) with an attention mechanism to explore treatment-focused document classification and contextual text representation.

### 5. MatchPyramid
Uses a query-document interaction model to explore relevance scoring based on interactions between query terms and document text.

### 6. Logistic Regression-Based Ensemble
Combines retrieval and neural-model scores using logistic regression to produce a final relevance score and rerank documents.

### 7. Evaluation and Ablation Analysis
Evaluates retrieval rankings using Precision@K and NDCG@K and compares different pipeline configurations to investigate the contribution of individual components.

## Pipeline

1. Receive a structured biomedical query.
2. Expand the query with relevant biomedical terminology.
3. Retrieve and rank candidate documents using BM25.
4. Apply field-weighting and neural relevance components.
5. Combine the component scores using an ensemble model.
6. Generate the final document ranking.
7. Evaluate ranking performance using retrieval metrics and ablation experiments.

## Example Queries

The illustrative experiments include queries involving:

- Melanoma and the BRAF V600E mutation
- Non-small cell lung cancer (NSCLC) and the EGFR L858R mutation
- Breast cancer and BRCA1

These examples are used to explore disease- and gene-focused biomedical document retrieval.

## Evaluation Metrics

| Metric | Purpose |
|---|---|
| Precision@5 | Measures the proportion of relevant documents among the top five results. |
| Precision@10 | Measures the proportion of relevant documents among the top ten results. |
| NDCG@5 | Measures the quality of the top-five ranking while accounting for relevance and rank position. |
| NDCG@10 | Measures ranking quality among the top ten results. |

## Illustrative Results

The following results are from the notebook's reported evaluation:

| Method | Precision@5 | Precision@10 | NDCG@5 | NDCG@10 |
|---|---:|---:|---:|---:|
| BM25 Initial | 0.6000 | 0.4000 | 0.8405 | 0.9140 |
| Full Ensemble | 0.7333 | 0.4000 | 0.9376 | 0.9635 |

The reported results show improved Precision@5 and NDCG values for the full ensemble compared with the initial BM25 baseline in these experiments. Precision@10 remains unchanged.

### Ablation Analysis

Reported NDCG@5 values for selected configurations:

| Configuration | NDCG@5 |
|---|---:|
| BM25 Only | 0.8548 |
| BM25 + Query Expansion | 0.8310 |
| BM25 + Field Boosting | 0.8405 |
| Full Ensemble | 0.9376 |

The ablation results illustrate why individual components should be evaluated rather than assuming that every added component improves retrieval performance.

## Technologies and Concepts

- **Programming:** Python
- **Information Retrieval:** BM25, `rank_bm25`
- **Deep Learning:** BiGRU, Attention, MatchPyramid
- **Machine Learning:** Logistic Regression
- **Evaluation:** Precision@K, NDCG@K, ablation analysis
- **Application Domain:** Bio-AI, biomedical NLP, precision medicine

## Dataset and Experimental Scope

The notebook uses a small illustrative collection of 20 simulated PubMed-style documents, three structured queries, and manually defined relevance judgments.

**Important:** This is a prototype experiment, not a full reproduction of the official TREC 2019 Precision Medicine benchmark. Its reported results should be interpreted within the scope of the small illustrative dataset and should not be generalized to real-world clinical retrieval without further validation.

## Limitations

- The evaluation collection is small and illustrative.
- Relevance judgments are manually defined.
- Results may change with different datasets, queries, and relevance labels.
- Neural ranking components require more extensive testing to establish their general usefulness.
- The system has not been clinically validated and is not intended to recommend treatments or support patient-specific medical decisions.

## Future Improvements

- Evaluate on larger, real biomedical research collections.
- Incorporate validated biomedical terminology resources.
- Compare against additional retrieval baselines.
- Use more extensive and independently assessed relevance judgments.
- Test statistical significance across a broader set of queries.
- Explore biomedical language models and hybrid sparse-dense retrieval.
- Improve reproducibility through documented configurations and repeatable experiments.

## Project Significance

This project explores how traditional information retrieval and neural ranking techniques can be combined for biomedical literature search. It provides a foundation for further experimentation in Bio-AI, biomedical natural language processing, and precision medicine information retrieval.

## Disclaimer

This repository is intended for academic and research purposes only. It is an experimental document-retrieval prototype and is not a clinically validated system or a substitute for professional medical judgment.

## Author

Developed as a Bio-AI capstone project exploring biomedical information retrieval and machine learning.
