# Driver Assistance Systems

**Author:** Bianca Rișco  
**Course:** Sisteme bazate pe Cunoaștere (SBC)

## Project Summary
This project develops an advanced **Driver Assistance System (ADAS)** that integrates **Deep Learning** for environment perception and a **Rule-Based System** for safety-critical decision-making. The system interprets road scenes at a pixel level to generate alerts such as "Emergency Brake" or "Lane Assist Warning".

## System Architecture
The system is built on a modular hybrid architecture:

* **Perception Module:** A **U-Net** architecture using a **ResNet34** Encoder.
* **Methodology:** The model was **trained from scratch** (no pre-trained weights) to ensure specialization on road-specific features like asphalt texture and lane markings.
* **Knowledge-Based Module:** A symbolic logic engine that applies deterministic rules to the segmentation masks to issue driving commands.

## Technical Details
* **Resolution:** Input images are standardized to **640x640 pixels**.
* **Semantic Classes:** 6 categories: Background, Road Signs, Cars, Markings, Road Surface, and Vegetation.
* **Normalization:** Uses custom **Z-Score Normalization** calculated directly from the project's dataset.
* **Optimization:** Trained using **Dice Loss** and evaluated via **Intersection over Union (IoU)**.

## Action & Decision Matrix
The system analyzes traffic density and lane visibility to determine the safety state:

| State | Condition | ADAS Recommendation |
| :--- | :--- | :--- |
| **SAFE** | Car density ≤ 5% & Visibility ≥ 15% | **CRUISE CONTROL** |
| **WARNING** | Car density between 5-15% | **PREPARE BRAKE** |
| **DANGER** | Car density > 15% | **EMERGENCY BRAKE** |
| **CRITICAL** | Road visibility < 15% | **LANE ASSIST WARNING** |

## Performance Metrics
* **High Accuracy:** Achieved an **IoU of ~80%** globally, with >90% on critical classes like the road surface.
* **Generalization:** Successfully tested on **urban environments**, demonstrating that the model learned transferable semantic features.

## 🚀 Roadmap & Next Steps
* **Massive Dataset Expansion:** Significantly increasing the volume of training data to improve the model's generalization capabilities and its ability to detect fine details like road signs.
* **Environmental Robustness:** Broadening the training distribution to encompass adverse environmental conditions, such as low-light (night) and poor visibility (rain, fog).
* **Sensor Fusion:** Integrating Radar/LiDAR data into the Expert System for increased reliability in scenarios where visual data is insufficient.
