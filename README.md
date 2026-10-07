# 🚘 AI Automatic Number Plate Recognition (ANPR)

> 🤖 An AI-powered **Automatic Number Plate Recognition system** built using **Python, OpenCV, YOLO, Computer Vision, and OCR**.

The system detects vehicle number plates from images or video, extracts the plate region, preprocesses it for OCR, recognizes the registration number, validates the extracted text, and returns structured results.

---

## 🚀 Project Overview

Automatic Number Plate Recognition (ANPR) is a computer vision technology used to automatically detect and recognize vehicle registration plates.

The complete pipeline is:

```text
🚗 Vehicle Image / Video
          ↓
🖼️ Image Preprocessing
          ↓
🔎 Number Plate Detection
          ↓
✂️ Plate Cropping
          ↓
🧹 Plate Enhancement
          ↓
🔤 OCR
          ↓
📝 Text Normalization
          ↓
✅ Plate Validation
          ↓
📊 Structured Result
```

---

## 🎯 Project Objectives

- 🚘 Detect vehicle number plates
- 🔎 Locate plates using computer vision
- ✂️ Extract the number plate region
- 🧹 Improve image quality for OCR
- 🔤 Recognize registration numbers
- 📝 Clean OCR output
- ✅ Validate registration patterns
- 📊 Measure detection and OCR accuracy
- 🎥 Extend the system to video
- 🚀 Build a deployable ANPR application

---

# ✨ Key Features

## 🔎 1. Number Plate Detection

The first stage identifies the plate region.

The notebook includes a classical computer-vision baseline using:

- Grayscale conversion
- Bilateral filtering
- Edge detection
- Contour detection
- Aspect-ratio filtering
- Area filtering

For production use, this can be upgraded to a trained **YOLO detector**.

```text
🚗 Vehicle
     ↓
🤖 YOLO
     ↓
📦 Bounding Box
     ↓
🚘 Number Plate
```

---

## ✂️ 2. Plate Cropping

After detection, the number plate is cropped from the original image.

```text
Vehicle Image
      ↓
Plate Bounding Box
      ↓
Crop
      ↓
Number Plate Image
```

This reduces irrelevant visual information before OCR.

---

## 🧹 3. Image Preprocessing

OCR accuracy depends heavily on image quality.

The project can apply:

- Grayscale conversion
- Image resizing
- Noise reduction
- Gaussian blur
- Thresholding
- Contrast enhancement
- Perspective correction

```text
Raw Plate
    ↓
Grayscale
    ↓
Resize
    ↓
Denoise
    ↓
Threshold
    ↓
OCR-Ready Image
```

---

# 🔤 4. Optical Character Recognition

OCR converts the plate image into text.

Possible OCR engines include:

- Tesseract OCR
- EasyOCR
- PaddleOCR
- Deep-learning OCR models

Example:

```text
┌──────────────────┐
│   TN 23 AB 1234  │
└──────────────────┘
          ↓
         OCR
          ↓
"TN 23 AB 1234"
```

---

# 🧹 5. OCR Text Cleaning

Raw OCR output can contain unwanted spaces and symbols.

Example:

```text
Raw OCR:

TN 23 - AB 1234

       ↓

Text Normalization

       ↓

TN23AB1234
```

The project converts text to uppercase and removes unnecessary characters.

---

# 🇮🇳 6. Registration Pattern Validation

A simplified Indian registration pattern can resemble:

```text
TN 23 AB 1234
```

Where:

```text
TN    → State Code
23    → RTO / District Code
AB    → Series
1234  → Registration Number
```

Example normalized value:

```text
TN23AB1234
```

⚠️ Real registration systems contain legitimate variations, including special series, temporary registrations, BH-series registrations, older formats, and jurisdiction-specific formats.

Production validation should therefore support the exact registration formats relevant to the deployment.

---

# 🤖 7. YOLO-Based ANPR

The advanced version uses YOLO for plate detection.

```text
                🚗 Vehicle Image
                       │
                       ▼
                🤖 YOLO Detector
                       │
                       ▼
                📦 Plate Bounding Box
                       │
                       ▼
                  ✂️ Plate Crop
                       │
                       ▼
                 🧹 Preprocessing
                       │
                       ▼
                    🔤 OCR
                       │
                       ▼
                 📝 Clean Text
                       │
                       ▼
                   ✅ Validate
```

Potential models:

- YOLOv8
- YOLO11
- Custom object detector

---

# 🏗️ System Architecture

```text
                       🚗 CAMERA
                           │
                           ▼
                  ┌────────────────┐
                  │ Vehicle Frame  │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ Image Quality  │
                  │ Checks         │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ YOLO Plate     │
                  │ Detector       │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ Plate Crop     │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ Preprocessing  │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ OCR Engine     │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ Text Cleaning  │
                  └───────┬────────┘
                          │
                          ▼
                  ┌────────────────┐
                  │ Validation     │
                  └───────┬────────┘
                          │
                          ▼
                  📊 Structured Result
```

---

# 🛠️ Technology Stack

## 🐍 Programming

- Python
- Jupyter Notebook
- NumPy

## 👁️ Computer Vision

- OpenCV
- Image Processing
- Object Detection

## 🤖 Deep Learning

- YOLO
- PyTorch
- Ultralytics

## 🔤 OCR

Potential options:

- EasyOCR
- PaddleOCR
- Tesseract OCR

## 📊 Visualization

- Matplotlib

## 🌐 Production Version

Potential stack:

- FastAPI
- React
- TypeScript
- REST API

---

# 📁 Project Structure

```text
ai-number-plate-recognition-anpr/
│
├── 📓 notebooks/
│   └── AI_Number_Plate_Recognition_ANPR.ipynb
│
├── 📄 README.md
│
├── 📊 dataset/
│   ├── images/
│   └── labels/
│
├── 🤖 models/
│   └── best.pt
│
├── ⚙️ src/
│   ├── detector.py
│   ├── preprocessing.py
│   ├── ocr.py
│   ├── validator.py
│   └── pipeline.py
│
├── 🧪 tests/
│
├── 🌐 api/
│   └── main.py
│
├── 📋 requirements.txt
│
└── .gitignore
```

---

# ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/ai-number-plate-recognition-anpr.git
```

Navigate to the project:

```bash
cd ai-number-plate-recognition-anpr
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Install the core libraries:

```bash
pip install numpy matplotlib opencv-python jupyter
```

Start Jupyter:

```bash
jupyter notebook
```

Open:

```text
AI_Number_Plate_Recognition_ANPR.ipynb
```

---

# 🔥 Advanced YOLO Setup

Install Ultralytics:

```bash
pip install ultralytics
```

Example Python import:

```python
from ultralytics import YOLO
```

Load a trained plate detector:

```python
model = YOLO("best.pt")
```

Run detection:

```python
results = model("vehicle.jpg")
```

The detector should be trained or fine-tuned on an appropriately licensed number-plate dataset.

---

# 🔤 OCR Setup

## EasyOCR

```bash
pip install easyocr
```

Example:

```python
import easyocr

reader = easyocr.Reader(["en"])

result = reader.readtext("plate.jpg")
```

## PaddleOCR

```bash
pip install paddleocr
```

You can compare multiple OCR engines and select the best-performing approach based on your evaluation dataset.

---

# 📊 Evaluation Metrics

A complete ANPR system should evaluate the detector and OCR separately.

## 🔎 Plate Detection

Use:

```text
Precision
Recall
mAP@50
mAP@50:95
IoU
```

---

## 🔤 OCR Evaluation

Use:

```text
Character Error Rate (CER)
Character Accuracy
Exact Plate Match
```

---

## 🚘 End-to-End ANPR

The most important metric is whether the complete registration number is correctly recognized.

Measure:

```text
Full Plate Recognition Rate
Latency Per Image
Failure Rate
Human Review Rate
```

Evaluate across:

- ☀️ Daylight
- 🌙 Night
- 🌧️ Weather variation
- 🏎️ Motion blur
- 📐 Viewing angles
- 🚘 Different vehicle types
- 🔍 Different distances
- 🚧 Partial occlusion

---

# 🎥 Real-Time ANPR

The project can later support video.

```text
📹 Camera
    ↓
Video Frames
    ↓
YOLO Detection
    ↓
Plate Tracking
    ↓
OCR
    ↓
Duplicate Filtering
    ↓
Validated Plate
```

For authorized deployments, duplicate filtering can prevent the same vehicle from being repeatedly recorded across adjacent frames.

---

# 🌐 Web Application

A portfolio version can include:

```text
                💻 React Frontend
                       │
                       ▼
                  📤 Upload Image
                       │
                       ▼
                 ⚡ FastAPI API
                       │
                       ▼
                 🤖 YOLO Model
                       │
                       ▼
                    🔤 OCR
                       │
                       ▼
                📊 Recognition Result
```

Example UI:

```text
┌─────────────────────────────────┐
│ 🚘 AI Number Plate Recognition │
├─────────────────────────────────┤
│                                 │
│      📤 Upload Vehicle Image    │
│                                 │
│      [ Choose Image ]           │
│                                 │
│      [ Detect Plate ]           │
│                                 │
├─────────────────────────────────┤
│ Detected Plate                  │
│                                 │
│ 🚗 TN 23 AB 1234               │
│                                 │
│ Detection Confidence: 96%       │
│ OCR Confidence: 94%             │
└─────────────────────────────────┘
```

---

# 🚀 Development Roadmap

## 🟢 Phase 1 — OpenCV Prototype

- [x] Image loading
- [x] Image preprocessing
- [x] Edge detection
- [x] Contour detection
- [x] Plate cropping
- [x] OCR preprocessing
- [x] Text normalization
- [x] Simplified plate validation

---

## 🔵 Phase 2 — YOLO

- [ ] Collect a legally sourced dataset
- [ ] Annotate number plates
- [ ] Train YOLO
- [ ] Validate model
- [ ] Test real-world images
- [ ] Optimize inference

---

## 🟣 Phase 3 — OCR

- [ ] EasyOCR
- [ ] PaddleOCR
- [ ] Tesseract
- [ ] Perspective correction
- [ ] OCR confidence scoring
- [ ] Character error evaluation
- [ ] Registration format handling

---

## 🟠 Phase 4 — Video

- [ ] Video processing
- [ ] Authorized webcam support
- [ ] Vehicle tracking
- [ ] Plate tracking
- [ ] Duplicate filtering
- [ ] Frame optimization

---

## 🔥 Phase 5 — Full-Stack Application

- [ ] FastAPI backend
- [ ] React frontend
- [ ] Image upload
- [ ] Video processing
- [ ] Recognition dashboard
- [ ] Human review queue
- [ ] Authentication
- [ ] Role-based permissions

---

## 🚀 Phase 6 — MLOps

- [ ] Dataset versioning
- [ ] Experiment tracking
- [ ] Model registry
- [ ] CI/CD
- [ ] Performance monitoring
- [ ] Error analysis
- [ ] Model drift monitoring
- [ ] Secure deployment

---

# 🛡️ Privacy & Responsible AI

Vehicle registration numbers can be sensitive identifiers in real-world deployments.

The system should therefore follow appropriate privacy and security practices.

### 🔐 Data Protection

- Protect stored plate records.
- Encrypt sensitive data where appropriate.
- Restrict access to authorized users.
- Minimize retention of raw vehicle images.

### 👤 Human Review

Low-confidence predictions should be reviewed.

```text
AI Prediction
      ↓
Confidence Check
      ↓
   ┌──┴───┐
   │      │
 High    Low
   │      │
   ▼      ▼
Accept  Human Review
```

### 📝 Audit Logging

Authorized systems should record important operations such as:

```text
User
Timestamp
Recognition Request
Model Version
Confidence
Result
Review Status
```

### ⚖️ Responsible Deployment

ANPR should only be deployed for legitimate and authorized purposes and in accordance with applicable privacy, surveillance, traffic, and data-protection requirements.

The system should not infer the identity of a vehicle owner solely from a registration number without lawful authorization and an appropriate data source.

---

# 💼 Resume Description

> **AI Automatic Number Plate Recognition (ANPR) System** — Developed a computer vision pipeline using Python, OpenCV, YOLO, and OCR to detect vehicle registration plates, extract plate regions, preprocess images, recognize registration text, validate OCR output, and evaluate end-to-end recognition performance, with an extensible architecture for real-time and web-based deployment.

---

# 🏷️ GitHub Topics

```text
python
computer-vision
opencv
yolo
object-detection
ocr
automatic-number-plate-recognition
anpr
license-plate-recognition
deep-learning
pytorch
ultralytics
image-processing
machine-learning
artificial-intelligence
```

---

# ⭐ Project Highlights

```text
🚘 Automatic Number Plate Recognition
👁️ Computer Vision
🤖 YOLO Object Detection
🔤 OCR
🧹 Image Preprocessing
📦 Bounding Box Detection
🇮🇳 Registration Validation
🎥 Video Processing Architecture
⚡ FastAPI
💻 React
📊 Model Evaluation
🛡️ Privacy-Aware Design
🚀 MLOps Roadmap
```

---

# 🎓 Learning Outcomes

By completing this project, you can practice:

### 🐍 Python
- NumPy
- OpenCV
- Image processing

### 👁️ Computer Vision
- Edge detection
- Contours
- Bounding boxes
- Image transformations

### 🤖 Deep Learning
- YOLO
- Object detection
- Model training
- Model evaluation

### 🔤 OCR
- Text recognition
- OCR preprocessing
- Character normalization
- Recognition evaluation

### 🚀 AI Engineering
- Model APIs
- Full-stack inference architecture
- MLOps
- Monitoring
- Responsible deployment

---

# 🔮 Future Vision

The project can evolve into a complete authorized **AI Vehicle Recognition Platform**:

```text
🚗 Vehicle
     ↓
🤖 Vehicle Detection
     ↓
🔎 Plate Detection
     ↓
🔤 OCR
     ↓
✅ Validation
     ↓
📊 Confidence Analysis
     ↓
👤 Human Review
     ↓
📋 Authorized Application Workflow
```

---

# 👨‍💻 Author

**Elavarasu Ravi**

Built as a practical **Computer Vision + Deep Learning + AI Engineering** portfolio project.

---

# ⭐ Support

If you find the project useful, consider giving the repository a ⭐.

> 🚘 **Detect. Recognize. Validate. Build responsible computer vision systems.**
