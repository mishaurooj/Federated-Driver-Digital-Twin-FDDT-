# Federated Driver Digital Twin (FDDT)

Federated Driver Digital Twin (FDDT): Secure, Adaptive, and Edge-Deployable Private Models for Connected Vehicles

This repository provides the official implementation, figures, and experimental results for the paper:

Federated Driver Digital Twin (FDDT): Secure, Adaptive, and Edge Deployable Private Models for Connected Vehicles  
IEEE Transactions on Affective Computing

---

## Repository Structure

Federated-Driver-Digital-Twin-FDDT/
Codes/
DT_Driver_Wise_Data/
Figs/
Results/
LICENSE
README.md

---

## Overview

The project introduces a privacy-preserving, federated, and generative driver digital twin framework that learns compact identity-aware latent representations without sharing raw vehicular sensor data.

---

## Core Components

SIGNet – Conditional Variational Autoencoder for driver digital twins  
IDInferNet – Latent-space identity inference network  
DT-GDIN – Digital-twin generated driver identification network

---

## Figures Included

overall-pipeline.png – End-to-end FDDT pipeline  
architectures.png – SIGNet variants and DT hierarchy  
Samples_Per_Driver.png – Driver-wise data distribution  
Trip-Wise_Summary.png – Trip-level statistics  
latent_pca.png – Latent space PCA visualization  
driver_id_comparis.png – Identity inference comparison  
dtgdin_evaluation.png – DT-generated data evaluation  
edge_metrics.png – Edge deployment profiling  
idinfernet_histogram.png – Latent inference distribution

---

## License

Apache License 2.0

---

## Citation

@article{FDDT2026,
  title={Federated Driver Digital Twin: Secure, Adaptive, and Edge Deployable Private Models for Connected Vehicles},
  author={Khan, Ajmal and Khan, Misha Urooj and Suleman, Ahmad and Kaleem, Zeeshan},
  journal={IEEE Transactions on Affective Computing},
  year={2026}
}
