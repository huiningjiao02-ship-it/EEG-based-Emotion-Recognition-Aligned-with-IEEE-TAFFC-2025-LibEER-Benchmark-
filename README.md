# EEG-based Emotion Recognition with LibEER Benchmark

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1GnnSo4iL_0Os2eptGpwOEsxCbBS6Vq6V)

## Introduction

This project reproduces the core evaluation pipeline of the **LibEER** benchmark (IEEE TAFFC 2025) for EEG‑based emotion recognition. LibEER provides standardized preprocessing, feature extraction, and evaluation protocols to address the long‑standing issue of inconsistent comparisons in the field.

I implemented a custom **1D‑CNN** model on the Kaggle *EEG Brainwave Dataset: Feeling Emotions* to perform three‑class emotion classification (Negative / Neutral / Positive). The project runs entirely in Google Colab with automatic dataset download.

## Key Features

- Reproduces the **Subject‑Dependent (SD)** workflow described in LibEER
- Custom 1D‑CNN with three convolutional blocks and automatic FC dimension inference
- Automatic Kaggle dataset download and preprocessing (label encoding, Z‑score normalization)
- One‑click Colab execution with GPU support
- Critical analysis of evaluation protocol and its impact on reported accuracy

## Quick Start

1. Click the **Open In Colab** badge above
2. Set runtime to **GPU** (`Runtime` → `Change runtime type`)
3. Run all cells (`Runtime` → `Run all`)

The notebook will download the dataset, train the model, and display results.

## Results

| Metric | Value |
| :--- | :--- |
| Test Accuracy | **99.5%** |
| Precision (weighted) | 0.99 |
| Recall (weighted) | 0.99 |
| F1‑Score (weighted) | 0.99 |

**Important Note**: This high accuracy is obtained under **Subject‑Dependent (SD) evaluation**, where samples from the same subject appear in both training and test sets. This causes **subject‑wise data leakage**—the model learns to recognize individual EEG signatures rather than generalizable emotion patterns. LibEER explicitly warns against interpreting SD results as true cross‑subject generalization.

Under the correct **Subject‑Independent (SI)** protocol (Leave‑One‑Subject‑Out), the expected accuracy would drop to approximately **60–70%**. The dataset used here lacks subject identifiers, so SI validation is not currently feasible.

## Limitations

1. **Evaluation Protocol** – Only Subject‑Dependent (SD) validation is performed due to the absence of subject IDs in the dataset. Cross‑subject generalization cannot be assessed.
2. **Preprocessing** – The dataset provides pre‑extracted features (2,548‑dim); standard EEG preprocessing (bandpass filtering, differential entropy) is not applied.
3. **Model Architecture** – The 1D‑CNN captures only temporal patterns. Spatial electrode relationships (as modeled by DGCNN) are not utilized.

## Future Improvements

- Migrate to a dataset with **real subject labels** (e.g., SEED, DEAP) to implement **LOSO cross‑validation**
- Apply full EEG preprocessing: **1–50 Hz bandpass filtering** and **differential entropy** extraction
- Replace 1D‑CNN with **DGCNN** to incorporate graph‑based spatial information

## Project Structure
