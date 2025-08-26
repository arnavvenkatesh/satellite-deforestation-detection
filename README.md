# satellite-deforestation-detection
## Overview
This project implements a computer vision pipeline for monitoring forest cover using satellite imagery. It processes incoming satellite images, compares them against a reference dataset, and identifies whether a region of land has undergone deforestation. If changes are detected, the system generates an alert to notify the user. The goal is to support environmental monitoring and provide early warnings of forest loss in a scalable, automated way. This project can also run using computer's webcam. Need to show live-feed of Earth perhaps by using Google Earth.

## Features
- Preprocessing pipeline for raw satellite images  
- Classification model to distinguish forested vs. deforested regions  
- Automated alert system when deforestation is detected  
- Modular design for integration with live satellite feeds or CubeSat payloads  

## Repository Structure
- `notebooks/` → Jupyter notebooks with the main code  
- `data/` → sample dataset or links to full datasets  
- `results/` → output images or detection results  
- `docs/` → related reports, presentations, and references  

## Requirements
To install dependencies, run:
```bash
pip install -r requirements.txt

