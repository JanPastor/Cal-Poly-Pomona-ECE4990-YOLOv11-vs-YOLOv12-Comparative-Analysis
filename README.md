# Cal Poly Pomona ECE4990: YOLOv11 vs. YOLOv12 Comparative Analysis

**Authors:** Jan D. Pastor, Vince Madrigal & Raj Gokidi  
**Course:** ECE 4990.3 – Computer Vision, Spring 2024–25

## Abstract
This project delivers a head-to-head comparative study of the YOLOv11 and YOLOv12 object-detection architectures. We leveraged Ultralytics’ pretrained models on both the VisDrone aerial imagery dataset and the COCO val2017 dataset, retraining and evaluating on Google Colab’s A100 GPUs. Our evaluation metrics include mean average precision (mAP@0.5), inference latency (ms/image), precision-recall curves, confusion matrices, and F1-scores. By systematically capturing these performance curves and resource footprints, we identify the architectural refinements in YOLOv12 and quantify their impact on detection accuracy and real-time suitability, offering guidance for deployment in resource-constrained vision systems.

## Installation

You have three main options to install and run this project environment. Pick one that fits your workflow:

### 1. Conda (recommended)

```bash
# 1. Clone the repo
git clone https://github.com/your-username/Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis.git
cd Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis

# 2. Create the environment (from environment.yml)
conda env create -f environment.yml

# 3. Activate it
conda activate yolov-comparison

# 4. Launch Jupyter
jupyter notebook

# 1. Clone the repo
git clone https://github.com/your-username/Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis.git
cd Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis

# 2. Create & activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate     # on PowerShell: .venv\Scripts\Activate.ps1

# 3. Install dependencies
pip install --upgrade pip
pip install -r requirements.txt   # generate via `pip freeze > requirements.txt` if not present

# 4. Launch Jupyter
jupyter notebook

# 1. Build the Docker image
docker build -t yolov-comparison:latest .

# 2. Run a container with Jupyter exposed on port 8888
docker run --gpus all -p 8888:8888 \
  -v $(pwd):/workspace/yolo-compare \
  yolov-comparison:latest \
  jupyter notebook --ip=0.0.0.0 --no-browser --allow-root
