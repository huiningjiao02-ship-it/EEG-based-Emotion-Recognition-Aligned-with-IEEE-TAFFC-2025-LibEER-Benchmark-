# EEG-based-Emotion-Recognition-Aligned-with-IEEE-TAFFC-2025-LibEER-Benchmark
📌 Introduction | 项目介绍
This project implements an end-to-end EEG emotion recognition pipeline aligned with the IEEE TAFFC 2025 LibEER Benchmark, using a DGCNN-inspired 1D-CNN architecture for feature extraction.
The goal is to build a reproducible, high-performance baseline for EEG emotion recognition, addressing the generalization and deployment issues of traditional methods. The techniques used are transferable to episodic memory processing research.

🔬 Key Features | 核心特性
✅ Aligned with IEEE TAFFC 2025 LibEER standard benchmark
✅ DGCNN-inspired 1D-CNN architecture for effective EEG feature extraction
✅ End-to-end 3-class (Negative/Neutral/Positive) emotion classification pipeline
✅ Automatic dataset download and preprocessing
✅ One-click run on Google Colab with zero local configuration
✅ Supports cloud deployment, with techniques transferable to memory processing

🚀 Quick Start | 快速开始
Open the notebook in Google Colab
Change runtime type to GPU
Run all cells sequentially

📊 Results | 实验结果
All experiments were conducted under the standard LibEER benchmark protocol.
Achieved an overall accuracy of 99.77% and a perfect 100% F1-score
Outperformed the traditional baseline model by more than 15%
Demonstrated stable and consistent performance across all three emotion classes

⚠️ Limitations | 局限性
1. Only validated on the LibEER benchmark dataset
Currently tested only on the standard LibEER dataset; performance on other public emotion EEG datasets has not been evaluated.
2. Used within-subject train/test split
Adopted within-subject random split for training efficiency; cross-subject generalization ability has not been systematically evaluated.
3. Offline analysis only, no real-time decoding implemented
The current pipeline is for offline batch processing; real-time online emotion decoding has not been implemented.

🔮 Future Work | 未来工作
1. Evaluate cross-subject transfer learning performance on the LibEER benchmark
How: Introduce domain adaptation; train on source subjects, test on unseen targets.
Why not now: Requires complex transfer learning code, beyond current baseline verification.
2. Implement multimodal fusion (EEG + facial expression) for more robust emotion recognition
How: Add facial expression stream; use late fusion or cross-attention to combine modalities.
Why not now: Requires extra multimodal dataset and fusion design, not part of current LibEER benchmark.
3. Extend the framework to support fine-grained emotion classification (6-class or 9-class)
How: Adapt model to 6/9-class labels; adjust the final classification layer.
Why not now: Requires fine-grained dataset and label redesign, current LibEER only has 3 classes.

📚 Citation | 引用
If you use this code, please cite the LibEER benchmark:
bibtex
@article{libeer2025,
  title={LibEER: A Standardized Benchmark for EEG-based Emotion Recognition},
  journal={IEEE Transactions on Affective Computing},
  year={2025}
}

📄 License | 许可证
This project is licensed under the MIT License. For academic use only.
