# BasketGround: A Multi-dimensional Vision-Language Dataset for Basketball Video Analysis

[![Paper](https://img.shields.io/badge/Paper-Arxiv-red)](https://github.com/nightPoemy/BasketGround)
[![Dataset](https://img.shields.io/badge/Dataset-Download-blue)](https://github.com/nightPoemy/BasketGround)
[![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-green)](LICENSE)

**BasketGround** 是一个专门为篮球视频理解设计的语义增强型多维视觉语言数据集。它在 [MultiSports](https://github.com/MCG-NJU/MultiSports) 数据集的基础上，通过引入球员身份（Identity）、团队属性（Team）、精细化动作语义（Action）、球场空间位置（Location）以及自然语言标题（Caption），构建了一个全方位的篮球视频分析基准。

---

## 🏀 数据集概览

![Overview](https://github.com/nightPoemy/BasketGround/raw/main/assets/overview.png)  
*图 1: BasketGround 数据集标注示例。每个球员实例都关联了身份、球衣颜色/号码、动作类型、场上位置以及一段描述性文本。*

### 核心亮点
- **多维统一标注**: 首次在一个数据集中统一了 "Who (谁)", "What (做什么)", "Where (在哪)" 和 "How (如何描述)"。
- **高质量标注**: 包含 43 个完整全场比赛视频，468 个视频片段，共计 **5,355** 个精细标注的球员实例。
- **空间语义增强**: 引入了诸如 "Left Side of the Key"、"Paint" 等篮球专业空间术语。
- **富有挑战性的基准**: 实验显示，即使是 GPT-4o 和 Gemini 2.5 等大模型，在球员身份识别（<20% 准确率）和复杂动作定位方面仍有巨大的进步空间。

---

## 📊 数据统计 (Dataset Statistics)

| 统计维度 | 数量 / 类别 |
| :--- | :--- |
| **视频总数 (Full Games)** | 43 |
| **视频切片 (Clips)** | 468 |
| **球员实例 (Annotated Instances)** | 5,355 |
| **主要动作类别** | Dribble, Pass, Shot, Screening, Defensive Rebound, etc. |
| **标注维度** | ID, Team, Jersey No., Color, Action, Location, Caption |

---

## 🛠 任务定义 (Benchmark Tasks)

### Task 1: 精细化多维语义理解
要求模型在给定球员裁剪视频（Cropped Tube）和边界框的情况下，联合预测该球员的：
- **Identity**: 球员姓名。
- **Action**: 精细动作标签。
- **Location**: 场上语义位置。

### Task 2: 基于视觉证据的时空视频定位 (STVG)
给定原始视频和一个包含缺失属性的查询（如：“穿红色球衣的球员正在上篮”），模型需要：
1. **视觉证据恢复**: 推断出球员的具体姓名、球队等。
2. **时空定位**: 在视频中回归出该球员完整的时空 Bounding Box 序列。

---

## 🚀 快速开始 (Quick Start)

### 1. 数据下载
请访问 [Dataset Page](https://github.com/nightPoemy/BasketGround) 下载：
- `videos/`: 468 个 .mp4 视频片段。
- `annotations/`: 包含所有多维标注的 JSON 文件。
- `rosters/`: 对应比赛的球员名单参考。

### 2. 数据格式示例
```json
{
  "clip_id": "AUS_vs_PHI_01",
  "instance_id": "player_13_Ezi",
  "metadata": {
    "name": "Ezi Magbegor",
    "team": "Australia",
    "jersey": "13 (Yellow)",
    "action": "Block",
    "location": "Under the basket"
  },
  "caption": "Ezi Magbegor, wearing the yellow #13 jersey for Australia, blocks an opponent's shot attempt directly under the basket.",
  "tube": [
    {"frame": 449, "bbox": [431, 288, 508, 453]},
    {"frame": 450, "bbox": [433, 290, 510, 455]}
  ]
}
