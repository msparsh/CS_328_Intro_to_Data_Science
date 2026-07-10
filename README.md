# Optimizing Query Retrieval via Learned Index Structures

## Overview

This project explores how machine learning can improve traditional probabilistic data structures for fast membership queries. Instead of relying solely on hash-based lookup, it introduces a **learned index** that predicts whether a URL is likely to belong to a known set before consulting a conventional Bloom filter.

The system combines the efficiency of Bloom filters with the predictive capability of machine learning to reduce unnecessary lookups while maintaining **zero false negatives** through a deterministic fallback mechanism.

## Project Objectives

* Implement a baseline Bloom filter for URL membership queries.
* Replace static hash-only decisions with a learned prediction model.
* Compare different learned oracle architectures.
* Evaluate accuracy, false positive rate, inference speed, and memory efficiency.
* Investigate the effect of model quantization on performance.

## Approach

The project evaluates three approaches:

* **Standard Bloom Filter** – Traditional probabilistic membership structure using multiple hash functions.
* **Gradient Boosted Trees (GBT) Oracle** – A classical machine learning classifier used as a learned index.
* **Quantized Neural Network Oracle** – A lightweight neural model optimized for efficient inference and reduced memory usage.

When the learned model is sufficiently confident, its prediction is used directly. Otherwise, the system falls back to the Bloom filter, preserving deterministic correctness and ensuring no false negatives.

## Dataset

The experiments use a publicly available dataset containing malicious and benign URLs. The original multiclass labels are converted into a binary classification problem:

* Benign URLs
* Malicious URLs (including phishing, malware, and defacement)

The notebook automatically downloads the dataset from Kaggle during execution.

## Workflow

1. Install required dependencies.
2. Download and preprocess the dataset.
3. Perform exploratory data analysis.
4. Convert URLs into numerical features using TF-IDF.
5. Train the Gradient Boosted Trees classifier.
6. Train the neural network model.
7. Quantize the neural network for efficient inference.
8. Integrate the learned oracle with the Bloom filter.
9. Evaluate and compare all approaches using classification and retrieval metrics.

## Evaluation

The implementations are compared using metrics such as:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC
* Precision-Recall AUC
* False Positive Rate
* Memory usage
* Inference time

Visualizations are included to compare model performance and demonstrate the trade-offs between traditional and learned membership structures.

## Technologies Used

* Python
* PyTorch
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* mmh3
* OpenDatasets (Kaggle)

## Running the Project

1. Install the required dependencies.
2. Obtain a Kaggle API token.
3. Run the notebook cells sequentially.
4. The dataset will be downloaded automatically.
5. Training, evaluation, and comparison plots will be generated during execution.

## Key Outcome

This project demonstrates that integrating learned models with Bloom filters can significantly improve query efficiency while preserving the reliability guarantees of traditional probabilistic data structures. It also highlights the practical benefits of model quantization for deploying learned indexing systems in memory-constrained environments.
