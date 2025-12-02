# AI-Check-coin-image-recognition-using-EDGE-IMPULSE
A project for training EDGE IMPULSE to distinguish Check coin images from non coin images and also determine which coin is on the image. Images will be taken by smart phone camera.

# Coin Recognition with Edge Impulse  
### Digital Electronics (MPA-DIE 25/26Z)

This repository contains the publicly accessible documentation for our group project:  
**an image-based machine learning system for automatic recognition of Czech coins using Edge Impulse.**

The goal of this README is to clearly present the **problem statement**, **solution overview**, **hardware list**, and **software design**, as required by the course assignment.

A full technical report is available inside the `/docs` folder.

---

# 1. Problem Statement and Solution Overview

### **Problem**
Automatically identifying objects—such as coins—typically requires specialized sensors or embedded microcontrollers.  
Our project explores whether **a machine learning model trained purely on camera images** can reliably classify Czech coin denominations, even when photographed under different conditions.

### **Objective**
Build and train an Edge Impulse model that can classify **2 Kč, 5 Kč, 10 Kč, 20 Kč, 50 Kč**, and **Unknown** (non-coins), using only:

- a smartphone camera,
- image preprocessing,
- and a cloud-based ML training pipeline.

### **Why This Matters**
A reliable coin-recognition model can be used for:
- mobile finance apps  
- accessibility tools for visually impaired users  
- teaching automated classification in embedded systems  
- sorting/counting systems  

### **Solution Overview**
Our solution uses:
- **Smartphone images** as the only sensor input  
- **Edge Impulse** for dataset acquisition, preprocessing, augmentation, and training  
- A progression from **MobileNetV2 (default model, 65% accuracy)** to **EfficientNet-Lite B0 (optimized, ~90.5% accuracy)**  

The final model:
- Achieves **90.5% accuracy**  
- Handles variations in lighting, angle, and position  
- Successfully distinguishes visually similar coins (with expected confusion in 10 Kč ↔ 5 Kč ↔ 50 Kč)

This project was approved **without any MCU or external hardware**, focusing solely on machine learning workflows.

---

# 2. Hardware Components

### **Hardware Used**
| Component | Purpose | Justification |
|----------|----------|---------------|
| **Smartphone camera** | Image capture for dataset | Only required sensor; professor approved ML-only project. |

### **Hardware Not Used**
We used **no MCU (microcontroller), sensors, actuators, or embedded platforms**.

**Reason:**  
The professor approved a smartphone-only Edge-Impulse project, since our focus was on the ML pipeline, dataset design, and model optimization rather than embedded deployment.

---

# 3. Software Design

The software system consists of three main stages:

1. **Data Capture & Preprocessing**  
2. **Model Training & Optimization**  
3. **Evaluation & Deployment**

## 3.1 System-Level Block Diagram

Smartphone Camera
        ↓
Dataset Upload (Edge Impulse)
        ↓
Data Labeling & Cleaning
        ↓
Data Augmentation (flip, crop, brightness)
