# 🐘 WildGuardX – Smart Agro-Defense Against Wildlife Intrusions

**WildGuardX** is an open-source, AI-powered, and IoT-driven solution to **safeguard farmlands from wild elephant intrusions and crop damage**—a growing and critical issue affecting agriculture across Sri Lanka and many other regions of the world.

---

## 📈 Our Vision

> **“Protecting Farms. Empowering Farmers. Saving Wildlife.”**  
> Through technology, we aim to foster coexistence between communities and nature, reducing human-elephant conflict and ensuring sustainable agriculture.

---

## 🌍 The Problem

Elephant intrusions into farms and villages are a **frequent and severe problem in rural Sri Lanka**. Despite the use of electric fences, many farmers face:

- ❌ **Fence malfunctions** due to power issues, physical damage, or lack of monitoring
- ❌ **Human error** in manually turning fences ON/OFF
- ❌ **Delayed response time** to damage or animal movements
- ❌ **No visibility** on fence health or elephant activity until it's too late
- ❌ **Significant crop loss and economic damage**

---

## ✅ Our Solution

**WildGuardX** addresses these challenges with a **phased, modular, and intelligent system** that automates electric fence control, monitors fence health in real time, and integrates AI-based early detection to help farmers **act before destruction happens**.

We aim to empower farmers with:

- 📡 **IoT-based smart electric fence control**
- ⚡ **Sensor-based fault detection and cluster heatmaps**
- 🤖 **AI/Computer Vision-based elephant detection**
- 🔔 **Instant alerts via SMS, WhatsApp, and Email**
- 🧠 **Offline-ready, fail-safe and energy-efficient design**
- 🛰️ **Support for GSM, NB-IoT, LoRaWAN, and multi-fallback connectivity**

---

## 🧱 Architecture – Phased Modular System

WildGuardX is developed in **three integrated phases**, each with its own component and repository:

| Phase | Subsystem           | Description |
|-------|---------------------|-------------|
| **1** | `wildguardx-link`   | Remote/manual/scheduled electric fence control with physical override and alert feedback |
| **2** | `wildguardx-pulse`  | Real-time voltage/current monitoring, sensor fault detection, and cluster-based health heatmap |
| **3** | `wildguardx-vision` | AI & computer vision-based wildlife detection using edge computing (Jetson Nano/RPi + cameras) |

In addition, we support:

- **`wildguardx-dashboard`**: Web/mobile UI to manage, visualize, and analyze data
- **`wildguardx-cloud`**: MQTT brokers, REST APIs, alerting services, and backend
- **`wildguardx-hardware`**: Circuit schematics, PCBs, power systems, solar backups
- **`wildguardx-docs`**: Architecture diagrams, installation manuals, user guides
- **`wildguardx-simulations`**: Simulations and test cases for field-level validation

---

## 🖥️ Explore Our Projects

| Repository | Purpose |
|------------|---------|
| [`wildguardx-link`](https://github.com/WildGuardX/wildguardx-link) | Smart fence control firmware and hardware |
| [`wildguardx-pulse`](https://github.com/WildGuardX/wildguardx-pulse) | Health & fault monitoring via sensors |
| [`wildguardx-vision`](https://github.com/WildGuardX/wildguardx-vision) | AI-powered detection of elephants using CV |
| [`wildguardx-dashboard`](https://github.com/WildGuardX/wildguardx-dashboard) | Web/mobile interface for control & analytics |
| [`wildguardx-cloud`](https://github.com/WildGuardX/wildguardx-cloud) | MQTT, alerts (SMS, Email, WhatsApp), APIs |
| [`wildguardx-hardware`](https://github.com/WildGuardX/wildguardx-hardware) | Power systems, PCBs, enclosure design |
| [`wildguardx-docs`](https://github.com/WildGuardX/wildguardx-docs) | Documentation and setup guides |
| [`wildguardx-simulations`](https://github.com/WildGuardX/wildguardx-simulations) | Simulations and synthetic test environments |

---

## 🔧 Technologies Used

### 💻 Embedded Systems & Microcontrollers
- **ESP32** – Primary IoT platform for remote fence control and sensor integration  
- **STM32L0 Series** – Optional ultra-low-power nodes for standalone monitoring  
- **GPIO / Relay Control** – For electric fence activation and physical override  
- **ADC / Digital IO** – For voltage, current, tamper, and override sensors

### 📡 Connectivity & Communication
- **GSM/4G (SIM800L / SIM7600)** – Primary cellular-based communication for MQTT/SMS  
- **NB-IoT (SIM7020 / BC95)** – For LPWAN-based data transmission  
- **LoRa / LoRaWAN** – For internal section-to-gateway communication without internet  
- **Wi-Fi** – For OTA updates or fallback when available  
- **MQTT (QoS 1)** – Core messaging protocol for telemetry and commands  
- **HTTP / REST API** – Backup communication and alert triggering  
- **Offline Failover Logic** – Ensures the system works autonomously without cloud access

### ⚙️ Sensors & Hardware Interfaces
- **Voltage Sensors (e.g., ZMPT101B)** – To monitor fence output voltage  
- **Current Sensors (e.g., ACS712)** – To detect flow status and faults  
- **Tamper / Reed Switches / PIR Sensors** – For physical breach detection  
- **Manual Override Switch** – Fence activation in emergencies  
- **Battery Management ICs (e.g., TP4056, DW01)** – Battery protection and charge control  
- **Solar Charging Modules** – For off-grid operation with battery backup  
- **Status Indicators (LEDs / Buzzers)** – For visual and audible local alerts

### ☁️ Cloud & Backend Systems
- **Mosquitto MQTT Broker** – Handles real-time data exchange  
- **Node.js / Express** – RESTful API backend and alert engine  
- **Firebase / AWS Lambda** – Cloud automation and push alert services  
- **MQTT Explorer / Grafana** – Development and live data visualization

### 🌐 Frontend / Dashboard
- **React + TailwindCSS** – Modern web dashboard with real-time updates  
- **Flutter** *(planned)* – Cross-platform mobile app for farmers and admins  
- **Mapbox / Leaflet.js** – Visual heatmaps and cluster-based monitoring views  
- **WebSocket / MQTT.js** – For real-time UI updates and interaction

### 🤖 AI & Computer Vision (Phase 3)
- **Jetson Nano / Raspberry Pi 4** – Edge inference for CV-based detection  
- **YOLOv5 / YOLOv8 / MobileNet SSD** – Wildlife object detection models  
- **OpenCV + TensorFlow Lite / ONNX Runtime** – Real-time image processing  
- **Infrared / USB Cameras** – 24/7 animal movement detection in all conditions

---

## 🔔 Notifications & Alert Channels

| Channel        | Purpose                                                          | Implementation                                                  |
|----------------|------------------------------------------------------------------|------------------------------------------------------------------|
| **SMS Alerts** | Critical alerts like fence OFF, breach, low voltage, or failure | GSM Module (e.g., SIM800L) or via Twilio SMS API                |
| **WhatsApp**   | Real-time updates on system health, animal detection, events     | WhatsApp Business API (e.g., via Twilio or Gupshup integration) |
| **Email**      | Periodic reports, daily summaries, and system alerts             | SMTP (Gmail, SendGrid) or cloud-based mail APIs                 |
| **MQTT**       | Fence state, sensor health, alerts, and commands                 | MQTT protocol with QoS 1, retained messages                     |
| **App Push** *(Planned)* | Mobile notifications for users and workers                   | Firebase Cloud Messaging (FCM)                                  |
| **LED / Buzzer** | On-device visual and audible feedback for local users         | GPIO-controlled local alert modules                             |
| **Web Dashboard** | Live alert banners, logs, and cluster health markers         | React frontend connected via MQTT or WebSockets                 |

> 💡 Alerts are intelligently routed via available channels with **failover logic** to ensure delivery, even during limited connectivity scenarios.

## 🤝 Contribute to the Mission

We believe in open collaboration and community-driven development.

### 🧩 How You Can Help:
- 💡 Suggest features or report issues via GitHub Issues
- 🛠️ Contribute code, docs, hardware design, or AI models
- 🧪 Test in field environments and provide feedback
- 🌱 Help with translation/localization for rural deployment
- 🌍 Collaborate on deployments with NGOs or institutions

> 🔗 Join our discussions [here](https://github.com/WildGuardX/.github/discussions) *(enable this if you haven’t already)*

## 📬 Contact Us

For partnerships, questions, or field deployment support:

📧 `wildguardx.project@gmail.com`  
🌐 GitHub: [github.com/WildGuardX](https://github.com/WildGuardX)  

---

![WildGuardX Logo](https://raw.githubusercontent.com/WildGuardX/.github/main/profile/assets/logo.png)

<p align="center"><i>Built with ❤️ in Sri Lanka by farmers, engineers, and conservationists</i></p>
