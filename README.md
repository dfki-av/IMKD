<p align="center">
  <h1 align="center">
    IMKD: Intensity-Aware Multi-Level Knowledge Distillation for Camera–Radar Fusion
  </h1>

  <p align="center">
    <a href="https://www.linkedin.com/in/shashank-mishra-73190b18/"><strong>Shashank Mishra</strong></a> ·
    <a href="https://www.linkedin.com/in/karanpatil0612/"><strong>Karan Patil</strong></a> ·
    <a href="https://scholar.google.com/citations?hl=en&user=ImhXfxgAAAAJ"><strong>Didier Stricker</strong></a> ·
    <a href="https://www.linkedin.com/in/jason-rambach-03a9b258/"><strong>Jason Rambach</strong></a>
  </p>

  <p align="center"><strong>WACV 2026</strong></p>

  <h3 align="center">
    <a href="#">Project Page</a> |
    <a href="https://arxiv.org/abs/2512.15581">Paper</a> |
    <a href="#">Models</a>
  </h3>
</p>

---

<!-- <p align="center">
  <img src="media/arch.jpg" alt="Teaser" width="80%">
</p> -->

<p align="center">
  IMKD introduces a three-stage, intensity-aware multi-level knowledge distillation pipeline for high-performance Radar–Camera 3D object detection without requiring LiDAR at inference time.
</p>

---

## 🚀 Abstract

High-performance Radar–Camera 3D object detection can be achieved through knowledge distillation without using LiDAR at inference time. However, existing distillation methods often transfer modality-specific features directly to each sensor, potentially distorting their unique characteristics and diminishing their strengths.

We propose **IMKD**, a radar–camera fusion framework based on **multi-level, intensity-aware knowledge distillation** that maintains each sensor’s intrinsic properties while enhancing their complementarity.

IMKD introduces a **three-stage distillation strategy**:

1. **LiDAR → Radar intensity-aware feature distillation**  
   Enhances radar representations with detailed structural cues.

2. **LiDAR → Fused intensity-guided distillation**  
   Selectively emphasizes valuable geometric and depth information at the fusion layer, encouraging complementary sensor interaction rather than strict alignment.

3. **Camera–Radar intensity-guided fusion mechanism**  
   Facilitates improved calibration and alignment between modalities.

Experiments on the **nuScenes** benchmark show that IMKD achieves:  
- **67.0% NDS**  
- **61.0% mAP**  

surpassing all previous distillation-based radar–camera fusion approaches.

Our code and models will be publicly released.

---

## 🏗️ Architecture

<p align="center">
  <img src="media/architecture.png" alt="Architecture" width="90%">
</p>

---

## Knowledge Distillation Performance on nuScenes

This section compares existing knowledge distillation (KD) methods for 3D object detection on the nuScenes test set. We focus on the impact of different distillation strategies while using each method’s best reported backbone and input resolution.

| Method | Input | KD | NDS ↑ | mAP ↑ | mATE ↓ | mASE ↓ | mAOE ↓ | mAVE ↓ | mAAE ↓ |
|------|------|------|------|------|------|------|------|------|------|
| UVTR (Li et al. 2022) | C | L2C | 52.2 | 45.2 | 0.612 | 0.256 | 0.385 | 0.664 | 0.125 |
| BEVDistill (Chen et al. 2022) | C | LC2C | 59.4 | 49.8 | 0.472 | 0.247 | 0.378 | 0.326 | 0.125 |
| UniDistill (Zhou et al. 2023) | C | L2C | 39.3 | 29.6 | 0.637 | 0.257 | 0.492 | 1.084 | 0.167 |
| LabelDistill (Kim et al. 2024) | C | LL◇2C | 61.0 | 52.6 | 0.443 | 0.252 | 0.339 | 0.370 | 0.136 |
| X3KD (Klingner et al. 2023) | C | LC2C | 56.1 | 45.6 | 0.506 | 0.253 | 0.414 | 0.366 | 0.131 |
| **X3KD (Klingner et al. 2023)** | **C+R** | **L2CR** | 55.3 | 44.1 | – | – | – | – | – |
| CRKD (Zhao et al. 2024) | C+R | LC2CR | 58.7 | 48.7 | 0.404 | 0.253 | 0.425 | 0.376 | 0.111 |
| **IMKD (Ours)** | **C+R** | **LL◇2M** | **67.0** | **61.0** | **0.401** | **0.249** | **0.305** | **0.238** | **0.102** |

**Notes:**  
L = LiDAR, L◇ = Label, C = Camera, R = Radar, M = Merged (Camera + Radar).  
Arrows indicate whether higher (↑) or lower (↓) values are better.

## 3D Object Detection Performance on nuScenes (Validation Set)

This section compares camera- and radar-based 3D object detection methods on the nuScenes validation set under **fair evaluation settings**. All methods exclude future frames, test-time augmentation, and CBGS to ensure a consistent comparison. Results are grouped by backbone and image resolution.

### ResNet-50 Backbone (BEVDepth-compatible setting)

| Method | Input | Backbone | Image Size | NDS ↑ | mAP ↑ | mATE ↓ | mASE ↓ | mAOE ↓ | mAVE ↓ | mAAE ↓ |
|------|------|---------|-----------|------|------|------|------|------|------|------|
| BEVDet (Huang et al. 2021) | C | ResNet-50 | 256 × 704 | 39.2 | 31.2 | 0.691 | 0.272 | 0.523 | 0.909 | 0.247 |
| BEVDepth (Li et al. 2023) | C | ResNet-50 | 256 × 704 | 47.5 | 35.1 | 0.639 | 0.267 | 0.479 | 0.428 | 0.198 |
| RC-BEVFusion (Stacker et al. 2023) | C+R | ResNet-50 | 256 × 704 | 52.5 | 43.4 | 0.511 | 0.270 | 0.527 | 0.421 | 0.182 |
| SOLOFusion (Park et al. 2022) | C | ResNet-50 | 256 × 704 | 53.4 | 42.7 | 0.567 | 0.274 | 0.411 | 0.252 | 0.188 |
| StreamPETR (Wang et al. 2023) | C | ResNet-50 | 256 × 704 | 54.0 | 43.2 | 0.581 | 0.272 | 0.413 | 0.295 | 0.195 |
| SparseBEV (Liu et al. 2023) | C | ResNet-50 | 256 × 704 | 54.5 | 43.2 | 0.606 | 0.274 | 0.387 | 0.251 | 0.186 |
| CRN (Kim et al. 2023) | C+R | ResNet-50 | 256 × 704 | 56.0 | 49.0 | 0.487 | 0.277 | 0.542 | 0.344 | 0.197 |
| RCBEVDet (Lin et al. 2024) | C+R | ResNet-50 | 256 × 704 | 56.8 | 45.3 | 0.486 | 0.285 | 0.404 | **0.220** | 0.192 |
| CRT-Fusion (Kim et al. 2024) | C+R | ResNet-50 | 256 × 704 | 57.2 | 50.0 | 0.499 | 0.277 | 0.531 | 0.261 | 0.192 |
| **IMKD (Ours)** | **C+R** | **ResNet-50** | **256 × 704** | **61.0** | **51.6** | **0.444** | **0.259** | **0.384** | 0.229 | **0.160** |
| RICCARDO (Long et al. 2025) | C+R | ResNet-101 | 1408 × 512 | 62.2 | **54.4** | 0.481 | 0.266 | **0.325** | 0.237 | 0.189 |
| **IMKD (Ours)** | **C+R** | **ResNet-101** | **1408 × 512** | **62.7** | 53.9 | **0.417** | **0.255** | 0.348 | **0.235** | **0.158** |

**Notes:**  
- C = Camera, R = Radar  
- ↑ / ↓ indicate higher / lower is better  
- Upper block: comparisons restricted to BEVDepth-style ResNet-50 settings  
- Lower block: ResNet-101 with higher image resolution, included for completeness


## 🔧 Getting Started
**Code and models will be made public soon.**

## Contact
You can contact the author through email: Shashank.Mishra@dfki.de

## Citing
If you find our work useful, please consider citing:
```BibTeX
@misc{mishra2025imkdintensityawaremultilevelknowledge,
      title={IMKD: Intensity-Aware Multi-Level Knowledge Distillation for Camera-Radar Fusion}, 
      author={Shashank Mishra and Karan Patil and Didier Stricker and Jason Rambach},
      year={2025},
      eprint={2512.15581},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2512.15581}, 
}
