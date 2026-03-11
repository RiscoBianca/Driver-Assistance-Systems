# 🚗 ADAS: Hybrid Semantic Segmentation & Knowledge-Based System
[cite_start]**Author:** Bianca RIȘCO [cite: 3]
[cite_start]**Course:** Knowledge-Based Systems (Sisteme bazate pe Cunoaștere) [cite: 4]

## 📌 Project Overview
[cite_start]This project presents an advanced **Driver Assistance System (ADAS)** developed as a semester project[cite: 1, 2]. [cite_start]It features a hybrid architecture that combines **Deep Learning** for environment perception and a **Rule-Based System** for safety-critical decision making[cite: 65, 75].

## 🏗️ System Architecture
The system is divided into two main modules:
* [cite_start]**Perception Module:** Utilizes a **U-Net** architecture with a **ResNet34** backbone[cite: 85, 86]. 
* [cite_start]**Methodology:** The model was **trained from scratch** (no pre-trained weights) to specialize filters on specific road geometries and lighting conditions[cite: 87, 212].
* [cite_start]**Knowledge-Based Module:** A symbolic logic system that interprets visual data to issue driving commands[cite: 69, 75].

## 🛠️ Technical Specifications
* [cite_start]**Input Resolution:** 640x640 pixels[cite: 88, 111].
* [cite_start]**Semantic Classes:** 6 categories (Background, Road Sign, Car, Marking, Road Surface, Vegetation)[cite: 77, 113].
* [cite_start]**Pre-processing:** Includes Median Blur for noise reduction and Z-Score Normalization[cite: 171, 193].
* [cite_start]**Data Augmentation:** Implemented via Albumentations (Horizontal Flip, Random Brightness/Contrast) to prevent overfitting[cite: 178, 180].

## 📊 Performance & Evaluation
* [cite_start]**Metrics:** Evaluated using **Intersection over Union (IoU)** and **Dice Loss**[cite: 90, 91].
* [cite_start]**Global IoU:** Achieved approximately **80%**[cite: 273].
* [cite_start]**Dominant Classes:** Road Surface and Background achieved >90% IoU[cite: 275].

### ADAS Decision Logic (Expert System)
[cite_start]The system applies `IF-THEN` rules to real-time segmentation facts[cite: 294]:

| State | Condition | ADAS Action |
| :--- | :--- | :--- |
| **SAFE** | Car density ≤ 5% & Visibility ≥ 15% | [cite_start]**Cruise Control** [cite: 300] |
| **WARNING** | Traffic density 5-15% | [cite_start]**Prepare Brake** [cite: 81] |
| **DANGER** | Car density > 15% | [cite_start]**Emergency Brake** [cite: 296] |
| **CRITICAL** | Road visibility < 15% | [cite_start]**Lane Assist Warning** [cite: 298] |

## 🚀 Future Development
* [cite_start]Scaling the dataset from dozens to thousands of images (night, rain, urban)[cite: 340].
* [cite_start]Implementing model quantization for real-time 30 FPS execution[cite: 343].
* [cite_start]Sensor fusion with Radar or LiDAR data[cite: 344].

## 📚 Bibliography
* [cite_start]Kaggle Roads Segmentation Dataset [cite: 346]
* [cite_start]Knowledge-Based Systems course materials [cite: 346]
