# Cal Poly Pomona ECE4990: YOLOv11 vs. YOLOv12 Comparative Analysis

**Authors:** Jan D. Pastor, Vince Madrigal & Raj Gokidi  
**Course:** ECE 4990.3 – Computer Vision, Spring 2024–25

## Abstract
This project delivers a head-to-head comparative study of the YOLOv11 and YOLOv12 object-detection architectures. We leveraged Ultralytics’ pretrained models on both the VisDrone aerial imagery dataset and the COCO val2017 dataset, retraining and evaluating on Google Colab’s A100 GPUs. Our evaluation metrics include mean average precision (mAP@0.5), inference latency (ms/image), precision-recall curves, confusion matrices, and F1-scores. By systematically capturing these performance curves and resource footprints, we identify the architectural refinements in YOLOv12 and quantify their impact on detection accuracy and real-time suitability, offering guidance for deployment in resource-constrained vision systems.

## 🚀 Quick Start (no installs!)

### Open in Google Colab
[![YOLOv11 in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JanPastor/Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis/blob/main/notebooks/yolov11/YOLOv11.ipynb)
[![YOLOv12 in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JanPastor/Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis/blob/main/notebooks/yolov12/YOLOv12.ipynb)

### Launch via Binder
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/JanPastor/Cal-Poly-Pomona-ECE4990-YOLOv11-vs-YOLOv12-Comparative-Analysis/main?urlpath=lab/tree/notebooks)


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

```
### 2. Pip + venv


```

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
```
### 3. Docker

```


#### Prerequisites
1. Install Docker Desktop (Windows/macOS): https://www.docker.com/products/docker-desktop  
2. (Optional, for GPU) Install NVIDIA Container Toolkit and enable WSL 2 integration.

#### Dockerfile
Create a file named `Dockerfile` at the repo root with these contents:
```dockerfile
FROM python:3.8-slim
WORKDIR /workspace
COPY environment.yml ./
RUN apt-get update -y && apt-get install -y wget bzip2 \
  && wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh \
  && bash /tmp/miniconda.sh -b -p /opt/conda \
  && rm /tmp/miniconda.sh \
  && /opt/conda/bin/conda env create -f environment.yml \
  && ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh \
  && echo "conda activate yolov-comparison" >> ~/.bashrc \
  && apt-get clean && rm -rf /var/lib/apt/lists/*
COPY . .
EXPOSE 8888
CMD ["bash", "-lc", "jupyter notebook --ip=0.0.0.0 --no-browser --allow-root"]

```
### Build the iamge

```
docker build -t yolov-comparison:latest .

```
### Run the container

#### CPU Only:
```
docker run \
  -p 8888:8888 \
  -v "$(pwd)":/workspace \
  yolov-comparison:latest
```

#### NVIDIA GPU
```
docker run --gpus all \
  -p 8888:8888 \
  -v "$(pwd)":/workspace \
  yolov-comparison:latest


```
Tip: After launching Jupyter, open your browser to
http://localhost:8888
and navigate into the notebooks/yolov11/ or notebooks/yolov12/ folders to run your experiments.


