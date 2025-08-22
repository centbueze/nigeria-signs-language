# Nigerian Sign Language (NSL) Recognition with YOLOv8 and ESP32-CAM

This project recognizes **Nigerian Sign Language (NSL)** hand gestures using an **ESP32-CAM** for data collection and a **YOLOv8** model for training/inference.  
A **Flask web app** serves real-time predictions from the trained model.

🔗 **Main Repository:** https://github.com/centbueze/nigeria-signs-language

---

## 📌 Project Overview
- 📷 **Data Collection:** Images captured with **ESP32-CAM** (programmed via **Arduino IDE**).
- 📝 **Annotation:** Labeled with LabelImg/Roboflow in **YOLO format**.
- 🤖 **Model Training:** Trained a **YOLOv8** model producing `best.pt`.
- 🌍 **Deployment:** **Flask** API for real-time hand gesture recognition.
- 🎯 **Goal:** Practical NSL recognition to support accessibility & inclusion.

---

## 📂 Repository Structure
nigeria-signs-language/
│── app.py # Flask server (inference)
│── requirements.txt # Python dependencies
│── README.md
│── .gitignore
│── dataset/ # Optional: sample or link to dataset
│ ├── train/images/ train/labels/
│ └── val/images/ val/labels/
│── output/
│ └── nsl_yolo_train2/
│ └── weights/
│ └── best.pt # Trained YOLOv8 weights (provide or link)
│── templates/ # Flask HTML (if UI is used)
│── static/ # CSS/JS/assets (if UI is used)
│── esp32_cam/ # Arduino sketches & notes (data collection)

---

## 📜 requirements.txt (minimal)
flask
ultralytics
opencv-python
numpy
torch
torchvision

---







