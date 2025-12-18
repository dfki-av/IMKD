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
