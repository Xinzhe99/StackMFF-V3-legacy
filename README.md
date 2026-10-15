> [!WARNING]
> **Deprecated / 已废弃 (2026-10).** This repository is no longer maintained. Its method has been merged with StackMFF V4 and redesigned into a new, unified **StackMFF V3** (all-attention, pixel-wise layer classification). The new code, weights and benchmark results will be released in a new repository, which will be linked here. Please use the new release; this code is kept for reference only.
>
> 本仓库已停止维护。其方法已与 StackMFF V4 合并并重新设计为新的统一版 **StackMFF V3**，新代码、权重与评测结果将在新仓库发布（届时在此处给出链接），请以新版本为准。本仓库仅作存档参考。
>
> The old StackMFF V3 repository has been renamed to [StackMFF-V3-legacy](https://github.com/Xinzhe99/StackMFF-V3-legacy). The name **StackMFF-V3** now belongs to the new, unified release, which will become public together with the paper.
>
> 旧版 StackMFF V3 仓库已更名为 StackMFF-V3-legacy；StackMFF-V3 这一名称现由新的统一版使用，将随论文一同公开。

<div align="center">

# <img src="assets/stackmffv3_logo.svg" alt="StackMFF V3" height="320" style="vertical-align: middle;"/> StackMFF V3

**General Multi-focus Image Fusion Network**

[![SSRN](https://img.shields.io/badge/SSRN-5954614-orange.svg)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5954614)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.8+-red.svg)](https://pytorch.org/)
[![GitHub](https://img.shields.io/badge/GitHub-StackMFF--V3-black.svg)](https://github.com/Xinzhe99/StackMFF-V3-legacy)

*Official PyTorch implementation for General Multi-focus Image Fusion Network*

</div>

## 📢 News

> [!NOTE]
> 🎉 **2026.01**: This work has been included in [StackMFF-Series](https://github.com/Xinzhe99/StackMFF-Series)

> 🎉 **2026.01**: StackMFF V4 has been submitted and is under review! [Project Link](https://github.com/Xinzhe99/StackMFF-V4)

> 🎉 **2025.11**: The paper for StackMFF V3 has been submitted.

## Table of Contents

- [Overview](#-overview)
- [Highlights](#-highlights)
- [Installation](#-installation)
- [Downloads](#-downloads)
- [Usage](#-usage)
- [Citation](#-citation)

## 📖 Overview

<div align="center">
<img src="assets/stackmffv3_framework.jpg" width="800px"/>
</div>

## ✨ Highlights

- Presents the first general multi-focus image fusion network.
- Reformulates stack fusion as a pixel-wise multi-class classification task.
- Employs an MLP-based backbone for intra-layer focus estimation with global context.
- Proposes a Pixel-wise Cross-layer Attention module for inter-layer modeling.
- Provides an open-source solution that outperforms commercial software at low cost.

 
## 🚀 Installation

1. Clone the repository:
```bash
git clone https://github.com/Xinzhe99/StackMFF-V3-legacy.git
cd StackMFF-V3
```

2. Create and activate a virtual environment (recommended):
```bash
conda create -n stackmffv3 python=3.8
conda activate stackmffv3
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## 📥 Downloads

| Resource | Link | Code | Description |
|----------|------|------|-------------|
| 🗂️ **Test Datasets** | [![Download](https://img.shields.io/badge/Download-4CAF50?style=flat-square)](https://pan.baidu.com/s/1XrKGlqSK6kc_R-1AzprHlA?pwd=cite) | `cite` | Complete test datasets |
| 📊 **Benchmark Results** | [![Download](https://img.shields.io/badge/Download-FF9800?style=flat-square)](https://pan.baidu.com/s/1_rBtM9o7RUQP4oyt8HHXwg?pwd=cite) | `cite` | Fusion results from all methods |


## 💻 Usage

The pre-trained model weights files (`stackmffv3.pth` and `stackmffv3_star.pth`) should be placed in the [weights](https://github.com/Xinzhe99/StackMFF-V3-legacy/tree/main/weights) directory.

### Example for fusing an image stack

To fuse a stack of multi-focus images, organize your input images in a folder with numeric filenames (e.g., `0.png`, `1.png`, etc.):

```
input_stack/
├── 0.png
├── 1.png
├── 2.png
└── 3.png
```

Run the StackMFF V3 prediction script:

```bash
python predict_one_stack.py --input_dir ./input_stack --output_dir ./results
```

Run the StackMFF V3-star prediction script:

```bash
python predict_one_stack_star.py --input_dir ./input_stack --output_dir ./results_star
```
### Example of batch processing test datasets

To perform batch processing on multiple test datasets, organize your data in the following directory structure:

```
test_datasets/
├── Mobile Depth/
│   └── image stack/
│       ├── scene1/
│       │   ├── 0.png
│       │   ├── 1.png
│       │   └── 2.png
│       └── scene2/
│           ├── 0.png
│           ├── 1.png
│           └── 2.png
├── FlyingThings3D/
│   └── image stack/
└── Middlebury/
    └── image stack/
```

Run the StackMFF V3 prediction script:

```bash
python predict_datasets.py --test_root ./test_datasets --output_dir ./bench_results
```

Run the StackMFF V3-star prediction script:

```bash
python predict_datasets_star.py --test_root ./test_datasets --output_dir ./bench_results_star
```
### Example of fusing image pairs from datasets

To fuse image pairs from multiple datasets, organize your data in the following directory structure:

```
image_pair_datasets/
├── Lytro/
│   ├── A/
│   │   ├── 1.png
│   │   ├── 2.png
│   │   └── 3.png
│   └── B/
│       ├── 1.png
│       ├── 2.png
│       └── 3.png
├── MFFW/
│   ├── A/
│   └── B/
└── MFI-WHU/
    ├── A/
    └── B/
```

Run the StackMFF V3 image pair prediction script:

```bash
python predict_pair_datasets.py --test_root ./image_pair_datasets --output_dir ./pair_results
```

Run the StackMFF V3-star image pair prediction script:

```bash
python predict_pair_datasets_star.py --test_root ./image_pair_datasets --output_dir ./pair_results_star
```

##  Training

### Dataset Structure

#### For StackMFF V3:

```
datasets_root/
├── DatasetName1/
│   ├── TR/ (Training set)
│   │   ├── focus_stack/ (image stacks)
│   │   │   ├── scene1/
│   │   │   │   ├── 0.png
│   │   │   │   ├── 1.png
│   │   │   │   └── 2.png
│   │   │   └── scene2/
│   │   │       ├── 0.png
│   │   │       ├── 1.png
│   │   │       └── 2.png
│   │   └── focus_index_gt/ (Focus index ground truth)
│   │       ├── scene1.npy
│   │       └── scene2.npy
│   └── TE/ (Test/Validation set)
│       ├── focus_stack/
│       └── focus_index_gt/
├── DatasetName2/
│   ├── TR/
│   └── TE/
└── ...
```

#### For StackMFF V3-Star:

```
datasets_root/
├── DatasetName1/
│   ├── TR/ (Training set)
│   │   ├── focus_stack/ (image stacks)
│   │   │   ├── scene1/
│   │   │   │   ├── 0.png
│   │   │   │   ├── 1.png
│   │   │   │   └── 2.png
│   │   │   └── scene2/
│   │   │       ├── 0.png
│   │   │       ├── 1.png
│   │   │       └── 2.png
│   │   └── depth/ (Depth maps)
│   │       ├── scene1.png
│   │       └── scene2.png
│   └── TE/ (Test/Validation set)
│       ├── focus_stack/
│       └── depth/
├── DatasetName2/
│   ├── TR/
│   └── TE/
└── ...
```

### Training StackMFF V3

To train the StackMFF V3 model, run the following command:

```bash
python train.py \
  --save_name train_stackmffv3 \
  --datasets_root /data/stackmff_datasets \
  --train_datasets NYU-V2 DUTS DIODE Cityscapes ADE \
  --val_datasets NYU-V2 DUTS DIODE Cityscapes ADE \
  --batch_size 8 \
  --num_epochs 50 \
  --lr 1e-3 \
  --gpu_ids 0
```

### Training StackMFF V3-Star

To train the StackMFF V3-Star model, run the following command:

```bash
python train_star.py \
  --save_name train_stackmffv3_star \
  --datasets_root /data/stackmff_datasets \
  --train_datasets NYU-V2 DUTS DIODE Cityscapes ADE \
  --val_datasets NYU-V2 DUTS DIODE Cityscapes ADE \
  --batch_size 8 \
  --num_epochs 50 \
  --lr 1e-3 \
  --gpu_ids 0
```

## 📚 Citation

TBD.

## 🙏 Acknowledgments

TBD.

<div align="center">

⭐ If you find this project helpful, please give it a star and cite our paper!

</div>









