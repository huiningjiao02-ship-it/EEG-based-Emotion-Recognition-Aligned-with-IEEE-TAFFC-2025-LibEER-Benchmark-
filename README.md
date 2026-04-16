# EEG-based Emotion Recognition with LibEER Benchmark

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1GnnSo4iL_0Os2eptGpwOEsxCbBS6Vq6V)

## Introduction

This project reproduces the core evaluation pipeline of the **LibEER** benchmark (IEEE TAFFC 2025) for EEG‑based emotion recognition. LibEER provides standardized preprocessing, feature extraction, and evaluation protocols to address the long‑standing issue of inconsistent comparisons in the field.

I implemented a custom **1D‑CNN** model on the Kaggle *EEG Brainwave Dataset: Feeling Emotions* to perform three‑class emotion classification (Negative / Neutral / Positive). The project runs entirely in Google Colab with automatic dataset download.

## 项目介绍

本项目复现了 **LibEER** 基准框架（IEEE TAFFC 2025）中 EEG 情绪识别的核心评估流程。LibEER 提供了标准化的预处理、特征提取和评估协议，旨在解决该领域长期存在的对比不一致问题。

我在 Kaggle 公开数据集 *EEG Brainwave Dataset: Feeling Emotions* 上实现了一个自定义的 **1D‑CNN** 模型，进行三分类情绪识别（消极 / 中性 / 积极）。项目完全在 Google Colab 中运行，并支持数据集的自动下载。

---

## Key Features

- Reproduces the **Subject‑Dependent (SD)** workflow described in LibEER
- Custom 1D‑CNN with three convolutional blocks and automatic FC dimension inference
- Automatic Kaggle dataset download and preprocessing (label encoding, Z‑score normalization)
- One‑click Colab execution with GPU support
- Critical analysis of evaluation protocol and its impact on reported accuracy

## 核心特性

- 复现了 LibEER 中描述的 **受试者依赖（SD）** 工作流
- 自定义三层卷积块 1D‑CNN，支持全连接层输入维度自动推断
- Kaggle 数据集自动下载与预处理（标签编码、Z‑score 标准化）
- Colab 一键运行，支持 GPU 加速
- 对评估协议及其对报告准确率的影响进行了批判性分析

---

## Quick Start

1. Click the **Open In Colab** badge above
2. Set runtime to **GPU** (`Runtime` → `Change runtime type`)
3. Run all cells (`Runtime` → `Run all`)

The notebook will download the dataset, train the model, and display results.

## 快速开始

1. 点击上方的 **Open In Colab** 徽章
2. 将运行时类型设置为 **GPU**（`Runtime` → `Change runtime type`）
3. 运行所有单元格（`Runtime` → `Run all`）

Notebook 将自动下载数据集、训练模型并展示结果。

---

## Results

| Metric | Value |
| :--- | :--- |
| Test Accuracy | **99.5%** |
| Precision (weighted) | 0.99 |
| Recall (weighted) | 0.99 |
| F1‑Score (weighted) | 0.99 |

**Important Note**: This high accuracy is obtained under **Subject‑Dependent (SD) evaluation**, where samples from the same subject appear in both training and test sets. This causes **subject‑wise data leakage**—the model learns to recognize individual EEG signatures rather than generalizable emotion patterns. LibEER explicitly warns against interpreting SD results as true cross‑subject generalization.

Under the correct **Subject‑Independent (SI)** protocol (Leave‑One‑Subject‑Out), the expected accuracy would drop to approximately **60–70%**. The dataset used here lacks subject identifiers, so SI validation is not currently feasible.

## 实验结果

| 指标 | 数值 |
| :--- | :--- |
| 测试准确率 | **99.5%** |
| 精确率（加权） | 0.99 |
| 召回率（加权） | 0.99 |
| F1‑Score（加权） | 0.99 |

**重要说明**：这一高准确率是在 **受试者依赖（SD）评估** 下获得的，即同一受试者的样本会同时出现在训练集和测试集中。这导致了 **被试数据泄露**——模型学会的是识别个体脑电特征，而非可泛化的情绪模式。LibEER 明确指出，不应将 SD 结果解释为真正的跨被试泛化能力。

若采用正确的 **受试者独立（SI）** 协议（留一被试交叉验证），准确率预计将降至约 **60–70%**。由于当前数据集缺少受试者标识，SI 验证暂时无法实施。

---

## Limitations

1. **Evaluation Protocol** – Only Subject‑Dependent (SD) validation is performed due to the absence of subject IDs in the dataset. Cross‑subject generalization cannot be assessed.
2. **Preprocessing** – The dataset provides pre‑extracted features (2,548‑dim); standard EEG preprocessing (bandpass filtering, differential entropy) is not applied.
3. **Model Architecture** – The 1D‑CNN captures only temporal patterns. Spatial electrode relationships (as modeled by DGCNN) are not utilized.

## 局限性

1. **评估协议** – 由于数据集缺少受试者 ID，仅进行了受试者依赖（SD）验证，无法评估跨被试泛化能力。
2. **预处理** – 数据集提供的是预提取的特征向量（2548 维），未应用标准 EEG 预处理流程（带通滤波、微分熵提取）。
3. **模型架构** – 1D‑CNN 仅捕捉时序特征，未利用电极间的空间关系（如 DGCNN 中的图卷积）。

---

## Future Improvements

- Migrate to a dataset with **real subject labels** (e.g., SEED, DEAP) to implement **LOSO cross‑validation**
- Apply full EEG preprocessing: **1–50 Hz bandpass filtering** and **differential entropy** extraction
- Replace 1D‑CNN with **DGCNN** to incorporate graph‑based spatial information

## 未来改进方向

- 迁移至包含 **真实受试者标签** 的数据集（如 SEED、DEAP），实现 **留一被试交叉验证（LOSO）**
- 补全 EEG 预处理流程：**1–50 Hz 带通滤波** 与 **微分熵（DE）** 特征提取
- 将 1D‑CNN 替换为 **DGCNN**，引入图卷积以建模电极空间关系

---

## Project Structure

- eeg_emotion_libeer.ipynb   # Main Colab notebook
- data/                      # Auto‑downloaded dataset
- README.md

## 项目结构

- eeg_emotion_libeer.ipynb   # 主 Colab Notebook
- data/                      # 自动下载的数据集
- README.md

---

## Reference

- **LibEER**: *A Comprehensive Benchmark and Algorithm Library for EEG‑based Emotion Recognition*  
  IEEE Transactions on Affective Computing, 2025  
  [arXiv:2410.09767](https://arxiv.org/abs/2410.09767) | [GitHub](https://github.com/XJTU-EEG/LibEER)

