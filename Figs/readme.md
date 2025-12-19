# Figures – Federated Driver Digital Twin (FDDT)

This directory contains **all figures used in the paper**:

> **Federated Driver Digital Twin (FDDT): Secure, Adaptive, and Edge-Deployable Private Models for Connected Vehicles**  
> *IEEE Transactions on Affective Computing*

Each figure is reproduced here exactly as referenced in the manuscript and is briefly described below for clarity and reuse.

---

## Figure 1 – End-to-End FDDT Pipeline

**File:** `overall-pipeline.png`

![Overall Pipeline](overall-pipeline.png)

**Description:**  
Illustrates the complete Federated Driver Digital Twin (FDDT) workflow, including SIGNet-based latent digital twin learning, latent-space identity evaluation via IDInferNet, and synthetic-data-driven assessment using DT-GDIN. The figure highlights privacy-preserving data flow and edge deployment compatibility.

---

## Figure 2 – Model Architectures and Digital Twin Variants

**File:** `architectures.png`

![Architectures](architectures.png)

**Description:**  
Shows the architectural evolution of SIGNet variants:  
- SIGNet-B (baseline CVAE)  
- SIGNet-S (β-VAE with stabilized latent regularization)  
- SIGNet-C (contrastive latent learning)  
- **SIGNet-DT (proposed hierarchical digital twin)**  

Also includes IDInferNet and DT-GDIN evaluation networks.

---

## Figure 3 – Driver-Wise Sample Distribution

**File:** `Samples_Per_Driver.png`

![Samples Per Driver](Samples_Per_Driver.png)

**Description:**  
Visualizes the number of samples available per driver in the DD’17 dataset, confirming balanced driver representation for training and evaluation.

---

## Figure 4 – Trip-Wise Statistical Summary

**File:** `Trip-Wise_Summary.png`

![Trip Summary](Trip-Wise_Summary.png)

**Description:**  
Summarizes trip-level statistics across drivers, highlighting inter-driver variability and temporal diversity in driving behavior.

---

## Figure 5 – Latent Space Visualization (PCA)

**File:** `latent_pca.png`

![Latent PCA](latent_pca.png)

**Description:**  
PCA projection of the SIGNet-DT latent space. Each cluster corresponds to a driver-specific digital twin state, demonstrating strong identity separability and latent consistency.

---

## Figure 6 – Identity Inference Performance Comparison

**File:** `driver_id_comparis.png`

![Driver ID Comparison](driver_id_comparis.png)

**Description:**  
Compares driver identification performance between classical machine-learning baselines trained on raw sensor data and IDInferNet operating on SIGNet latent representations.

---

## Figure 7 – Digital-Twin Generated Data Evaluation (DT-GDIN)

**File:** `dtgdin_evaluation.png`

![DT-GDIN Evaluation](dtgdin_evaluation.png)

**Description:**  
Evaluates identity consistency, robustness, and utility retention when classifiers are trained exclusively on digital-twin–generated samples.

---

## Figure 8 – IDInferNet Latent Distribution Analysis

**File:** `idinfernet_histogram.png`

![IDInferNet Histogram](idinfernet_histogram.png)

**Description:**  
Histogram analysis of latent embeddings used by IDInferNet, illustrating compactness and stability of learned driver-specific representations.

---

## Figure 9 – Edge Deployment and Efficiency Metrics

**File:** `edge_metrics.png`

![Edge Metrics](edge_metrics.png)

**Description:**  
Reports inference latency, FLOPs, model size, memory usage, and energy consumption across SIGNet variants, demonstrating real-time feasibility on edge devices.

---

## Usage Notes

- All figures are **paper-aligned** and can be directly referenced in documentation or presentations.
- Paths are relative and render correctly on GitHub.
- No post-processing or resizing is applied.

---

## License

All figures are released under the **Apache License 2.0**, consistent with the repository license.

---

## Citation

If you reuse these figures, please cite the original paper:

```bibtex
@article{FDDT2026,
  title={Federated Driver Digital Twin: Secure, Adaptive, and Edge Deployable Private Models for Connected Vehicles},
  author={Khan, Ajmal and Khan, Misha Urooj and Suleman, Ahmad and Kaleem, Zeeshan},
  journal={IEEE Transactions on Affective Computing},
  year={2026}
}
