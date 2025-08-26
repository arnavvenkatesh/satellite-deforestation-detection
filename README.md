# satellite-deforestation-detection
## Overview  
This project implements a computer vision pipeline for monitoring forest cover using satellite imagery. It processes incoming satellite images, compares them against a reference dataset, and identifies whether a region of land has undergone deforestation. If changes are detected, the system generates an alert to notify the user. The goal is to support environmental monitoring and provide early warnings of forest loss in a scalable, automated way. This project can also run using computer's webcam. Need to show live-feed of Earth perhaps by using Google Earth.
This project detects deforestation by classifying satellite images into two categories: **lush** (forested) and **barren** (deforested). A convolutional neural network is trained on labeled images stored in two folders:  

- `data/lush/` → training images of healthy forest cover  
- `data/barren/` → training images of deforested or degraded land  

Once the model is trained, it can be run on a live camera feed. In testing, Google Earth was used as the source of satellite imagery: the webcam was pointed at the screen, and the model classified each frame in real time. If the feed shows deforested land, the system immediately flags it and produces an alert.  

## Workflow  
1. **Prepare Data:** Organize training images into `lush/` and `barren/` folders.  
2. **Train Model:** Run the notebook to preprocess the dataset and train the classifier. The trained model is saved for reuse.  
3. **Live Detection:** Re-run the notebook’s inference section to open the webcam. Point the camera at a satellite feed (Google Earth or similar). The system will classify frames as *lush* or *barren* and trigger alerts when deforestation is detected.  

## Applications  
- Early detection of deforestation for conservation monitoring  
- Educational demo for environmental science and AI in aerospace/earth observation  
- Prototype payload concept for CubeSat or UAV integration  

