# Tech Stack

### 1. Drone / Hardware

|Component|Technology|Purpose|
|---|---|---|
|Flight controller|**Pixhawk-class**|Flight stabilization & autonomous navigation|
|Autopilot|**ArduPilot / PX4**|Waypoints, RTL, missions|
|Motors|Brushless BLDC|Propulsion|
|Battery|LiPo|Flight power|
|GPS|GNSS/GPS|Position & navigation|
|IMU|Accelerometer + Gyroscope|Orientation|
|Barometer|Pressure sensor|Altitude|
|Obstacle sensing|LiDAR / depth camera|Tree/obstacle avoidance|
|RGB camera|HD camera|Daytime observation|
|Thermal|LWIR thermal camera|Night/heat detection|
|Companion computer|**Jetson Orin Nano / Raspberry Pi-class**|AI processing|
|Communication|4G/5G + telemetry radio where available|Data/alerts|

---

# 🧠 2. AI / Computer Vision

### Object Detection

**YOLO** would be a good starting point.

```
Thermal/RGB frame
       ↓
YOLO
       ↓
Human / Deer / Elephant / Boar / Unknown
```

For your prototype, train/fine-tune using **thermal + visible-light datasets** relevant to the wildlife you're targeting.

### Tracking

Use something like:

**YOLO + ByteTrack/DeepSORT**

This prevents the system from treating the same person as a new detection in every frame.

---

# 🔥 3. Thermal Processing

Possible stack:

**Thermal camera → OpenCV → YOLO → tracking**

The system can extract:

- Heat signature
- Bounding box
- Confidence
- Movement
- Location

Don't try to identify someone from their face at long range.

---

# 🎙️ 4. Acoustic Detection

For gunshot-like events:

**Microphone array → audio preprocessing → ML classifier**

Possible technologies:

- Python
- NumPy
- SciPy
- Librosa
- PyTorch
- CNN/audio classifier

Workflow:

```
Audio
 ↓
Noise filtering
 ↓
Spectrogram
 ↓
AI classifier
 ↓
Gunshot-like / Other sound
 ↓
Confidence
```

For multiple microphones:

```
Mic A ─┐
Mic B ─┼→ Time difference → Approximate source direction
Mic C ─┘
```

---

# 🧩 5. Sensor Fusion

This is one of the **most important parts of your project**.

Don't make independent systems that generate unrelated alerts.

Instead:

```
           Thermal
              │
RGB ──────────┼────────── Acoustic
              │
              ▼
        SENSOR FUSION
              │
              ▼
        THREAT ENGINE
              │
              ▼
        LOW / MEDIUM / HIGH
```

Example:

**Thermal:** Human 87%

**Acoustic:** Gunshot-like event 91%

**Location:** Restricted zone

**Time:** 02:13 AM

→ **HIGH THREAT**

---

# 🗺️ 6. GIS / Mapping

For the forest map:

### Frontend

**React + Leaflet**

or

**React + Mapbox GL JS**

### GIS data

- GeoJSON
- Forest boundaries
- Patrol zones
- Drone bases
- Outposts
- Roads
- Restricted zones

Your dashboard could look like:

```
┌──────────────────────────────────────┐
│       WILDLIFE SURVEILLANCE          │
├──────────────────────────────────────┤
│                                      │
│     🛩️ Drone A                       │
│          ↓                           │
│      🔴 Suspicious                   │
│          ↓                           │
│   📍 23.xxxx, 70.xxxx                │
│                                      │
│  🟢 Patrol Zone   🔴 High Risk       │
│                                      │
├──────────────────────────────────────┤
│ Threat: HIGH                         │
│ Human confidence: 92%                │
│ Acoustic event: DETECTED             │
└──────────────────────────────────────┘
```

---

# ☁️ 7. Backend

Since you're already comfortable with Python, I'd use:

### **FastAPI**

```
Drone
 ↓
FastAPI
 ↓
AI Detection Service
 ↓
Database
 ↓
Dashboard
```

Technologies:

- **Python**
- FastAPI
- Pydantic
- WebSockets
- REST API

WebSockets are useful for **live drone positions and alerts**.

---

# 🗄️ 8. Database

### PostgreSQL + PostGIS

This is particularly good because you're dealing with **geographical information**.

Store:

- Drone locations
- Detection coordinates
- Patrol routes
- Forest zones
- Outposts
- Alerts
- Authorized patrols
- Historical incidents

Example:

```
detections
-----------
id
drone_id
latitude
longitude
timestamp
object_type
confidence
thermal_image
rgb_image
threat_level
```

---

# 📱 9. Alert System

When threat level becomes HIGH:

```
AI
 ↓
FastAPI
 ↓
Alert Service
 ├── Dashboard
 ├── SMS
 ├── Email
 └── Mobile notification
```

For a prototype, **Telegram/WhatsApp-style notification simulation or email** can demonstrate the concept.

---

# 🔋 10. Battery / Fleet Management

The backend should also know:

```
Drone A
Battery: 82%
Status: PATROLLING

Drone B
Battery: 19%
Status: RETURNING

Drone C
Battery: 100%
Status: AVAILABLE
```

When Drone A reaches its safety threshold:

```
Battery low
     ↓
Return-to-home
     ↓
Land at base
     ↓
Battery swap/charge
     ↓
Available again
```

For future deployment:

**Solar-powered forward station + battery swapping dock.**

---

# 🛰️ 11. Complete Workflow

This is the workflow I'd present to your judges:

```
                    FOREST
                       │
                       ▼
                🛩️ AUTONOMOUS DRONE
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Thermal        RGB        Acoustic
       Camera        Camera       Sensor
          │            │            │
          └────────────┼────────────┘
                       ▼
                 EDGE AI PROCESSING
                       │
                       ▼
              HUMAN / ANIMAL / UNKNOWN
                       │
                       ▼
                 OBJECT TRACKING
                       │
                       ▼
                 SENSOR FUSION
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
      Patrol/Authorization    Gunshot Event
          Verification              │
             │                      │
             └──────────┬───────────┘
                        ▼
                  THREAT ENGINE
                        │
                ┌───────┼───────┐
                ▼       ▼       ▼
              LOW     MEDIUM    HIGH
                                │
                                ▼
                         GPS-TAGGED ALERT
                                │
                                ▼
                       FOREST CONTROL ROOM
                                │
                                ▼
                         FIELD RESPONSE
```

---

# 🧑‍💻 Software Architecture

I'd divide your software into **5 services**:

```
┌─────────────────────────────────────────┐
│              DRONE LAYER                │
│       PX4/ArduPilot + Sensors           │
└───────────────────┬─────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│             EDGE AI LAYER               │
│ YOLO + OpenCV + Tracking + Audio ML     │
└───────────────────┬─────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│            FUSION ENGINE                │
│ Threat Score + Authorization + Rules    │
└───────────────────┬─────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│             BACKEND                     │
│ FastAPI + WebSockets + PostgreSQL       │
│              + PostGIS                  │
└───────────────────┬─────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│             DASHBOARD                   │
│ React + Leaflet/Mapbox                  │
└─────────────────────────────────────────┘
```