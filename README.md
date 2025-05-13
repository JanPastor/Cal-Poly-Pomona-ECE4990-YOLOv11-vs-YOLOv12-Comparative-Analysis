# Cal Poly Pomona ECE4990: YOLOv11 vs. YOLOv12 Comparative Analysis

**Authors:** Jan D. Pastor, Vince Madrigal & Raj Gokidi  
**Course:** ECE 4990.3 – Computer Vision, Spring 2024–25

## Abstract
This project delivers a head-to-head comparative study of the YOLOv11 and YOLOv12 object-detection architectures. We leveraged Ultralytics’ pretrained models on both the VisDrone aerial imagery dataset and the COCO val2017 dataset, retraining and evaluating on Google Colab’s A100 GPUs. Our evaluation metrics include mean average precision (mAP@0.5), inference latency (ms/image), precision-recall curves, confusion matrices, and F1-scores. By systematically capturing these performance curves and resource footprints, we identify the architectural refinements in YOLOv12 and quantify their impact on detection accuracy and real-time suitability, offering guidance for deployment in resource-constrained vision systems.

## Installation

```bash
git clone https://github.com/your-username/Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis.git
cd Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis
conda env create -f environment.yml    # or pip install -r requirements.txt
conda activate yolov-comparison
