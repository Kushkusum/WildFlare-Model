# 🌲 Forest Fire Detection System

An IoT + AI based project to detect and confirm forest fires using sensors, an ESP32-CAM, and a Convolutional Neural Network (CNN).  
The system provides **early fire detection** to reduce response time and prevent large-scale damage.

---

## 🔥 Project Need
Forest fires cause severe ecological and human loss. Traditional detection methods (watchtowers, satellites, patrols) are **slow and error-prone**.  
This project addresses those challenges by combining IoT sensors with AI for:
- **Early detection** using temperature, humidity, infrared, and smoke sensors.  
- **High accuracy** fire confirmation via CNN.  
- **Energy efficiency** (ESP32-CAM activates only when sensors detect anomalies).  
- **Automated alerting** via buzzer upon fire confirmation.  

---

## 🛠 Tools, Technologies & Models Used

### Hardware
- ESP32-CAM + NodeMCU32  
- Infrared Sensor (heat detection)  
- Air Quality Sensor MQ-135 (smoke detection)  
- Temperature & Humidity Sensor  
- Buzzer  

### Software
- Arduino IDE (ESP32 code deployment)  
- Google App Script (uploads images to Drive)  
- Google Drive (image storage)  
- Google Colab (CNN inference)  
- TensorFlow / Keras (CNN model training & testing)  

### Model
- Convolutional Neural Network (CNN)  
- Trained model saved as `CNN_FIRE_DETECT.h5`  

---

---

## 🚀 How to Run the Project

### 1. **Arduino & ESP32-CAM Setup**
- Open `CameraWebServer_copy.ino` in **Arduino IDE**.  
- Install ESP32 board support in Arduino IDE.  
- Replace:
  - `ssid` and `password` with your WiFi credentials.  
  - Script URL with your Google App Script deployment link.  
- Upload the code to **ESP32-CAM**.  

### 2. **Google App Script**
- Go to [Google App Script](https://script.google.com).  
- Create new project → paste **`ESP32_CAM.json`** contents.  
- Save → Deploy as **Web App** → copy deployment link.  
- Paste this link inside Arduino `.ino` file.  

### 3. **Google Drive**
- Images from ESP32-CAM are uploaded to a Drive folder via App Script.  

### 4. **CNN Model in Google Colab**
- Open `CNN_FIRE_DETECT.ipynb` in **Google Colab**.  
- Mount Google Drive:  
  ```python
  from google.colab import drive
  drive.mount('/content/drive')
---


