# ⚽ Soccer Players Tracking

=====================================================

🚀 An end-to-end **computer vision pipeline** for **soccer player detection, multi-object tracking and ROI-based behavior analysis** from broadcast videos.

Developed for the **Artificial Vision (MSc in Computer Engineering)** course at the **University of Salerno**, and evaluated on the **SoccerNet 2023 Tracking dataset** using **HOTA₀.₅** and **normalized MAE (nMAE)** metrics.

> Demonstrates practical experience in deep learning, multi-object tracking, re-identification, camera motion compensation and performance-driven experimental design.

* * *

📸 System Overview Snapshot
---------------------------


https://github.com/user-attachments/assets/5996374a-c95f-4319-a4a7-bcc40bbd1adb

---

## 📌 Overview

This project implements a complete pipeline that performs:

* ⚽ **Player, referee and linesman detection**
* 🔁 **Multi-object tracking with ID consistency**
* 🧠 **Behavior analysis** (number of players inside predefined ROIs)
* 📊 Evaluation using **HOTA₀.₅** (tracking) and **nMAE** (behavior)
* 🏆 Final ranking metric: **PTBS = HOTA₀.₅ + nMAE**

The system was tested on the official **SoccerNet Tracking 2023 dataset** and evaluated using the simulation tool provided by the course instructors.

Full technical details are available in:  
📄 `1 - Documentazione_Artificial_Vision_Cirillo_Fasolino.pdf`

* * *

🌍 Language Note
----------------

All **code comments and internal documentation** are written in **Italian**, as the project was developed during a group exam at the **University of Salerno (Italy)**.

Despite this, the **codebase follows international best practices**, with clear method names and class structures that make it easily understandable for global developers and recruiters.

* * *

## 🧠 System Architecture

The final pipeline consists of:

1. **YOLO12m (fine-tuned on SoccerNet)** for detection
2. **Soccer pitch mask filtering** (color-based with safety threshold)
3. **Bot SORT tracker (tuned)**
    * Camera Motion Compensation (sparse optical flow)
    * Re-identification using Omni-Scale Network (MSMT17 pretrained)
4. **ROI-based behavior analysis**
5. Output generation in official contest format

### 🔄 Processing Pipeline

CodeVideo → YOLO Detection → Pitch Mask Filtering → Bot SORT Tracking  
      → Tracking Output (.txt)  
      → ROI Counting → Behavior Output (.txt)

The final inference pipeline consumes **< 500MB RAM**, making it deployable on mid-range devices.

---

## 🔬 Technologies Used

### 🧠 Detection

* **YOLOv8 / YOLO11 / YOLO12 (Ultralytics)**
* Final model: **YOLO12m fine-tuned on SoccerNet**
* Resolution: 1024
* Optimizer: AdamW

### 🔁 Tracking

* **ByteTrack** (baseline + tuning)
* **Bot SORT** (final choice)
* ReID: **Omni-Scale Network x0_25**
* Camera Motion Compensation

### 🖼 Vision & Utilities

* OpenCV
* Ultralytics
* boxmot
* Optical Flow
* Morphological operators

---

## 📊 Metrics

### 🎯 Tracking Metric

* **HOTA₀.₅ = 0.762231**

### 🧠 Behavior Metric

* **MAE = 0.184925**
* **Normalized MAE (nMAE) = 0.981507**

### 🏆 Final Score

PTBS = HOTA₀.₅ + nMAE = 1.743739

The system was evaluated using the official simulator provided by the course (not present in this repository).

---

## 📂 Repository Structure

```
Code📦 soccer-players-tracking  
├── 📁 docs  
│   ├── 0 - Contest presentation.pdf  
│   ├── 1 - Documentazione_Artificial_Vision_Cirillo_Fasolino.pdf  
│   └── 2 - output_simulator.txt  
│  
├── 📁 scripts  
│   ├── 0 - dataset_download.py  
│   ├── 1 - create_behavior_gt.ipynb  
│   ├── 2 - dataset_conversion.ipynb  
│   ├── 3 - yolo_training.ipynb  
│   ├── 4 - yolo_validation.ipynb  
│   └── 5 - tracking_pipeline_inference_script.ipynb  
│  
├── 📁 weights  
│   └── best_yolo12m_v2.pt  
│  
├── LICENSE  
└── README.md
```

---

## 🧪 Development Workflow

### 1️⃣ Dataset Preparation

* Conversion from SoccerNet format → YOLO format
* Removal of ball annotations
* ROI generation
* Behavior ground truth generation

Scripts:

* `dataset_conversion.ipynb`
* `create_behaviour_gt.ipynb`

---

### 2️⃣ Training & Validation

* Fine-tuning of YOLO12m
* Validation split created from training set
* Hyperparameter exploration (freeze vs full fine-tuning)

Notebook:

* `yolo_training.ipynb`
* `yolo_validation.ipynb`

---

### 3️⃣ Tracking Optimization

* ByteTrack tuning
* Switch to Bot SORT
* ReID integration
* Camera Motion Compensation
* ID switch reduction analysis

---

### 4️⃣ Final Inference

Full pipeline available in:

Codetracking_pipeline_inference_script.ipynb

Outputs:

* `tracking_K_XX.txt`
* `behavior_K_XX.txt`
* Annotated output videos

---

## 🎓 Academic Context

Developed as a **Project Work** for:

**Artificial Vision – MSc in Computer Engineering**  
University of Salerno  
Academic Year 2025/2026

All internal documentation is written in **Italian**, as required by the course.

---

## 💡 Key Challenges Addressed

* Over-tracking and ID fragmentation
* Camera panning & zoom effects
* False detections outside the pitch
* Appearance similarity among players
* ROI-based counting robustness

---

## 🔮 Future Improvements

* Semantic segmentation-based pitch mask
* Jersey number recognition for long-term re-identification
* Player Attribute Recognition (PAR)
* Further tracker optimization
* More robust handling of adverse weather conditions (e.g., snow)

---

## ⭐ Final Note

This project highlights:

* Applied deep learning
* Multi-object tracking optimization
* Experimental methodology
* Metric-driven development
* End-to-end system design

If you find it interesting, feel free to ⭐ the repository.

* * *

📬 Contacts
-----------

✉️ Got feedback or want to contribute? Feel free to open an Issue or submit a Pull Request!

* * *

📈 SEO Tags
-----------

```
Soccer Player Tracking, SoccerNet Tracking 2023, Multi-Object Tracking, MOT Computer Vision, YOLO12 Fine-Tuning, YOLO Soccer Detection, Bot SORT Tracker, ByteTrack Tracking, Player Re-Identification, ReID Computer Vision, Camera Motion Compensation, Optical Flow Tracking, Sports Video Analytics, Soccer Video Understanding, ROI Behavior Analysis, HOTA Metric, HOTA 0.5 Evaluation, Detection and Association Accuracy, Normalized MAE, PTBS Score, Deep Learning for Sports, Broadcast Video Analysis, Real-Time Object Tracking, Ultralytics YOLO, Computer Vision MSc Project, Artificial Vision Project, Python Computer Vision, Soccer Analytics AI, End-to-End Vision Pipeline, University of Salerno Project
```

* * *

📄 License
----------

This project is licensed under the **MIT License**, a permissive open-source license that allows anyone to use, modify, and distribute the software freely, as long as credit is given and the original license is included.

> In plain terms: **use it, build on it, just don’t blame us if something breaks**.

> ⭐ Like what you see? Consider giving the project a star!

* * *


