# Smart Dustbin – Object Detection System (YOLOv8)

## Overview
This project implements a smart waste segregation system using computer vision and embedded hardware.  
A Raspberry Pi 4 Model B with a Pi Camera is used to detect waste materials and automatically open the corresponding waste bin.

The system is designed with a feedback loop where detected images are stored on the cloud to continuously improve the dataset and detection accuracy.

## System Architecture
- Raspberry Pi 4 Model B
- Pi Camera for image capture
- YOLOv8n (Nano) for real-time object detection
- Servo-controlled waste bins

## Waste Categories
The YOLO model is trained on **six waste categories**:

1. paper_cardboard  
2. glass  
3. metal  
4. biodegradable  
5. plastic  
6. e_waste  

### Error Handling (Other Category)
A seventh category, **Other**, is implemented at the Raspberry Pi logic level (not used for YOLO training).

- If the system fails to classify an object after **three detection attempts**
- The **Other** bin is opened
- This handles unknown waste types or unusual object shapes

## Dataset & Annotation
- Images are captured during real-world usage
- Both annotated and non-annotated images are stored on the cloud
- Annotations are created using:
  - CVAT
  - Roboflow
- Labels are exported in **YOLOv8-compatible format**


## Dataset Structure
```
dataset/
├── images/
│ ├── train/
│ └── val/
└── labels/
  ├── train/
  └── val/
```
## Continuous Improvement Pipeline
- Misclassified and unknown waste images are collected
- Dataset is expanded over time
- Model retraining improves detection accuracy
- Enables handling of new waste categories in future

## Applications
- Smart waste segregation systems
- Embedded AI using Raspberry Pi
- Real-time object detection on edge devices

## Future Work
- Model retraining with expanded dataset
- Performance optimization on Raspberry Pi
- Cloud dashboard for monitoring detections
