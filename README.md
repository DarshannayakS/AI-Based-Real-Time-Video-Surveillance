# AI-Based Real-Time Video Surveillance System for Anomaly Detection and Alert Generation

An intelligent AI-powered surveillance system that automatically detects anomalous activities from video streams in real time using Deep Learning and generates instant alerts with recorded evidence clips.

This project transforms traditional CCTV systems into smart surveillance systems by integrating video understanding, anomaly detection, automated alerting, and intelligent event monitoring.

---

## Project Overview

Traditional CCTV systems continuously record footage but rely heavily on human operators for monitoring. Continuous manual monitoring is difficult, time-consuming, and prone to human error.

This project introduces an AI-based surveillance solution capable of automatically understanding video content and identifying suspicious or abnormal activities.

The system uses an R3D-18 (3D Residual Network) architecture to learn both visual appearance and motion patterns from videos and generate smart alerts whenever anomalies occur.

---

## Key Features

1. Real-time anomaly detection

2. R3D-18 based deep learning model

3. Transfer learning using Kinetics-400 pretrained weights

4. Partial layer freezing for better generalization

5. Sliding window clip buffering

6. Prediction smoothing using majority voting

7. Automatic anomaly clip recording

8. AVI → MP4 conversion using FFmpeg

9. Email alert generation with evidence clips

10. Supports uploaded videos and live camera streams

---

## System Architecture

```text
Video Input
     ↓
Frame Extraction
     ↓
Clip Buffering
     ↓
Preprocessing
     ↓
R3D-18 Model Inference
     ↓
Softmax Prediction
     ↓
Prediction Smoothing
     ↓
Decision Threshold
     ↓
Anomaly Detection
     ↓
Clip Recording
     ↓
FFmpeg Conversion
     ↓
Email Alert
```

---

## Model Architecture

### Model Used

R3D-18 (3D Residual Network)

### Transfer Learning

Pretrained on:

Kinetics-400 Dataset

### Partial Freezing Strategy

Frozen Layers:

- Layer 1
- Layer 2

Trainable Layers:

- Layer 3
- Layer 4
- Fully Connected Layer

### Input Shape

```text
Batch × 3 × 8 × 96 × 96
```

Output Classes:

- Normal
- Anomaly

---

## Dataset Information

Dataset sources:

- Campus CCTV recordings
- UCF-Crime dataset
- Public surveillance datasets
- Custom CCTV videos
- Movie fight clips

Final dataset distribution:

| Class | Samples |
|---------|----------|
| Normal | ~3600 |
| Anomaly | ~3500 |

Included anomaly scenarios:

- Fighting
- Theft
- Suspicious behavior
- Crowd abnormalities
- Movie fight scenes

---

## Technologies Used

| Component | Technology |
|------------|------------|
| Deep Learning Framework | PyTorch |
| Model Architecture | R3D-18 |
| Video Processing | OpenCV |
| Data Handling | NumPy |
| Training Utilities | Scikit-learn |
| Visualization | Matplotlib |
| Alert System | SMTP |
| Video Conversion | FFmpeg |
| Development Environment | Ubuntu |
| GPU Support | CUDA |

---

## Installation

Clone repository:

```bash
git clone https://github.com/YOUR_USERNAME/AI-Based-Video-Surveillance.git

cd AI-Based-Video-Surveillance
```

Create virtual environment:

```bash
python -m venv venv
```

Activate environment:

Linux:

```bash
source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Run Project

Run the anomaly detection system:

```bash
python app.py
```

The system starts processing video input and performs:

- Frame extraction
- Clip buffering
- Video preprocessing
- R3D-18 inference
- Anomaly detection
- Automatic clip recording
- Email alert generation

Supports:

- Uploaded video files
- CCTV footage
- Live camera streams

---

## Training Configuration

| Hyperparameter | Value |
|---------------|--------|
| Image Size | 96×96 |
| Clip Length | 8 Frames |
| Batch Size | 4 |
| Learning Rate | 1e-4 |
| Maximum Epochs | 15 |
| Early Stopping | Patience = 5 |
| Loss Function | CrossEntropyLoss |

---

## Performance Metrics

| Metric | Value |
|----------|---------|
| Test Accuracy | 98.23% |
| Train Accuracy | 99.41% |
| F1 Score | 0.9823 |
| Precision | 0.9824 |
| Recall | 0.9823 |
| Test Loss | 0.0905 |

---

## Inference Performance

GPU:

- ~30 FPS
- ~33 ms prediction latency

CPU:

- ~8 FPS
- ~125 ms prediction latency

Alert Generation:

- Less than 5 seconds

---

## Project Structure

```text
AI-Based-Video-Surveillance/
│
├── app.py
├── train.py
├── inference.py
│
├── saved_models/
│   └── best_model.pth
│
├── dataset/
│   ├── normal/
│   └── anomaly/
│
├── clips/
│
├── notebooks/
│   └── AI-Based Real-Time Video Surveillance.ipynb
│
├── requirements.txt
├── README.md
│
└── assets/
```

---

## Challenges Faced

### Dataset Bias

Initial datasets mostly contained CCTV footage which caused poor generalization on movie scenes.

### Movie vs CCTV Domain Gap

Movie fight scenes contained:

- Different camera angles
- Dynamic lighting
- Professional choreography

Solution:

Added approximately 200 movie clips and retrained the model.

### False Positives

Normal activities such as:

- Fast walking
- Crowd movement
- Running children

were initially detected as anomalies.

Solution:

- Prediction smoothing
- Majority voting
- Dataset expansion

### Overfitting

Solutions used:

- Transfer learning
- Layer freezing
- Early stopping
- Random clip sampling

---

## Future Improvements

- Multi-class anomaly detection
- Multiple camera support
- Mobile push notifications
- Infrared camera support
- Cloud deployment
- Longer temporal analysis
- Edge deployment optimization

---

## Results

The proposed AI surveillance system successfully transformed traditional CCTV monitoring into an intelligent automated anomaly detection platform.

Key achievements:

- High anomaly detection accuracy
- Reduced false positives
- Real-time processing capability
- Automated alert generation pipeline
- Efficient surveillance monitoring

---

## Author

**Darshan S**

B.Tech (Hons.) — Data Science  
School of Engineering and Technology  
Vidyashilp University  

GitHub: https://github.com/DarshannayakS

---

## References

1. Tran et al., Learning Spatiotemporal Features with 3D CNNs (ICCV 2015)

2. Hara et al., Can Spatiotemporal 3D CNNs Retrace the History of 2D CNNs? (CVPR 2018)

3. Sultani et al., Real-world Anomaly Detection in Surveillance Videos (CVPR 2018)

4. Simonyan & Zisserman, Two-Stream Convolutional Networks for Action Recognition

---

If you found this project useful, consider giving it a star.
