<p align="center">
  <h1 align="center">
    <img src="media/logo.png" width="50" style="vertical-align: middle; margin-right: 8px;">
    IMKD: Intensity-Aware Multi-Level Knowledge Distillation for Camera–Radar Fusion
  </h1>

  <p align="center">
    <a href="#"><strong>Shashank Mishra</strong></a> ·
    <a href="#"><strong>Karan Patil</strong></a> ·
    <a href="#"><strong>Didier Stricker</strong></a> ·
    <a href="#"><strong>Jason Rambach</strong></a>
  </p>

  <p align="center"><strong>WACV 2026</strong></p>

  <h3 align="center">
    <a href="#">Project Page</a> |
    <a href="#">Dataset</a> |
    <a href="#">Paper</a> |
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

## 🔧 Getting Started
**Code and models will be made public soon.**

## Contact
You can contact the author through email: Shashank.Mishra@dfki.de

## Citing
If you find our work useful, please consider citing:
```BibTeX
@misc{wang2025inpaint360gsefficientobjectaware3d,
      title={Inpaint360GS: Efficient Object-Aware 3D Inpainting via Gaussian Splatting for 360{\deg} Scenes}, 
      author={Shaoxiang Wang and Shihong Zhang and Christen Millerdurai and Rüdiger Westermann and Didier Stricker and Alain Pagani},
      year={2025},
      eprint={2511.06457},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2511.06457}, 
}
