# 🌱 Bio-Bubble AI – Smart Plant Health Dashboard
**AI-powered predictive plant monitoring with real-time IoT integration**

---

Bio-Bubble AI is a smart plant-care dashboard that monitors environmental conditions, predicts plant stress, gives AI recommendations, and lets you remotely control a water pump — all from a beautiful web interface.

This project integrates:

✔ **ESP8266 Sensor Node**  
✔ **ThingSpeak Cloud IoT Platform**  
✔ **AI Prediction Model (Gradient Boosting)**  
✔ **Modern Web Dashboard (HTML + JS + Chart.js)**  
✔ **Manual Water Pump Control**

---

## 🚀 Key Features

### 🌡 Real-Time Monitoring
- Temperature
- Humidity
- Soil Moisture
- Current Stress Level
- Predicted Stress Level (AI Model)

### 💧 Smart Water Automation
- Manual water pump trigger from dashboard
- Auto-watering when soil moisture is low
- Pump activity counter (Field 6)

### 🤖 AI-Powered Insights
- Gradient Boosting Model predicts future stress (Field 5)
- AI recommendations based on temp, humidity, soil
- Personalized tips for plant health

### 📈 Beautiful Analytics
- Live charts using Chart.js
- Environment trends
- Stress timeline
- Summary of last 50 readings
- Real-time clock display

### ☁️ Cloud Sync with ThingSpeak
- **Field1** → Temperature
- **Field2** → Humidity
- **Field3** → Soil moisture
- **Field4** → Current stress
- **Field5** → Predicted stress
- **Field6** → Pump count
- **Field7** → Manual pump trigger

---

## 📡 IoT Architecture

```
ESP8266 ──> ThingSpeak ──> Bio-Bubble AI Web App
   ↑               ↓
   └──── Pump Control (Field 7)
```

### Hardware Used
- NodeMCU ESP8266
- DHT11 Sensor (Temp & Humidity)
- Soil Moisture Sensor
- Relay Module
- Mini Water Pump
- 5V Supply

---

## ⚙️ Web App Setup

### 1. Clone the Repo
```bash
git clone https://github.com/your-username/bio-bubble-ai.git
cd bio-bubble-ai
```

### 2. Update ThingSpeak Details

Inside `index.html`, update:

```javascript
const CHANNEL_ID = "YOUR_CHANNEL_ID";
const READ_API_KEY = "YOUR_READ_KEY";
const WRITE_API_KEY = "YOUR_WRITE_KEY";
```

### 3. Run the Web App

This is a static web app — you can run it with:

**Option A – VS Code Live Server**
- Install "Live Server" extension
- Right-click → Open with Live Server

**Option B – Local Python Server**
```bash
python3 -m http.server 8080
```

**Option C – Deploy to Vercel**
```bash
vercel deploy
```

---

## 🤖 AI Prediction Model (Colab)

The Colab notebook:

✔ Fetches ThingSpeak data  
✔ Trains a Gradient Boosting model  
✔ Predicts stress every 10 minutes  
✔ Uploads prediction to Field 5  
✔ Web app fetches it automatically

```python
update_thingspeak_predicted_stress(predicted_stress)
```

*(Include link to your notebook here)*

---

## 🔌 ESP8266 Firmware

The ESP8266 code:

- Reads DHT11 + soil moisture
- Calculates stress
- Sends data to ThingSpeak
- Reads Field 7 for manual pump trigger
- Runs pump automatically if soil < 30%
- Updates pump cycle count (Field 6)

*(Add a link to code file)*

---

## 🗂 Project Structure

```
bio-bubble-ai/
│── index.html         # Main dashboard
│── assets/
│     ├── banner.png
│     ├── dashboard.png
│     └── charts.png
│── README.md
│── /esp8266-code/
│── /colab-model/
```

---

## 📊 ThingSpeak Fields

| Field   | Purpose                    |
|---------|----------------------------|
| Field1  | Temperature                |
| Field2  | Humidity                   |
| Field3  | Soil Moisture              |
| Field4  | Current Stress             |
| Field5  | Predicted Stress (AI)      |
| Field6  | Pump Count                 |
| Field7  | Manual Pump ON/OFF (1 or 0)|

---

## 🌟 Why Gradient Boosting?

- Works well with small IoT datasets
- Captures non-linear environmental relationships
- High accuracy for stress prediction
- More reliable than Random Forest in small data scenarios

---

## 🧪 AI Recommendations

The web app generates personalized suggestions based on:

- Soil dryness
- Temperature extremes
- Humidity imbalance
- Stress level predictions

**Example:**

> Critical stress detected.  
> Move plant to a cooler area and water immediately.

---

## 🧩 Future Improvements

- Add plant species-specific models
- Add LSTM time-series forecasting
- Multi-sensor support (light, CO₂)
- Mobile app version
- Voice assistant integration

---

## 📜 License

MIT License

---

## 💙 Contributors

**Srikanth** – IoT + Web App + ML  
**AI & Code Support** – ChatGPT
