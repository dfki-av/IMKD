# IMKD: Intensity-Aware Multi-Level Knowledge Distillation for Camera–Radar Fusion

<p align="center">
  <img src="media/architecture.png" alt="IMKD architecture" width="900">
</p>

<p align="center">
  <a href="https://arxiv.org/abs/2512.15581"><img src="https://img.shields.io/badge/WACV-2026-blue" alt="WACV 2026"></a>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/shashank-mishra-73190b18/"><strong>Shashank Mishra</strong></a> ·
  <a href="https://www.linkedin.com/in/karanpatil0612/"><strong>Karan Patil</strong></a> ·
  <a href="https://scholar.google.com/citations?hl=en&user=ImhXfxgAAAAJ"><strong>Didier Stricker</strong></a> ·
  <a href="https://www.linkedin.com/in/jason-rambach-03a9b258/"><strong>Jason Rambach</strong></a>
</p>

<p align="center">
  <a href="#">Project Page</a> |
  <a href="https://arxiv.org/abs/2512.15581">Paper</a> |
  <a href="#">Models</a>
</p>

**IMKD** introduces a three-stage, intensity-aware multi-level knowledge distillation pipeline for high-performance Radar–Camera 3D object detection without requiring LiDAR at inference time.

---

## 🚀 Overview

High-performance Radar–Camera 3D object detection can be achieved through knowledge distillation without using LiDAR at inference time. However, existing distillation methods often transfer modality-specific features directly to each sensor, potentially distorting their unique characteristics and diminishing their strengths.

We propose **IMKD**, a radar–camera fusion framework based on **multi-level, intensity-aware knowledge distillation** that maintains each sensor’s intrinsic properties while enhancing their complementarity.

---

## ✨ Key Contributions

IMKD introduces a **three-stage distillation strategy**:

1. **LiDAR → Radar intensity-aware feature distillation**  
   Enhances radar representations with detailed structural cues.

2. **LiDAR → Fused intensity-guided distillation**  
   Selectively emphasizes valuable geometric and depth information at the fusion layer, encouraging complementary sensor interaction rather than strict alignment.

3. **Camera–Radar intensity-guided fusion mechanism**  
   Facilitates improved calibration and alignment between modalities.

---

## 📊 Main Results

Experiments on the **nuScenes** benchmark show that IMKD achieves **67.0% NDS** and **61.0% mAP**, surpassing all previous distillation-based radar–camera fusion approaches.

### Knowledge Distillation Performance on nuScenes

This section compares existing knowledge distillation (KD) methods for 3D object detection on the nuScenes test set. We focus on the impact of different distillation strategies while using each method’s best reported backbone and input resolution.

| Method       | Input   | KD        | NDS ↑    | mAP ↑    | mATE ↓    | mASE ↓    | mAOE ↓    | mAVE ↓    | mAAE ↓    |
| ------------ | ------- | --------- | -------- | -------- | --------- | --------- | --------- | --------- | --------- |
| UVTR         | C       | L2C       | 52.2     | 45.2     | 0.612     | 0.256     | 0.385     | 0.664     | 0.125     |
| BEVDistill   | C       | LC2C      | 59.4     | 49.8     | 0.472     | 0.247     | 0.378     | 0.326     | 0.125     |
| UniDistill   | C       | L2C       | 39.3     | 29.6     | 0.637     | 0.257     | 0.492     | 1.084     | 0.167     |
| LabelDistill | C       | LL◇2C     | 61.0     | 52.6     | 0.443     | 0.252     | 0.339     | 0.370     | 0.136     |
| X3KD         | C       | LC2C      | 56.1     | 45.6     | 0.506     | 0.253     | 0.414     | 0.366     | 0.131     |
| **X3KD**     | **C+R** | **L2CR**  | 55.3     | 44.1     | –         | –         | –         | –         | –         |
| CRKD         | C+R     | LC2CR     | 58.7     | 48.7     | 0.404     | 0.253     | 0.425     | 0.376     | 0.111     |
| **IMKD**     | **C+R** | **LL◇2M** | **67.0** | **61.0** | **0.401** | **0.249** | **0.305** | **0.238** | **0.102** |

L = LiDAR, L◇ = Label, C = Camera, R = Radar, M = Merged (Camera + Radar).

---

### 3D Object Detection Performance on nuScenes (Validation Set)

This section compares camera- and radar-based 3D object detection methods on the nuScenes validation set under **fair evaluation settings**. All methods exclude future frames, test-time augmentation, and CBGS to ensure a consistent comparison. Results are grouped by backbone and image resolution.

| Method       | Input   | Backbone       | Image Size     | NDS ↑    | mAP ↑    | mATE ↓    | mASE ↓    | mAOE ↓    | mAVE ↓    | mAAE ↓    |
| ------------ | ------- | -------------- | -------------- | -------- | -------- | --------- | --------- | --------- | --------- | --------- |
| BEVDet       | C       | ResNet-50      | 256 × 704      | 39.2     | 31.2     | 0.691     | 0.272     | 0.523     | 0.909     | 0.247     |
| BEVDepth     | C       | ResNet-50      | 256 × 704      | 47.5     | 35.1     | 0.639     | 0.267     | 0.479     | 0.428     | 0.198     |
| RC-BEVFusion | C+R     | ResNet-50      | 256 × 704      | 52.5     | 43.4     | 0.511     | 0.270     | 0.527     | 0.421     | 0.182     |
| SOLOFusion   | C       | ResNet-50      | 256 × 704      | 53.4     | 42.7     | 0.567     | 0.274     | 0.411     | 0.252     | 0.188     |
| StreamPETR   | C       | ResNet-50      | 256 × 704      | 54.0     | 43.2     | 0.581     | 0.272     | 0.413     | 0.295     | 0.195     |
| SparseBEV    | C       | ResNet-50      | 256 × 704      | 54.5     | 43.2     | 0.606     | 0.274     | 0.387     | 0.251     | 0.186     |
| CRN          | C+R     | ResNet-50      | 256 × 704      | 56.0     | 49.0     | 0.487     | 0.277     | 0.542     | 0.344     | 0.197     |
| RCBEVDet     | C+R     | ResNet-50      | 256 × 704      | 56.8     | 45.3     | 0.486     | 0.285     | 0.404     | **0.220** | 0.192     |
| CRT-Fusion   | C+R     | ResNet-50      | 256 × 704      | 57.2     | 50.0     | 0.499     | 0.277     | 0.531     | 0.261     | 0.192     |
| **IMKD**     | **C+R** | **ResNet-50**  | **256 × 704**  | **61.0** | **51.6** | **0.444** | **0.259** | **0.384** | 0.229     | **0.160** |
| RICCARDO     | C+R     | ResNet-101     | 1408 × 512     | 62.2     | **54.4** | 0.481     | 0.266     | **0.325** | 0.237     | 0.189     |
| **IMKD**     | **C+R** | **ResNet-101** | **1408 × 512** | **62.7** | 53.9     | **0.417** | **0.255** | 0.348     | **0.235** | **0.158** |

---

## 🔧 Getting Started

- [ ] Release code
- [ ] Release config files
- [ ] Release model

---

## 📧 Contact

For questions, please contact [Shashank.Mishra@dfki.de](mailto:Shashank.Mishra@dfki.de).

---

## 📖 Citation

If you find our work useful, please consider citing:

```bibtex
@inproceedings{mishra2026imkd,
  title={IMKD: Intensity-Aware Multi-Level Knowledge Distillation for Camera-Radar Fusion},
  author={Mishra, Shashank and Patil, Karan and Stricker, Didier and Rambach, Jason},
  booktitle={2026 IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
  pages={6027--6038},
  year={2026},
  organization={IEEE}
}
```
