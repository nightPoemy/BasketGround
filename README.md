
# 🏀 BasketGround: A Multi-dimensional Vision-Language Dataset for Basketball Video Analysis
Basketball Video Analysis

---

## 📌 Overview

We present **BASKETGROUND**, a dataset for **Fine-grained Video Analysis** in basketball videos.

Unlike existing datasets, BASKET focuses on fine-grained semantic understanding in highly dynamic, multi-player sports scenarios. 

Each instance in BASKET is annotated with rich visual and semantic information, including:

- 🧑 Player identity (name, team affiliation, jersey color and number)  
- 🏀 Fine-grained actions and player interactions  
- 📍 Spatial-temporal localization (bounding boxes and temporal segments)
- 🎽 Comprehensive captions   
This benchmark introduces significant challenges due to **occlusions, short duration, and similar appearances among players**, making it a strong testbed for multimodal reasoning.

---

## 🎯 Key Features

- 🔹 **Multi-entity reasoning**: identity + action + spatial grounding  
- 🔹 **Fine-grained annotations**: player name, team, jersey color, number  
- 🔹 **Challenging scenarios**: occlusion, fast motion, multi-player interaction  
- 🔹 **Compositional Semantics** 
- 🔹 **Annotation Reliability**

---


> 📌 *Detailed statistics will be updated upon release.*

---

## 🧠 Task Definition

### 🔹 Task 1: Fine-grained Multi-dimensional Semantic Understanding
Predict player-related attributes:
- Player Name
- Team
- Jersey Color
- Jersey Number

### 🔹Task 2: Visual-Evidence-Based Spatio-Temporal Video Grounding
Given a textual query, localize:
- ⏱ Temporal segment  
- 📦 Spatial region  

---

## 📏 Evaluation Metrics

We propose a unified evaluation framework:

- **VEA (Visual Evidence Accuracy)**
- **mTIoU (mean Temporal IoU)**
- **mVIoU (mean Visual IoU)**

We also evaluate **conditional localization performance under different VEA levels**.

---

## 📂 Dataset Structure

BASKET/
│── videos/
│── annotations/
│ ├── train.json
│ ├── val.json
│ └── test.json
│── metadata/
│── splits/


## 📥 Download

🚧 The dataset will be released upon acceptance.

(Anonymous version for review: [LINK])
