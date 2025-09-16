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

## 🖥 File Usage Summary (Detailed)

- **/arduino/**
  - `CameraWebServer_copy.ino` → Arduino sketch for ESP32-CAM.  
    - Upload via **Arduino IDE** after updating WiFi SSID, password, and Google App Script URL.  
  - `Base64.cpp` / `Base64.h` → Utility files used by the ESP32-CAM sketch for encoding captured images before upload.  

- **/scripts/**
  - `ESP32_CAM.json` → Google App Script.  
    - Copy contents into a new Google App Script project.  
    - Deploy as **Web App** to connect ESP32-CAM → Google Drive.  

- **/notebooks/**
  - `CNN_FIRE_DETECT.ipynb` → Colab notebook to train or test the CNN model.  
    - Use if you want to re-train the model or verify predictions.  
  - `Automated.ipynb` → Optional notebook with automation logic (monitoring uploaded images and predicting fire presence automatically).  

- **/models/**
  - `CNN_FIRE_DETECT.h5` → Pre-trained CNN model file.  
    - Load this in Colab for predictions.  
    - If this file is **not included** (due to GitHub size limits), you can re-train using `CNN_FIRE_DETECT.ipynb` and save it with:  
      ```python
      model.save('CNN_FIRE_DETECT.h5')
      ```  
    - Then place it in `/models/` or directly in your Google Drive.  

- **/data/**
  - `Data-Set.zip` → Image dataset used for training/testing the CNN.  
    - Extract and use with the Colab notebook for training.  


📌 If You Don’t Have the Model File
If `CNN_FIRE_DETECT.h5` is not present in the repo (due to GitHub file size limits):  
1. Open `CNN_FIRE_DETECT.ipynb` in Google Colab.  
2. Train the CNN on your dataset (`Data-Set.zip`).  
3. Save the trained model:  
   ```python
   model.save('CNN_FIRE_DETECT.h5')

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


