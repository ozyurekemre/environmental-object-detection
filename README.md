# Environmental Object Detection using YOLOv8n  
### A Deep Learning Pipeline for Scalable Environmental Monitoring  
📄 Final Project – Computer Vision & Artificial Intelligence (2025)

---

## 🌍 Project Overview  
This project develops a **YOLOv8n-based object detection system** for environmental monitoring,  
using a real-world dataset of **8,693 annotated images** across six classes  
(car, bus, bicycle, motorbike, person, truck).  
_Source: Dataset description, page 6_ :contentReference[oaicite:1]{index=1}

Although trained on street-level images, the system is explicitly designed as a  
**surrogate for satellite or aerial monitoring**, enabling transfer to tasks such as:

- Wildlife detection  
- Illegal vehicles in conservation zones  
- Emission hotspot tracking  
- Urban mobility & congestion analysis  
- Deforestation and remote activity detection  

The model achieves **92% mAP@0.5** and **0.90 F1-score**,  
outperforming classical models in speed-accuracy balance.

_Source: Evaluation results, page 14–15_ :contentReference[oaicite:2]{index=2}

---

## 🧩 Problem Statement  
Traditional environmental monitoring suffers from:  
- High operational costs  
- Manual, slow data collection  
- Lack of real-time visibility  
- Limited scalability in remote ecosystems  

_Source: Problem Formulation, page 5_ :contentReference[oaicite:3]{index=3}  

Modern CV models like YOLOv8 offer:  
- Real-time inference  
- High accuracy  
- Low-hardware deployment (edge devices, IoT)  
- Scalability across large spatial regions  

---

## 📂 Dataset  
- **8,693 labeled images**  
- **YOLO annotation format**  
- **6 environmental object classes**  
  - car  
  - bus  
  - bicycle  
  - person  
  - motorbike  
  - truck  

Class imbalance:  
- Cars represent **56.96%** of all objects  
- Buses/trucks < 2%  
- 40% of objects are *small-sized*, requiring specialized augmentation  
_Source: Dataset analysis, pages 6–7_ :contentReference[oaicite:4]{index=4}

---

## 🧠 Data Preparation & Augmentation  

To handle imbalance, occlusions, and small objects, an extensive augmentation pipeline was used:  
_Source: Augmentation section, pages 8–10_ :contentReference[oaicite:5]{index=5}  

- RandomBrightnessContrast (±30–40%)  
- Rotation (±20°) → improves thin-object detection (bicycles)  
- Scaling → simulates distance variation  
- Cutout → teaches occlusion resistance  
- Normalization & resizing (640×640)  

This pipeline significantly improved generalizability in real environmental conditions.

---

## ⚙️ Model Architecture – YOLOv8n  
The project uses the **YOLOv8 nano variant**, chosen for:

- Extremely fast inference  
- Strong performance on small objects  
- Lightweight deployment (edge devices, low-power GPUs/CPUs)  
- Modern decoupled head architecture  
- PAN-FPN neck for multi-scale feature extraction  

_Source: Model Implementation, pages 11–12_ :contentReference[oaicite:6]{index=6}  

Training configuration:

- **50 epochs**  
- **640×640 image size**  
- **AdamW optimizer**  
- **Cross-entropy + IoU loss**  
- Early stopping & validation monitoring  

Training time: **48.72 hours** on Intel i7-6700HQ  
_Source: page 13_ :contentReference[oaicite:7]{index=7}  

---

## 📈 Model Performance  

### **Final Evaluation (before tuning)**  
- **mAP@0.5:** 0.92  
- **mAP@0.5:0.95:** 0.77  
- **Precision:** 0.95  
- **Recall:** 0.86  
- **F1-Score:** 0.90  
_Source: page 14_ :contentReference[oaicite:8]{index=8}  

### **After Hyperparameter Tuning**  
- **mAP@0.5: 0.94** (↑ +2%)  
- **Recall: 0.89** (↑ +3% with conf=0.4)  
- **F1-Score: 0.91**  
_Source: page 15_ :contentReference[oaicite:9]{index=9}  

YOLOv8n outperformed Faster R-CNN in total balance of:  
- Speed  
- Inference latency  
- Small-object detection  

---

## 🔍 Example Predictions  
Below is an example of the model detecting cars, bicycles, pedestrians, and motorbikes in urban traffic:

_Image output, page 17_ :contentReference[oaicite:10]{index=10}  

The model successfully detects:

- Motorcycles in shadows  
- Partially occluded objects  
- Dense traffic objects with overlapping bounding boxes  

_Source: page 18_ :contentReference[oaicite:11]{index=11}

---

## 🌱 Practical Applications  
Source: pp. 18–19 :contentReference[oaicite:12]{index=12}

### **Urban Monitoring**  
- Traffic congestion & emissions  
- Speeding and illegal vehicle tracking  
- Bicycle-lane safety monitoring  

### **Environmental & Wildlife Monitoring**  
- Animal detection using transfer learning  
- Illegal vehicle tracking in forest reserves  
- Ecotourism impact measurement  

### **Climate & Sustainability**  
- Emission hotspot mapping  
- Wildfire early alerts (smoke/vehicle detection)  
- Deforestation activity tracking  

### **Deployment Benefits**  
YOLOv8n runs on:  
- Edge devices  
- Solar-powered sensors  
- Low-power embedded boards  

---

## 🛡️ Ethical & Regulatory Compliance  
The system follows EU AI Act guidelines:  
_Source: page 20_ :contentReference[oaicite:13]{index=13}

- **Anonymization**: faces & plates blurred  
- **Data Minimization**: only bounding boxes transmitted  
- **Resolution Thresholds**: no residential monitoring below 50m  

This ensures fully ethical environmental surveillance.

