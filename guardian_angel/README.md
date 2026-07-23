
# 👼 Guardian Angel - AI-Powered Seizure Detection System

**An AI-powered offline smartphone-based epilepsy detection, prediction, and emergency response system.**

[![Streamlit App](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=Streamlit&logoColor=white)](https://guardian-angel.streamlit.app)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com/)

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Key Features](#key-features)
3. [Performance Metrics](#performance-metrics)
4. [Milestones](#milestones)
5. [Technology Stack](#technology-stack)
6. [Installation Guide](#installation-guide)
7. [User Guide](#user-guide)
8. [Project Structure](#project-structure)
9. [Demo Accounts](#demo-accounts)
10. [License](#license)
11. [Acknowledgements](#acknowledgements)

---

## 🏆 Project Overview

Guardian Angel is an **AI-powered offline smartphone-based epilepsy detection, prediction, and emergency response system**. It uses phone motion sensors (accelerometer + gyroscope) to detect seizures in real-time, predict seizure risk, and initiate emergency protocols.

### The Problem

- **50 million people** worldwide have epilepsy
- **70%** could live seizure-free with proper treatment
- **Sudden Unexpected Death in Epilepsy (SUDEP)** is a major concern
- **Real-time detection** can save lives

### Our Solution

Guardian Angel provides:
- ✅ **Real-time seizure detection** using phone motion sensors
- ✅ **AI-powered risk prediction** with explainable results
- ✅ **Automatic emergency response** with GPS location sharing
- ✅ **Offline-first design** — works without internet
- ✅ **No expensive wearables** — just your phone

---

## 🎯 Key Features

| Feature | Description | Status |
|---------|-------------|--------|
| **🧠 Real-time Detection** | CNN+LSTM model trained on 20 real patients | ✅ |
| **📊 Risk Prediction** | Low/Moderate/High risk levels | ✅ |
| **🛡️ Smart Alerts** | Consecutive-window smoothing reduces false alarms by 95% | ✅ |
| **🆘 Welfare Check** | Multi-stage escalation (user → caregiver → emergency) | ✅ |
| **💡 Explainable AI** | SHAP tells WHY, not just WHAT | ✅ |
| **📱 Offline PWA** | Works without internet, installable on phone | ✅ |
| **🚨 Emergency Response** | SMS alerts with GPS location via Twilio | ✅ |
| **👨‍⚕️ Admin Dashboard** | Monitor all patients from one dashboard | ✅ |
| **🔐 Multi-User Auth** | Secure login with Firebase | ✅ |

---

## 📊 Performance Metrics

### Model Performance

| Metric | Value |
|--------|-------|
| **Sensitivity (Recall)** | 63% |
| **Specificity** | 79% |
| **Precision (Before Smoothing)** | 0.7% |
| **Precision (After Smoothing)** | ~15% |
| **False Alarm Reduction** | 95% |
| **Training Data** | 20 patients, 886 seizures |

### Clinical Relevance

- ✅ Trained on real clinical data (SeizeIT2)
- ✅ Model explains decisions via SHAP
- ✅ Phone-based = accessible to everyone
- ✅ Offline-first = works without internet
- ✅ Consecutive-window smoothing = 95% fewer false alarms

---

## 🎓 Milestones

### ✅ Milestone 1 — Data Pipeline & Windowing
- Dataset: SeizeIT2 (OpenNeuro ds005873)
- 20 real patients with 886 seizures
- Signal cleaning and windowing (10s windows, 5s step)
- Feature extraction (mean/std/min/max per signal)
- Processed CSV output: `data/seizeit2_windows.csv`

### ✅ Milestone 2 — Baseline ML Models
- Logistic Regression
- Random Forest
- Performance comparison with confusion matrix
- End-to-end pipeline validation

### ✅ Milestone 3 — CNN+LSTM Seizure Detection
- CNN+LSTM architecture (69,217 parameters)
- Motion-sensor-only detection (Accel + Gyro)
- 63% sensitivity, 79% specificity
- Model saved: `models/seizure_detection_model.h5`

### ✅ Milestone 4 — Monitoring Coverage & Welfare Check
- Monitoring Coverage Tracker
- Welfare Check Protocol
- Escalation: User → Caregivers → Emergency
- Consecutive-window smoothing (3 consecutive windows)

### ✅ Milestone 5 — Explainable AI (SHAP)
- SHAP feature importance analysis
- Top features: ECG (Heart Rate), Accelerometer X, Gyroscope Y
- Plain-language explanations
- Visualization: `evaluation/shap_analysis.png`

### ✅ Milestone 6 — Offline PWA App
- Streamlit-based interface
- Installable via "Add to Home Screen"
- Risk Dashboard, Monitoring Coverage, Welfare Check
- GPS integration, Emergency Contacts
- Seizure/risk history
- Service worker for offline support

### ✅ Milestone 7 — Emergency Response & Evaluation
- Twilio SMS integration
- Real GPS sharing
- Evaluation metrics
- Complete system testing

---

## 🛠️ Technology Stack

| Layer | Technology | Version |
|-------|------------|---------|
| **Frontend** | Streamlit (PWA) | 1.28+ |
| **Backend** | Python | 3.12+ |
| **Machine Learning** | TensorFlow/Keras | 2.13+ |
| **Database** | Firebase Realtime DB | - |
| **Authentication** | Firebase Auth | - |
| **SMS** | Twilio API | 8.10+ |
| **Visualization** | Plotly | 5.17+ |
| **Explainability** | SHAP | 0.42+ |
| **Signal Processing** | MNE, SciPy | 1.5+ |

---

## 🚀 Installation Guide

### Prerequisites

- Python 3.12+
- Git
- Firebase Account (free tier)
- Twilio Account (optional, free trial)

### Step 1: Clone the Repository

```bash
git clone https://github.com/promivine-prog/guardian-angel.git
cd guardian-angel
Step 2: Create Virtual Environment
bash
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate
Step 3: Install Dependencies
bash
pip install -r requirements.txt
Step 4: Configure Firebase
Go to Firebase Console

Create a new project

Enable Email/Password Authentication

Create Realtime Database (test mode)

Get your config keys

Update app/firebase_config.py

Step 5: Configure Environment Variables
Create a .env file:

env
# Firebase
FIREBASE_API_KEY=your_api_key
FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
FIREBASE_DATABASE_URL=https://your_project-default-rtdb.firebaseio.com
FIREBASE_PROJECT_ID=your_project_id

# Twilio (Optional)
TWILIO_ACCOUNT_SID=your_account_sid
TWILIO_AUTH_TOKEN=your_auth_token
TWILIO_FROM_NUMBER=+1234567890
Step 6: Run the App
bash
streamlit run app/app.py
Step 7: Install as PWA on Phone
Open http://localhost:8501 in Chrome

Tap "Add to Home Screen"

Use like any other app!

📱 User Guide
Creating an Account
Open the app

Click "Sign Up" tab

Fill in your details

Select "user" or "admin" role

Click "Create Account"

Login with your credentials

User Dashboard
Section	Description
Seizure Risk	🟢 Low / 🟠 Moderate / 🔴 High
Monitoring	🟢 Active / 🔴 Paused
Coverage	Percentage of time monitored
Total Alerts	Number of alerts received
Real-time Chart	Risk score and motion activity
Alert History	All your past alerts
Quick Actions	I'm Fine / Need Help buttons
Emergency Contacts
In the sidebar, find "Emergency Contacts"

Enter contact phone numbers

Click to save

Contacts receive SMS alerts during emergencies

Welfare Check Flow
text
Seizure Detected (Automatic)
        ↓
User Gets "Are You Okay?" Prompt
        ↓
⏰ Wait 30 seconds
        ↓
No Response? → Caregivers Alerted (SMS)
        ↓
⏰ Wait 60 seconds
        ↓
No Response? → Emergency Alert with GPS
👨‍⚕️ Admin Guide
Admin Dashboard Access
Create an account with role "admin"

Login with admin credentials

Navigate to "Admin Dashboard"

Admin Dashboard Features
Feature	Description
Metrics	Total Users, High Risk, Active Monitoring, Total Alerts
All Users Table	Name, Email, Role, Risk, Monitoring, Contacts
Filter Users	By Role, Risk, Monitoring Status
Export Data	Download CSV of all users
Recent Alerts	View all alerts across users
📁 Project Structure
text
guardian_angel/
├── app/
│   ├── app.py                     # Main Streamlit app
│   ├── auth.py                    # Firebase authentication
│   ├── admin_dashboard.py         # Admin panel
│   ├── firebase_config.py         # Firebase configuration
│   └── __init__.py                # Package init
├── models/
│   └── seizure_detection_model.h5 # Trained CNN+LSTM model
├── evaluation/
│   ├── shap_analysis.png          # SHAP visualization
│   └── shap_explanations.json     # Feature importance
├── preprocessing/
│   └── windowing.py               # Data pipeline
├── data/
│   └── seizeit2_windows.csv       # Processed features
├── .streamlit/
│   └── config.toml                # Streamlit config
├── SYSTEM_MANUAL.md               # Complete system manual
├── README.md                      # This file
├── requirements.txt               # Dependencies
├── .env.example                   # Environment template
└── .gitignore                     # Git ignore
🔑 Demo Accounts
Role	Email	Password
Admin	admin@guardian.com	admin123
User	user@guardian.com	user123


🏆 Competition Submission
What Makes This Project Unique
Real Clinical Data: Trained on SeizeIT2 dataset with 886 real seizures

Explainable AI: SHAP tells WHY predictions are made

Consecutive-Window Smoothing: Reduces false alarms by 95%

Welfare Check Protocol: Multi-stage escalation (user → caregiver → emergency)

Offline-First Design: Works without internet

Phone-Only: No expensive wearables needed

Multi-User Support: Admin + User dashboards

How Judges Can Test
Run streamlit run app/app.py

Use the sidebar to simulate risk levels

Test the welfare check protocol

View SHAP explanations in the dashboard

Install as PWA on phone

📄 License
MIT License - Free for academic and research use.

🙏 Acknowledgements
SeizeIT2 Dataset (OpenNeuro ds005873) — Clinical seizure data

Streamlit — PWA framework and dashboard

TensorFlow — Deep learning framework

SHAP — Model explainability

Twilio — SMS emergency alerts

Firebase — Authentication and database

Plotly — Interactive visualizations

📝 Version History
Version	Date	Changes
v2.0	2026-07-15	Full production release with Firebase + Admin Dashboard
v1.0	2026-07-10	Initial release with all 7 milestones
📞 Contact
GitHub: promivine-prog/guardian-angel

Issues: Report a bug

⭐ Star Us!
If you find this project useful, please give it a star on GitHub!


👼 Guardian Angel — Saving Lives with AI

GUARDIAN ANGEL - DATICAN AI in Medicine Competition 2026
University of Ibadan, Nigeria

Contact: promivine@gmail.com
