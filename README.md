
# Federated Driver Digital Twin (FDDT)

## Secure, Adaptive, and Edge-Deployable Private Models for Connected Vehicles

================================================================================

This repository contains the **complete, exhaustive, and publication-faithful research artifacts**
for the paper:

**Federated Driver Digital Twin (FDDT): Secure, Adaptive, and Edge-Deployable Private Models for Connected Vehicles**  
*IEEE Transactions on Affective Computing*

================================================================================

## TABLE OF CONTENTS

1. Introduction  
2. Research Motivation  
3. Contributions  
4. Repository Structure  
5. System Overview  
6. FDDT Framework  
   6.1 SIGNet Family  
   6.2 IDInferNet  
   6.3 DT-GDIN  
7. Architectural Details  
8. Dataset Description  
9. Training Protocol  
10. Evaluation Metrics (Complete)  
11. Latent Space Analysis  
12. Latent Consistency & Separability Results  
13. Identity Inference Results  
14. Digital Twin Generated Data Evaluation  
15. Edge Deployment & Efficiency  
16. Federated Learning Properties  
17. Privacy Analysis  
18. Comparative Evaluation with Literature  
19. Reproducibility Checklist  
20. Limitations  
21. License  
22. Citation  

================================================================================

## 1. Introduction

Modern intelligent transportation systems increasingly rely on behavioral modeling of drivers.
However, existing solutions face critical limitations related to privacy, scalability, and deployment.

The **Federated Driver Digital Twin (FDDT)** framework introduces a generative,
federated-compatible digital twin that learns **driver-specific behavioral representations**
without requiring raw data sharing.

================================================================================

## 2. Research Motivation

Existing driver modeling methods typically suffer from:

- Centralized training requiring raw data aggregation
- High privacy leakage risk
- Lack of generative behavioral abstraction
- Poor adaptability to edge devices
- Weak identity consistency across sessions

FDDT resolves these limitations by combining:

- Generative modeling
- Latent identity abstraction
- Federated learning compatibility
- Edge-aware deployment constraints

<table> <thead> <tr> <th><b>Method</b></th> <th><b>Year</b></th> <th><b>Federated<br>Learning</b></th> <th><b>Raw Data<br>Sharing</b></th> <th><b>Digital<br>Twin</b></th> <th><b>Identity<br>Preservation</b></th> <th><b>Edge<br>Ready</b></th> <th><b>Key Limitations</b></th> </tr> </thead> <tbody> <tr> <td><b>STCN-ID</b></td> <td>2022</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#ffd6d6">Yes</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#fff2cc">🟡 Weak</td> <td style="background:#fff2cc">🟡 Partial</td> <td>No privacy preservation, centralized training</td> </tr> <tr> <td><b>DG-DriverID</b></td> <td>2023</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#ffd6d6">Yes</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#c6efce">🟢 Strong</td> <td style="background:#fff2cc">🟡 Partial</td> <td>Lacks federated and generative modeling</td> </tr> <tr> <td><b>FL-Drive</b></td> <td>2023</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#fff2cc">🟡 Moderate</td> <td style="background:#fff2cc">🟡 Partial</td> <td>Communication heavy, no digital twin abstraction</td> </tr> <tr> <td><b>FedTwin</b></td> <td>2022</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#c6efce">No</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#fff2cc">🟡 Moderate</td> <td style="background:#fff2cc">🟡 Partial</td> <td>Weak identity consistency, generic IoT focus</td> </tr> <tr> <td><b>SFLAAP</b></td> <td>2023</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#c6efce">No</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#c6efce">🟢 Strong</td> <td style="background:#fff2cc">🟡 Partial</td> <td>High coordination complexity at edge</td> </tr> <tr> <td><b>FedDriveScore</b></td> <td>2024</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#c6efce">No</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#c6efce">🟢 Strong</td> <td style="background:#c6efce">🟢 Yes</td> <td>Requires large participant pool</td> </tr> <tr> <td><b><span style="color:#0b5394;">⭐ FDDT (Proposed)</span></b></td> <td><b>2026</b></td> <td style="background:#c6efce"><b>🟢 Yes</b></td> <td style="background:#c6efce"><b>No</b></td> <td style="background:#c6efce"><b>🟢 Full</b></td> <td style="background:#c6efce"><b>🟢 Explicit</b></td> <td style="background:#c6efce"><b>🟢 Yes</b></td> <td><b>None observed under evaluated settings</b></td> </tr> </tbody> </table>

================================================================================

## 3. Contributions

1. First federated generative driver digital twin framework
2. Hierarchical latent disentanglement of static and temporal behavior
3. Identity inference without raw sensor access
4. Synthetic digital twin data with full utility retention
5. Comprehensive evaluation across 21+ metrics
6. Real-time edge deployment validation

================================================================================

## 4. Repository Structure

```
Federated-Driver-Digital-Twin-FDDT/
│
├── Codes/
│   ├── signet/
│   ├── idinfernet/
│   ├── dtgdin/
│   ├── federated/
│   └── edge/
│
├── DT_Driver_Wise_Data/
├── Figs/
│   ├── overall-pipeline.png
│   ├── architectures.png
│   ├── latent_pca.png
│   ├── idinfernet_histogram.png
│   ├── driver_id_comparis.png
│   ├── edge_metrics.png
│
├── Results/
│   ├── latent_metrics.csv
│   ├── idinfernet_results.csv
│   ├── dtgdin_results.csv
│
├── LICENSE
└── README.md
```

================================================================================

## 5. System Overview

The FDDT system consists of three interacting components:

1. SIGNet – generative digital twin encoder/decoder
2. IDInferNet – latent identity inference
3. DT-GDIN – synthetic data evaluation

![Overall Pipeline](Figs/overall-pipeline.png)

================================================================================

## 6. FDDT Framework

### 6.1 SIGNet — Stochastic Identity-Conditioned Generative Network

SIGNet is implemented as a Conditional Variational Autoencoder (CVAE).

Variants:

- SIGNet-B: baseline CVAE
- SIGNet-S: β-VAE with latent regularization
- SIGNet-C: contrastive latent learning
- SIGNet-DT: hierarchical digital twin (proposed)

### 6.2 IDInferNet

A lightweight classifier operating strictly on latent embeddings.

### 6.3 DT-GDIN

A synthetic-data-only evaluation framework measuring digital twin fidelity.

================================================================================

## 7. Architectural Details

![Architectures](Figs/architectures.png)

### Table: Architectural Comparison of SIGNet Variants

| Property | SIGNet-B | SIGNet-S | SIGNet-C | SIGNet-DT |
|--------|----------|----------|----------|-----------|
| Conditional Generative | ✓ | ✓ | ✓ | ✓ |
| β-Regularization | – | ✓ | ✓ | ✓ |
| Contrastive Learning | – | – | ✓ | – |
| Latent Disentanglement | – | ○ | ○ | ✓ |
| Static / Temporal Split | – | – | – | ✓ |
| Hierarchical Latents | – | – | – | ✓ |
| Digital Twin Fidelity | – | ○ | ○ | ✓ |

================================================================================

## 8. Dataset Description

Dataset: DD’17 Driving Dataset

- 52 vehicular sensor signals
- 23+ hours of real-world driving
- Multiple drivers
- Identical routes

![Samples Per Driver](Figs/Samples_Per_Driver.png)  
![Trip Summary](Figs/Trip-Wise_Summary.png)

================================================================================

## 9. Training Protocol

- Driver-wise segmentation
- Fixed train/validation/test split
- Adam optimizer
- Deterministic seeds
- Identical classifiers across experiments

================================================================================

## 10. Evaluation Metrics (COMPLETE)

### Training Objectives
- Reconstruction Error
- KL Divergence

### Latent Metrics
- Cosine Similarity
- Euclidean Distance
- Variance Trace
- Coefficient of Variation
- Centroid Distance
- Centroid Cosine Similarity
- Fisher Ratio
- Silhouette Score
- Davies–Bouldin Index

### Identity Metrics
- Precision
- Recall
- F1 Score
- Worst-Class Recall

### Digital Twin Utility
- Accuracy
- Macro-F1
- Balanced Accuracy
- Utility Retention Ratio (URR)

### Edge Metrics
- Latency
- FLOPs
- Model Size
- Energy Consumption

================================================================================

## 11. Latent Space Analysis

![Latent PCA](Figs/latent_pca.png)

SIGNet-DT exhibits tight, well-separated identity clusters.

================================================================================

## 12. Latent Consistency & Separability Results

| Model | Cosine | Euclid | Var Trace | Fisher | Silhouette | DB |
|------|--------|--------|-----------|--------|------------|----|
| SIGNet-B | 0.8353 | 0.8887 | 0.5549 | 0.0462 | 0.2651 | 2.3625 |
| SIGNet-S | 0.8237 | 1.3613 | 1.1969 | 11.4954 | 0.2546 | 2.2877 |
| SIGNet-C | 0.8835 | 0.4455 | 0.1279 | 24.8706 | 0.5203 | 0.8285 |
| SIGNet-DT | 0.9793 | 0.1053 | 0.0087 | 48.2169 | 0.8936 | 0.1609 |

================================================================================

## 13. Identity Inference Results

![Driver ID Comparison](Figs/driver_id_comparis.png)

SIGNet-DT and IDInferNet achieve near-perfect identity inference without raw data.

================================================================================

## 14. Digital Twin Generated Data Evaluation

| Model | Accuracy | Macro-F1 | Balanced Acc | Worst Recall | URR |
|------|----------|----------|--------------|--------------|-----|
| SIGNet-B | 0.664 | 0.61 | 0.66 | 0.58 | 0.74 |
| SIGNet-S | 0.603 | 0.60 | 0.60 | 0.53 | 0.62 |
| SIGNet-C | 0.651 | 0.65 | 0.65 | 0.52 | 0.67 |
| SIGNet-DT | ≥0.99 | ≥0.99 | ≥0.99 | ≥0.99 | 1.00 |

================================================================================

## 15. Edge Deployment & Efficiency

![Edge Metrics](Figs/edge_metrics.png)

Validated under pruning and quantization with real-time inference.

================================================================================

## 16. Federated Learning Properties

- No raw data sharing
- Latent-only communication
- Low bandwidth overhead
- Client-side personalization
- 
## 17. Privacy Analysis

- Implicit identity conditioning
- No raw sensor leakage
- Synthetic-only benchmarking
- Minimal attack surface

<table> <thead> <tr> <th><b>Framework</b></th> <th><b>Federated<br>Learning</b></th> <th><b>Raw Data<br>Shared</b></th> <th><b>Latent-Only<br>Training</b></th> <th><b>Digital<br>Twin</b></th> <th><b>Communication<br>Overhead</b></th> <th><b>Privacy Risk</b></th> </tr> </thead> <tbody> <tr> <td>Centralized DL</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#ffd6d6">Yes</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#ffd6d6">High</td> <td style="background:#ffd6d6">High</td> </tr> <tr> <td>FL-Drive</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#ffd6d6">🔴 No</td> <td style="background:#fff2cc">Medium</td> <td style="background:#fff2cc">Medium</td> </tr> <tr> <td>FedTwin</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#c6efce">No</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#fff2cc">Medium</td> <td style="background:#fff2cc">Low</td> </tr> <tr> <td>SFLAAP</td> <td style="background:#c6efce">🟢 Yes</td> <td style="background:#c6efce">No</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#fff2cc">🟡 Partial</td> <td style="background:#fff2cc">Medium</td> <td style="background:#c6efce">Low</td> </tr> <tr> <td><b><span style="color:#0b5394;">⭐ FDDT (Proposed)</span></b></td> <td style="background:#c6efce"><b>🟢 Yes</b></td> <td style="background:#c6efce"><b>No</b></td> <td style="background:#c6efce"><b>🟢 Yes</b></td> <td style="background:#c6efce"><b>🟢 Full</b></td> <td style="background:#c6efce"><b>Low</b></td> <td style="background:#c6efce"><b>Minimal</b></td> </tr> </tbody> </table>

================================================================================

## 18. Comparative Evaluation with Literature

SIGNet-DT outperforms prior driver identification and digital twin frameworks
in accuracy, robustness, and privacy preservation.

<table> <thead> <tr> <th><b>Model</b></th> <th><b>Year</b></th> <th><b>Dataset</b></th> <th><b>Accuracy</b></th> <th><b>F1-Score</b></th> <th><b>Latency (ms)</b></th> <th><b>Privacy</b></th> <th><b>Remarks</b></th> </tr> </thead> <tbody> <tr> <td>STCN-ID</td> <td>2022</td> <td>Steering Dataset</td> <td style="background:#fff2cc">86.7%</td> <td style="background:#fff2cc">0.82</td> <td style="background:#c6efce">21.3</td> <td style="background:#ffd6d6">🔴 No</td> <td>Centralized, no personalization</td> </tr> <tr> <td>DG-DriverID</td> <td>2023</td> <td>DD’17</td> <td style="background:#fff2cc">91.3%</td> <td style="background:#fff2cc">0.86</td> <td style="background:#fff2cc">35.5</td> <td style="background:#ffd6d6">🔴 No</td> <td>Limited generalization</td> </tr> <tr> <td>FL-Drive</td> <td>2023</td> <td>Federated Dataset</td> <td style="background:#fff2cc">90.1%</td> <td style="background:#fff2cc">0.87</td> <td style="background:#fff2cc">31.6</td> <td style="background:#c6efce">🟢 Yes</td> <td>High communication overhead</td> </tr> <tr> <td>FedDriveScore</td> <td>2024</td> <td>Cross-Vehicle FL</td> <td style="background:#c6efce">95.2%</td> <td style="background:#c6efce">0.93</td> <td style="background:#c6efce">25.7</td> <td style="background:#c6efce">🟢 Yes</td> <td>Needs large federation</td> </tr> <tr> <td>SIGNet-B</td> <td>2026</td> <td>DD’17</td> <td style="background:#fff2cc">92.5%</td> <td style="background:#fff2cc">0.89</td> <td style="background:#c6efce">24.1</td> <td style="background:#c6efce">🟢 Yes</td> <td>Weak inter-driver separation</td> </tr> <tr> <td>SIGNet-C</td> <td>2026</td> <td>DD’17</td> <td style="background:#c6efce">97.2%</td> <td style="background:#c6efce">0.96</td> <td style="background:#fff2cc">30.2</td> <td style="background:#c6efce">🟢 Yes</td> <td>Higher training complexity</td> </tr> <tr> <td><b><span style="color:#0b5394;">⭐ SIGNet-DT (Proposed)</span></b></td> <td><b>2026</b></td> <td><b>DD’17</b></td> <td style="background:#c6efce"><b>99.1%</b></td> <td style="background:#c6efce"><b>0.99</b></td> <td style="background:#fff2cc">32.8</td> <td style="background:#c6efce"><b>🟢 Yes</b></td> <td><b>Best overall performance</b></td> </tr> <tr> <td><b>IDInferNet</b></td> <td>2026</td> <td>Latent Only</td> <td style="background:#c6efce">98.9%</td> <td style="background:#c6efce">0.98</td> <td style="background:#c6efce"><b>15.2</b></td> <td style="background:#c6efce">🟢 Yes</td> <td>Ultra-lightweight inference</td> </tr> </tbody> </table> 
================================================================================

## 19. Reproducibility Checklist

- Fixed splits ✓
- Deterministic seeds ✓
- Logged checkpoints ✓
- Metric scripts included ✓

================================================================================

## 20. Limitations

- Slightly larger model size
- Higher training complexity
- Requires high-quality sensor synchronization

================================================================================

## 21. License

Apache License 2.0

================================================================================

## 22. Citation

```bibtex
@article{FDDT2026,
  title={Federated Driver Digital Twin: Secure, Adaptive, and Edge Deployable Private Models for Connected Vehicles},
  author={Khan, Ajmal and Khan, Misha Urooj and Suleman, Ahmad and Kaleem, Zeeshan},
  journal={IEEE Transactions on Affective Computing},
  year={2026}
}
```
