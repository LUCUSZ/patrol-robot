# 🛡️ **Patrol Robot**

*Autonomous JetBot System for Navigation, Detection, and Patrol Operations*

---

## 🚀 **Overview**

**Patrol Robot** is an intelligent JetBot-based autonomous system designed for security, monitoring, and environmental awareness.
The robot can navigate predefined patrol routes, avoid obstacles, detect humans and fire, return to a home location via GPS, and stream real-time camera footage to a web dashboard.

This project integrates **robot motion control**, **AI-based detection**, **GPS navigation**, and a **Flask web interface** into one complete patrol solution.

---

## ⚡ **Before You Start (Power & Safety Instructions)**

### 🔋 **1. Power On the JetBot**

To operate the Patrol Robot safely and correctly:

* Switch on the **JetBot main power**.
* Turn on the **battery pack** and ensure it is sufficiently charged.
* Allow a few seconds for the Jetson Nano to fully boot.

### 🛰️ **2. GPS Recommendations**

For accurate GPS tracking and reliable route-following:

* **Run the robot outdoors** in an open, unobstructed area.
* Avoid tall buildings, indoor environments, or covered areas.
* GPS requires **direct line-of-sight to the sky**.
* Allow **10–30 seconds** for the GPS module to lock onto satellites.

---

## 🔥 **Key Features**

### 🤖 **Autonomous Navigation**

* Rectangle patrol modes (ROUTE1 – small, ROUTE2 – large)
* Real-time obstacle avoidance using ultrasonic sensors
* GPS-based return-to-home navigation

### 🧠 **AI Detection System**

* Person detection using MobileNetSSD
* Fire detection using HSV color segmentation
* Blocked-path prediction using collision-avoidance neural network
* Alerts saved with snapshots + GPS coordinates

### 📡 **Live Dashboard**

* MJPEG live camera stream
* Manual control buttons (forward, back, turn, spin)
* Patrol mode control + AI toggle
* Alerts viewer with images and timestamps
* GPS status display

---

## 🧱 **System Architecture**

```
Patrol Robot
│
├── Sensors: Ultrasonic, GPS, Camera
├── Motion Control: JetBot motors (Robot API)
├── AI Models: MobileNetSSD, AlexNet (blocked), HSV fire detection
├── Web Server: Flask (REST API + MJPEG stream)
└── Threads:
      ├── camera_loop()
      ├── gps_loop()
      └── control_loop()
```

---

## ⚙️ **Installation**

```bash
git clone <your-repo-url>
cd patrol_robot
pip install -r requirements.txt
```

For Jetson Nano (JetBot):

```bash
sudo apt install python3-opencv python3-pip
pip3 install flask torch torchvision jetbot
```

---

## ▶️ **How to Run**

Start the robot system:

```bash
python patrol_robot.py
```

Open the dashboard in your browser:

```
http://<robot-ip>:5000
```

---

## 🎮 **Dashboard Controls**

### **Manual Control**

* Forward
* Backward
* Turn Left / Right
* Spin
* Stop

### **Patrol Modes**

* ROUTE1 (Small Rectangle)
* ROUTE2 (Large Rectangle)
* Return Home (GPS)
* Idle
* Toggle AI Detection

### **GPS Tools**

* Set Home Position
* Show current coordinates

---

## 🧩 **Core Functions**

### **Navigation**

* `drive_forward(speed, duration)`
* `turn_left(speed, duration)`
* `stop_robot()`
* `step_rectangle(mode)`

### **Sensors**

* `read_ultrasonic_cm()`
* `parse_nmea_lat_lon()`
* `bearing_deg()` / `haversine_m()`

### **AI Detection**

* `predict_blocked(frame)`
* `run_detection(frame)`
* `add_alert(label, explanation, gps, snapshot)`

### **Background Loops**

* `camera_loop()`
* `gps_loop()`
* `control_loop()`

---

## 📁 **Project Structure**

```
patrol_robot/
│── src/                    # Source code
│── models/                 # AI or trained models (optional)
│── static/                 # Web assets
│── templates/              # Dashboard HTML templates
│── patrol_robot.py         # Main program
│── README.md
│── requirements.txt
│── Demo_VDO.mp4            # Demonstration video
└── presentation_slide.pptx # Presentation
```

---

## 🧪 **Testing**

* Test camera with simple OpenCV read loop
* Test ultrasonic sensor with distance printout
* Test GPS with continuous NMEA reading
* Verify AI detection using sample images
* Check dashboard responsiveness and video stability

---

## 👤 **Authors**

**Saharat Yuanthong**
Sirindhorn International Institute of Technology (SIIT)
Contact: *your email here*

---

## 📜 **License**

This project is released under the MIT License.
You are free to modify and use it for academic or personal robotics development.


