For SIH, I would make the MVP **much smaller** than the full system. The goal is to prove the **core innovation**, not build an entire autonomous forest-security network.

# 🛩️ MVP — AI Wildlife Anti-Poaching Drone

### 🎯 MVP Objective

> **Detect and locate a human in a forest environment at night, distinguish the detection from common wildlife, and immediately send a GPS-based alert to the Forest Department dashboard.**

---

## 1. Hardware

### Drone

- Small quadcopter
- Pixhawk-class flight controller
- GPS
- LiPo battery
- Brushless motors

### Sensors

**Minimum:**

🌡️ **Thermal camera**  
📷 **RGB camera**  
📍 **GPS**

For the MVP, **skip LiDAR and acoustic hardware initially**.

---

# 2. AI

### Human vs Animal

Use:

**YOLO + OpenCV**

Classes:

```
Human
Deer
Wild Boar
Elephant
Unknown
```

Pipeline:

```
Thermal/RGB
     ↓
YOLO
     ↓
Object detected
     ↓
Human / Animal / Unknown
     ↓
Confidence score
```

Example:

> Human — 91%

---

# 3. Tracking

Add **ByteTrack** or another lightweight tracker.

Why?

If the camera sees:

```
Frame 1 → Human
Frame 2 → Human
Frame 3 → Human
```

the system understands it's **one continuously tracked object**, rather than three separate detections.

---

# 4. GPS

Every detection gets:

```
Object: HUMAN
Confidence: 91%
Latitude: XX.XXXX
Longitude: XX.XXXX
Time: 02:14:32
Drone: D-01
```

This is one of the most important MVP features.

---

# 5. Threat Logic

Keep it simple.

```
IF human detected
AND confidence > threshold
AND location is inside restricted zone
AND person is not in authorized patrol list
THEN
    HIGH PRIORITY ALERT
```

For the MVP, **don't attempt sophisticated behavioral prediction**.

---

# 6. Backend

### FastAPI

Receives:

```
POST /detections
```

Example payload:

```
{
  "drone_id": "D01",
  "object": "human",
  "confidence": 0.91,
  "latitude": 23.1234,
  "longitude": 70.5678,
  "threat": "HIGH"
}
```

---

# 7. Database

### PostgreSQL

Store:

- Drone
- Detection
- Location
- Timestamp
- Classification
- Confidence
- Threat level

For the MVP, **PostGIS is optional**. Add it if you're comfortable with it.

---

# 8. Dashboard

### React + Leaflet

Show:

```
┌─────────────────────────────────────┐
│ WILDLIFE SECURITY                   │
├─────────────────────────────────────┤
│                                     │
│          🛩️ Drone                   │
│             ↓                       │
│          🔴 HUMAN                   │
│             ↓                       │
│        📍 Detection                 │
│                                     │
│   ┌─────────────────────────────┐   │
│   │ Threat: HIGH                │   │
│   │ Human: 91%                  │   │
│   │ Time: 02:14                 │   │
│   │ Location: XX.XXXX, XX.XXXX  │   │
│   └─────────────────────────────┘   │
└─────────────────────────────────────┘
```

---

# 9. Alert

When HIGH threat:

**Dashboard alert + email/Telegram notification**

Example:

> 🚨 **POSSIBLE UNAUTHORIZED HUMAN DETECTED**  
> Location: 23.1234, 70.5678  
> Confidence: 91%  
> Time: 02:14 AM  
> Drone: D01

---

# 10. MVP Workflow

```
             🛩️ DRONE
                 │
          RGB + THERMAL
                 │
                 ▼
           EDGE COMPUTER
                 │
             YOLO AI
                 │
       ┌─────────┼─────────┐
       ▼         ▼         ▼
     HUMAN     ANIMAL    UNKNOWN
       │
       ▼
   TRACK OBJECT
       │
       ▼
    GPS TAG
       │
       ▼
   THREAT CHECK
       │
       ▼
   ┌───┴────┐
   │        │
 NORMAL   HIGH
            │
            ▼
       🚨 ALERT
            │
            ▼
    FOREST DASHBOARD
```



# Your MVP in one sentence

> **“A GPS-enabled drone using thermal and RGB cameras with edge AI to distinguish humans from wildlife and automatically alert the Forest Department when an unauthorized human is detected in a restricted forest zone.”**