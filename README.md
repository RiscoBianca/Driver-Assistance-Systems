# 🚗 ADAS: Hybrid Semantic Segmentation & Knowledge-Based System

**Author:** Bianca RIȘCO  
**Course:** Sisteme bazate pe Cunoaștere (SBC)

## 📌 Project Overview
This project develops an advanced **Driver Assistance System (ADAS)** that integrates **Deep Learning** for environment perception and a **Rule-Based System** for safety-critical decision-making. The system interprets road scenes at a pixel level to generate alerts such as "Emergency Brake" or "Lane Assist Warning".

## 🏗️ System Architecture
[cite_start]The system is built on a modular hybrid architecture[cite: 75]:
* [cite_start]**Perception Module:** A **U-Net** architecture using a **ResNet34** backbone[cite: 85, 86].
* [cite_start]**Methodology:** The model was **trained from scratch** (no pre-trained weights) to ensure specialization on road-specific features like asphalt texture and lane markings[cite: 87, 212].
* [cite_start]**Knowledge-Based Module:** A symbolic logic engine that applies deterministic rules to the segmentation masks to issue driving commands[cite: 69, 75].

## 🛠️ Technical Specifications
* [cite_start]**Resolution:** Input images are standardized to **640x640 pixels**[cite: 88].
* [cite_start]**Semantic Classes:** 6 categories: Background, Road Signs, Cars, Markings, Road Surface, and Vegetation[cite: 77].
* [cite_start]**Normalization:** Uses custom **Z-Score Normalization** calculated directly from the project's dataset ($\mu$ and $\sigma$ specific to these road scenes)[cite: 230, 231, 232].
* [cite_start]**Optimization:** Trained using **Dice Loss** and evaluated via **Intersection over Union (IoU)** to manage class imbalance[cite: 90, 91].



## 📊 ADAS Decision Logic (Expert System)
[cite_start]The system analyzes traffic density and lane visibility to determine the safety state[cite: 78, 79]:

| State | Condition | ADAS Recommendation |
| :--- | :--- | :--- |
| **SAFE** | Car density ≤ 5% & Visibility ≥ 15% | [cite_start]**CRUISE CONTROL** [cite: 300] |
| **WARNING** | Car density between 5-15% | [cite_start]**PREPARE BRAKE** [cite: 81] |
| **DANGER** | Car density > 15% | [cite_start]**EMERGENCY BRAKE** [cite: 296] |
| **CRITICAL** | Road visibility < 15% | [cite_start]**LANE ASSIST WARNING** [cite: 298] |

## 🚀 Key Results
* [cite_start]**High Accuracy:** Achieved an **IoU of ~80%** globally, with >90% on critical classes like the road surface[cite: 273, 275].
* [cite_start]**Generalization:** Successfully tested on **urban environments** (out-of-distribution) demonstrating that the model learned transferable semantic features rather than just memorizing images[cite: 313, 316].

## 📚 Future Work
* [cite_start]**Scaling:** Expanding the dataset to include night, rain, and fog scenarios[cite: 340].
* [cite_start]**Quantization:** Optimizing the model for real-time 30 FPS execution on embedded hardware[cite: 343].
* [cite_start]**Sensor Fusion:** Integrating Radar/LiDAR data for increased reliability[cite: 344].
