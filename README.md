# 🐄 CowSense - AI-Powered Cattle Disease Detection System

Welcome to **CowSense**! 🚀  
An **AI + IoT powered smart livestock health management system** designed to monitor cattle vitals, detect diseases using computer vision, and streamline farmer-veterinarian interaction. 🧠📱🌾

---

## 📌 Table of Contents
- [✨ Key Features](#-key-features)
- [📱 Mobile Applications](#-mobile-applications)
- [📦 Tech Stack](#-tech-stack)
- [🧠 AI Model Details](#-ai-model-details)
- [🔗 Live Demo & Model Previews](#-live-demo--model-previews)
- [📡 IoT Device - CowLink](#-iot-device---cowlink)
- [📲 System Architecture](#-system-architecture)
- [🚀 Getting Started](#-getting-started)
- [🛠 Installation](#-installation)
- [📜 License](#-license)
- [🙋‍♂️ Maintainer](#-maintainer)

---

## ✨ Key Features

✅ AI-powered disease detection via image upload/live camera 📷  
✅ Annotated image reports with disease type & accuracy 💉📄  
✅ CowLink IoT collar with real-time vitals monitoring 📊  
✅ Alerts for abnormal readings 🚨  
✅ In-app vet consultation & appointment booking 🩺  
✅ Gemini AI support for farmers 🤖  
✅ Profile & animal management for both users 👤  
✅ Real-time chat between farmer and vet 💬

---

## 📱 Mobile Applications

We built **two Flutter-based mobile apps**:

### 👨‍🌾 Farmer App
- Real-time vitals dashboard from CowLink
- Disease prediction with AI model
- Chat with vets
- Book appointments
- Gemini AI Assistant
- Share AI reports with vets

### 🩺 Vet App
- Accept/Reject appointments
- View AI reports & update consult status
- Suggest medication
- Real-time chat with farmers

> 🔒 Both apps include secure login & registration flows.

---

## 📦 Tech Stack

| Layer        | Technology Used                     |
|--------------|-------------------------------------|
| Frontend     | Flutter (Farmer + Vet Apps)         |
| Backend      | Node.js + Express.js                |
| AI Model     | YOLOv8m (Trained on Google Colab)   |
| Dataset      | Roboflow Annotated Dataset          |
| Hosting/API  | Render, HuggingFace, Roboflow       |
| IoT Board    | ESP32 with sensors                  |
| DB           | Cloud-based MongoDB 🟢              |

---

## 🧠 AI Model Details

- 📸 Model Type: YOLOv8m Object Detection
- 🏷️ Annotated with: **Roboflow**
- 📍 Trained on: Google Colab (Python, Ultralytics)
- 🚀 Deployment: Hugging Face Space + Roboflow Space
- 🧪 Output: Annotated images, confidence score, disease label

#### 🔍 Model Capabilities:
- Detect visible diseases on cattle skin/body
- Annotate affected areas
- Generate report with disease name + accuracy

> 📚 The model is trained to **self-improve** by saving feedback & future annotations.

---

## 🔗 Live Demo & Model Previews

🔬 **Roboflow Preview**:  
👉 [Roboflow CowSense Model](https://app.roboflow.com/visionvet/cowsense/models/cowsense/1)

🤖 **Hugging Face AI Space**:  
👉 [Hugging Face Model Live Demo](https://huggingface.co/spaces/malikTayab/cowsense-disease-detector)

📸 **Sample Model Output**  
*(Insert sample AI model annotated image here)*  
![AI Sample Output](images/ai_model_output.png)

---

## 📡 IoT Device - CowLink

🧠 **CowLink** is a custom-built smart collar worn by cattle. It collects vital health data and sends it to our backend server in real time.

### 🧰 Sensor Suite
- **ESP32** (Microcontroller)
- **DS18B20** – Body Temperature 🌡️
- **DHT22** – Environment Temp & Humidity 🌦️
- **MAX30102** – Heart Rate & SpO2 ❤️
- **MPU6050** – Motion, Rest & Activity 📈
- **GPS Module** – Real-time Location 🗺️

📤 Sensor data is transmitted to a **Node.js/Express.js server** hosted on **Render**, then shown in the farmer app.

🔔 Abnormal readings generate **instant alerts** to the farmer.

🖼️ *CowLink Device Images*  
*(Insert device images here)*  
![CowLink Device](images/cowlink_device.jpg)

---

## 📲 System Architecture

```mermaid
graph TD
A[Farmer App] -->|View Vitals & Upload Image| B(Server API)
VetApp[Veterinarian App] -->|View Reports & Consult| B
CowLink[IoT Collar] -->|Sensor Data| B
B -->|Store & Retrieve Data| DB[(MongoDB)]
B -->|Invoke AI Model| AIModel[YOLOv8m - Hugging Face]
