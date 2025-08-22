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

## 🧠 Model Path (important)
from ultralytics import YOLO

model_path = r"output/nsl_yolo_train2/weights/best.pt"

model = YOLO(model_path)

---

## 🧪 Quick Inference (CLI)
yolo predict model=output/nsl_yolo_train2/weights/best.pt source=0
# or
yolo predict model=output/nsl_yolo_train2/weights/best.pt source="sample.jpg"

---

## 🎯 Training
yolo detect train data=dataset/data.yaml model=yolov8n.pt epochs=50 imgsz=640


---

## 📄Dataset/data.yaml
path: ./dataset

train: train/images

val: val/images

nc: 26

names: [A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z]

---

## 📊 Dataset Structure
dataset/

├── train/
│   ├── images/
│   └── labels/

└── val/
    ├── images/
    └── labels/

---

## 📲 ESP32-CAM Data Collection (Arduino)
Install Arduino IDE + ESP32 board support (Boards Manager → “esp32”).

Flash CameraWebServer or custom sketch in esp32_cam/.

Select ESP32-CAM board + correct COM port → Upload.

Open Serial Monitor → copy ESP32 IP address.

Visit http://<ESP32_IP>/ → live stream.

Capture gesture frames → save into dataset folders → label later.

---

## 🖼️ Demo
![V_1752583739738](https://github.com/user-attachments/assets/5f7764e0-c27a-47da-9a99-0c91cd4e429b)

---

## 🔧 .gitignore
flaskenv/

venv/

__pycache__/

*.pyc
*.pkl
*.onnx
*.h5
*.pth
*.dll
*.so
*.lib
runs/

---

## 🧩 Troubleshooting
pip install -r requirements.txt

---

## 🙏 Acknowledgements
Ultralytics YOLOv8
ESP32-CAM + Arduino IDE
Nigerian Sign Language Community
GitHub LFS (Large Files) for handling .pt models

---

## 🐧🍎 Linux / Mac
```bash
python3 -m venv flaskenv
source flaskenv/bin/activate
```

---

## 🚀 Run the Flask App
python app.py

---

## 🌐 Open in your browser
[Ultralytics YOLOv8
ESP32-CAM + Arduino IDE
Nigerian Sign Language Community
GitHub LFS (Large Files) for handling .pt models](http://127.0.0.1:5000/)

---

