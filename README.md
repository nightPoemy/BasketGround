# BasketGround: A Multi-dimensional Vision-Language Dataset for Basketball Video Analysis

[![Paper](https://img.shields.io/badge/Paper-Arxiv-red)](https://github.com/nightPoemy/BasketGround)
[![Dataset](https://img.shields.io/badge/Dataset-Download-blue)](https://github.com/nightPoemy/BasketGround)
[![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-green)](LICENSE)

**BasketGround** is a semantically augmented basketball video dataset designed to bridge the gap in unified modeling of player identity, action, court location, and natural language. Built upon the basketball subset of [MultiSports](https://github.com/MCG-NJU/MultiSports), it transforms action-oriented tracking data into a multi-dimensional benchmark for fine-grained sports understanding.

---

## 🏀 Dataset Overview

We enrich each player tube with identity, team affiliation, jersey attributes, fine-grained actions, court locations, and natural-language captions.*

### Key Features
- **Multi-dimensional Annotation**: Unlike datasets focusing on isolated tasks, BasketGround unifies:
  - **Who**: Player identity, team affiliation, and jersey details (number/color).
  - **What**: Fine-grained basketball actions (e.g., *Basketball Drive, Block, Pass Steal*).
  - **Where**: Semantic court positions (e.g., *Left Side of the Key, Paint, Corner*).
  - **How**: High-quality basketball-oriented natural language descriptions.

- **Challenging Benchmarks**: Experiments show that representative Large Multimodal Models (LMMs) like GPT-4o and Gemini 2.5 still struggle with fine-grained identity recognition and evidence-grounded localization.

---

## 📊 Dataset Statistics

| Dimension | Count / Categories |
| :--- | :--- |
| **Total Games** | 43 |
| **Video Clips** | 468 |
| **Annotated Instances** | 5,355 |
| **Action Categories** | 12+ (Dribble, Pass, Shot, Screening, etc.) |
| **Language** | 5,355 Human-verified Captions |

---

## 🛠 Benchmark Tasks

### Task 1: Fine-grained Multi-dimensional Semantic Understanding
Evaluates a model's ability to jointly recognize **Identity**, **Action**, and **Court Location** from a single cropped player tube.


| Model                  | Identity | Labels | Location |
|------------------------|----------|--------|----------|
| Gemini 2.5 Flash [7]   | **18.17** | 31.86  | 71.20    |
| GPT-4o [20]            | -        | **33.83** | **73.80** |
| Qwen3-VL-8B-Instruct [3] | 12.51    | 33.60  | 69.87    |


### Task 2: Visual-Evidence-Based Spatio-Temporal Video Grounding (STVG)
A more challenging task where the model is given an incomplete query (e.g., *"The player in red shoots..."*) and must:
1. **Recover Missing Evidence**: Infer attributes like player name or team from the video.
2. **Spatio-Temporal Localization**: Precisely ground the player's bounding box sequence across the video.

| Model                | mVEA  | mtIoU | mvIoU | mtIoU@0.50 | mvIoU@0.50 | mtIoU@0.75 | mvIoU@0.75 | mtIoU@1.00 | mvIoU@1.00 |
|----------------------|-------|-------|-------|------------|------------|------------|------------|------------|------------|
| Gemini 2.5 Flash     | **78.08** | **9.63** | **1.73** | 3.80       | 1.23       | **9.10**   | **1.95**   | 10.47      | **2.33**   |
| Qwen3-VL-8B-Instruct | 68.46 | 7.44  | 1.34  | 1.59       | 0.00       | 5.65       | 0.79       | **11.93**  | 2.01       |

---

##  📊 supplementary material


## 🚀 Data Download
Download the videos and annotation files from our Dataset Page.
Structure your data folder as follows:
data/
├── videos/          # .mp4 clips
├── annotations/     # Multi-dimensional JSON annotations
└── rosters/         # Team rosters and box scores
