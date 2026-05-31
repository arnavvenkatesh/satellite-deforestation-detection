# satellite-deforestation-detection

An end-to-end computer vision pipeline that leverages deep learning to detect localized deforestation, agricultural encroachment, and land degradation from satellite imagery in real time. 

By utilizing transfer learning on an optimized convolutional neural network spine, this system is designed to process live orbital feeds to instantly differentiate between untouched, intact forest canopy and human-altered or barren terrains.

## 🛰️ Orbital Hardware Integration: CubeSat Prototype
This repository serves as the software and inference backbone for a larger aerospace initiative. The computer vision model built here is designed to directly ingest live optical feeds transmitted from my custom-built CubeSat. 

To view the hardware architecture, telemetry systems, and physical build of the satellite providing the live feed, please visit the companion repository: **[CubeSat Prototype](https://github.com/arnavvenkatesh/cubesat-prototype)**.

---

## 🚀 Engineering Highlights
* **Real-Time Inference Loop:** Built an efficient screen-scraping architecture using OpenCV and `mss` to perform live, on-the-fly predictions on active mapping software and live video telemetry at minimal compute cost.
* **Transfer Learning Backbone:** Implemented a pre-trained `MobileNetV2` architecture, fine-tuning top-layer weights to capture complex landscape textures and multi-spectral structural profiles rather than simple color maps.
* **Curation & Data Hygiene:** Hand-managed a balanced multi-source pipeline to eliminate systemic data bias, training natively on an optimized 1:1 distribution.

---

## 📊 Dataset & Architecture

The production model is trained on a robust, naturally balanced dataset containing **5,469 high-fidelity remote sensing images**:

* 🌲 **Intact Nature / Lush Canopy:** 2,610 images (Class 1)
* 🏜️ **Cleared / Barren / Altered Land:** 2,859 images (Class 0)

### 🗃️ Data Provenance & Processing
To maximize model generalization across different geographical terrains, the dataset was constructed as a hybrid blend:
1. **[EuroSAT Dataset on Kaggle:](https://www.kaggle.com/datasets/apollo2506/eurosat-dataset)** Utilized benchmark satellite data for structural baseline profiles of dense forest and vegetation vs. infrastructure.
2. **[Satellite Image Classification on Kaggle:](https://www.kaggle.com/datasets/mahmoudreda55/satellite-image-classification)** Integrated diverse arid and agricultural land textures to prevent over-fitting to single-continent profiles.
3. **Google Earth Engine (Manual Sampling):** Explicitly hand-sampled real-world coordinates highlighting localized logging roads, seasonal crop grids, and recent Amazonian deforestation sectors.

---

## 🛠️ Tech Stack & Dependencies

* **Core Framework:** Python 3.11
* **Deep Learning:** TensorFlow 2.x, Keras
* **Computer Vision & Capture:** OpenCV (`cv2`), `mss`
* **Data Processing:** NumPy, Scikit-learn

---

## 📦 Directory Structure

*(Note: Raw image assets are omitted from remote version control via `.gitignore` to maintain structural agility, but local compilation mirrors this format)*:

<pre>
├── Satellite image detection.ipynb  # Primary production notebook (5-cell execution)
├── mobilenet_satellite.keras        # Compiled, production-ready model weights
├── .gitignore                       # System asset and backup filtering
├── Barren/                          # Local directory: 2,859 images (Label 0)
└── Lush/                            # Local directory: 2,610 images (Label 1)
</pre>

---

## 🖥️ Usage & Execution

The workflow is consolidated into `Satellite image detection.ipynb` for modular testing and deployment:

### 1. Model Training & Compilation
Run **Cells 1 through 4** to initialize the data augmentation generators, load the `MobileNetV2` spine, and initiate training. The pipeline outputs the optimized weights file as `mobilenet_satellite.keras`.

### 2. Live Scanner Deployment
To run live monitoring without restarting training cycles:
1. Ensure `mobilenet_satellite.keras` is in the root directory.
2. Execute **Cell 1** (Imports) and **Cell 5** (Live Screen Capture Loop).
3. Align your target mapping software viewport within the frame (or route your live CubeSat feed to the designated display window). Press `q` over the OpenCV rendering window to safely terminate the stream.

---

## ⚠️ Limitations & Future Scope

While the current architecture successfully classifies terrain in real-time, deployment relies on navigating several environmental and hardware constraints:
* **Atmospheric Occlusion:** As a purely optical computer vision model, inference is currently limited by cloud cover, atmospheric scattering, and extreme weather systems. Future iterations will explore integrating SAR (Synthetic Aperture Radar) data to bypass visual blockages.
* **Telemetry Latency:** Streaming a live optical feed from the CubeSat prototype to the ground-station inference loop introduces inherent transmission latency, requiring strict frame-buffer optimization to prevent desync.
* **Daylight Dependency:** The model requires adequate illumination, limiting viable data collection to sunlit orbital passes.
