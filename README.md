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

## ⚙️ Environment & Installation

### Clone
```bash
git clone https://github.com/centbueze/nigeria-signs-language.git
cd nigeria-signs-language

---

**# Create & Activate Virtual Environment**
python -m venv flaskenv
.\flaskenv\Scripts\activate

---

## python -m venv flaskenv
.\flaskenv\Scripts\activate

---

## Linux/Mac:
python3 -m venv flaskenv
source flaskenv/bin/activate

---

## Install Dependencies
pip install -r requirements.txt

---

## 📜 requirements.txt (minimal)
flask
ultralytics
opencv-python
numpy
torch
torchvision

---

## Then Install
pip install -r requirements.txt

---

## 🚀 Run the Flask App
python app.py

---

## Open in your browser:
http://127.0.0.1:5000/

---
## 🧠 Model Path (important)
from ultralytics import YOLO
model = YOLO("best.pt")

---

## Auto-detect latest best.pt:
import glob, os
from ultralytics import YOLO

candidates = glob.glob(r"runs/**/weights/best.pt", recursive=True) + \
             glob.glob(r"output/**/weights/best.pt", recursive=True)
if not candidates:
    raise FileNotFoundError("No best.pt found under runs/ or output/")

model_path = max(candidates, key=os.path.getctime)
print(f"Using model: {model_path}")
model = YOLO(model_path)

---

## Train (from scratch or fine-tune)
yolo detect train data=dataset/data.yaml model=yolov8n.pt epochs=50 imgsz=640

---

## dataset/data.yaml example:
path: ./dataset
train: train/images
val: val/images
nc: 26
names: [A, B, C,D, E, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z]

---

## 📊 Dataset
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

Use CameraWebServer or custom sketch in esp32_cam/.

Select ESP32-CAM board, correct COM port → Upload.

Open Serial Monitor → get ESP32 IP address.

Visit http://<ESP32_IP>/ to preview stream.

Capture frames by sign → store in dataset folders → label later.

---

## 🖼️ Demo
![V_1752583739738](https://github.com/user-attachments/assets/b238f69e-fa61-4628-b266-e7c5625c2a02)
 
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
No module named 'flask' → run pip install -r requirements.txt inside env.

best.pt not found → fix model path or use auto-detect snippet.

Wrong Python used → ensure (flaskenv) is active → run python --version.

---

## 🙏 Acknowledgements
Ultralytics YOLOv8

ESP32-CAM + Arduino IDE

Nigerian Sign Language Community

Push rejected (large files) → use Git LFS or don’t commit heavy models.






