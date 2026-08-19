
# SLIDE 1 — PROBLEM & WHY IT MATTERS

## **WILDLIFE PROTECTION HAS A SURVEILLANCE GAP**

### The Problem

Wildlife sanctuaries and protected habitats are often too large and difficult to patrol continuously. Forest teams face:

- 🌲 Dense vegetation and occlusion
- ⛰️ Hills, ravines and difficult terrain
- 🌙 Darkness / low visibility
- 📍 Large distances between patrol locations
- 👮 Limited field personnel
- 📡 Unreliable connectivity in remote areas

These conditions create **surveillance blind spots**, allowing unauthorized human activity and potential poaching incidents to go undetected or be detected too late.

### Existing technology is fragmented

**Patrols** → Human-intensive  
**Fixed cameras** → Limited viewpoint  
**Thermal** → Cannot reliably see through dense vegetation  
**Drones** → Limited endurance  
**Acoustic detection** → Imperfect / false positives

### CORE PROBLEM

> **How can technology provide continuous, rapid early detection of unauthorized human activity and possible poaching incidents across large, difficult-to-patrol wildlife habitats?**

### Our objective

> **Build an AI-assisted early-warning layer that detects, verifies and prioritizes suspicious activity for Forest Department response—not replace forest personnel.**

### Visual

Use a **large forest map/image** on one side and show 4–5 red "surveillance blind spots."

Don't put a drone hero image here. **The problem should be the hero.**

---

# SLIDE 2 — OUR SOLUTION

# **FROM A SINGLE DRONE TO AN INTELLIGENT WILDLIFE SURVEILLANCE NETWORK**

### Proposed solution

A distributed system combining:

**MOBILE UAVs**  
→ Patrol + rapid response

**TETHERED UAVs**  
→ Persistent surveillance at selected high-risk zones

**THERMAL**  
→ Night/low-light heat-signature detection

**RGB**  
→ Visual confirmation & evidence

**ACOUSTIC**  
→ Gunshot-like event detection

**AI**  
→ Human / Animal / Unknown classification

**GPS + GIS**  
→ Location-aware monitoring

**THREAT ENGINE**  
→ Prioritizes suspicious events

---

### Put this large architecture in the center

```
                  FOREST CONTROL ROOM
                          │
             ┌────────────┴────────────┐
             │                         │
        MOBILE UAVs              TETHERED UAVs
     Patrol / Response          Persistent Zones
             │                         │
             └────────────┬────────────┘
                          ↓
                ┌──────────────────┐
                │ THERMAL + RGB    │
                │     + AUDIO      │
                └────────┬─────────┘
                         ↓
                  AI SENSOR FUSION
                         ↓
             HUMAN / ANIMAL / UNKNOWN
                         ↓
                    TRACKING
                         ↓
                  THREAT SCORE
                         ↓
              AUTHORIZATION CHECK
                         ↓
                 GPS-TAGGED ALERT
                         ↓
               FOREST PERSONNEL
```

### Key message

> **We don't depend on one sensor. We combine multiple imperfect observations into one actionable, explainable alert.**

This is the heart of the project. The research identifies the combination of thermal + RGB + acoustic + GPS + AI + sensor fusion + threat assessment + autonomous patrol + tethered surveillance as the core positioning.

---

# SLIDE 3 — INNOVATION / USP

# **WHAT MAKES THIS MORE THAN "A DRONE WITH A CAMERA"?**

This slide needs to convince the judge that there is a genuine system-level innovation.

## 1. MULTI-SENSOR FUSION

Instead of:

> **Heat detected = human**

we use:

**Thermal + RGB + Audio + Movement + Context**

→ **AI assessment**

The system can classify:

**Human | Animal | Unknown**

The `Unknown` class prevents uncertain detections from being forced into a wrong category.

---

## 2. CONTEXT-AWARE THREAT SCORING

A human detection doesn't automatically mean poaching.

### Threat increases:

**Human + Night + Restricted Zone + Unexpected Time + Suspicious Movement + Acoustic Event**

### Threat decreases:

**Authorized Patrol + Strong Animal Classification**

Output:

🟢 **GREEN — Normal**

🟡 **YELLOW — Suspicious**

🔴 **RED — High Priority**

---

## 3. MOBILE + PERSISTENT SURVEILLANCE

### Mobile UAV

**Mobility**

→ Patrol  
→ Investigate  
→ Respond

### Tethered UAV

**Persistence**

→ Selected high-risk zone  
→ Continuous surveillance

### Forward/mobile base

**Operational depth**

→ Battery swap/charging  
→ Extend patrol range

This solves a fundamental problem: **a battery-powered UAV cannot provide unlimited surveillance across a huge sanctuary.**

---

## 4. HUMAN-IN-THE-LOOP

The system does **not** say:

> "Poacher confirmed."

It says:

> **"Potential unauthorized human activity detected."**

Then provides:

- Location
- Confidence
- Thermal/RGB evidence
- Acoustic evidence
- Threat score
- Patrol authorization status

**Forest personnel make the final operational decision.**

---

### Bottom USP statement

> **“Turning fragmented sensor observations into explainable, prioritized early-warning intelligence.”**

---

# SLIDE 4 — TECHNICAL ARCHITECTURE & INTELLIGENCE

# **HOW THE SYSTEM THINKS**

This slide should show the **technical depth**.

---

## A. EDGE / UAV LAYER

### Sensors

**RGB Camera**  
Daytime visual confirmation

**Thermal Camera**  
Exposed heat signatures / night surveillance

**Acoustic Sensor**  
Gunshot-like acoustic events

**GNSS + IMU + Barometer**  
Position + orientation + altitude

**Obstacle Sensor / LiDAR**  
Navigation and obstacle avoidance

The proposed prototype architecture includes a Pixhawk-class flight controller, ArduPilot/PX4 and a Raspberry Pi/Jetson-class companion computer.

---

## B. AI LAYER

```
RGB ──────────┐
              │
Thermal ──────┼──→ SENSOR FUSION
              │
Audio ────────┘
                    ↓
              OBJECT DETECTION
                    ↓
           HUMAN / ANIMAL / UNKNOWN
                    ↓
             MULTI-FRAME TRACKING
                    ↓
             BEHAVIOR / MOVEMENT
                    ↓
              THREAT ASSESSMENT
```

### AI features

- Body shape
- Size
- Height/width ratio
- Posture
- Movement pattern
- Speed
- Direction
- Thermal + RGB evidence
- Multiple consecutive frames

---

## C. CONTEXT LAYER

AI output is combined with:

**GPS location**

**Time**

**Restricted zone**

**Patrol schedule**

**Acoustic events**

↓

### THREAT SCORE

---

## D. RESPONSE LAYER

```
THREAT DETECTED
       ↓
GPS-TAGGED EVENT
       ↓
CONTROL ROOM
       ↓
FOREST PERSONNEL
       ↓
VERIFICATION
       ↓
APPROPRIATE RESPONSE
```

---

### Important technical limitation

Put a small box at the bottom:

> ⚠️ **Thermal cameras cannot reliably see through dense vegetation. Complete concealment remains a detection limitation. The system uses multi-angle observation, repeated observations and sensor fusion to improve detection rather than claiming “vision through trees.”**

This is an important credibility point.

---

# SLIDE 5 — FEASIBILITY, MVP & DEPLOYMENT

# **DESIGNED TO WORK BEYOND THE DEMO**

This slide answers:

> **Can you actually build and deploy this?**

---

## MVP — WHAT WE WILL ACTUALLY BUILD

### Phase 1 — Physical prototype

🚁 Small multirotor

📷 RGB camera

🌡️ Thermal camera

📍 GPS

🤖 Human/Animal/Unknown AI

🎯 Multi-frame tracking

🗺️ GPS-tagged dashboard

### Phase 2 — Intelligence

🎙️ Acoustic event detection

🔗 Sensor fusion

🧠 Threat scoring

📋 Patrol authorization

### Phase 3 — Network simulation

🚁 Multiple UAVs

🔋 Forward/mobile battery stations

🔌 Tethered UAV

🏢 Central control room

The research explicitly recommends building the core intelligence while **simulating sanctuary-scale infrastructure** rather than attempting to physically build everything.

---

## BATTERY / DEEP-FOREST SOLUTION

```
             MAIN BASE
                 ↓
       FORWARD / MOBILE BASE
                 ↓
        BATTERY SWAP / CHARGE
                 ↓
            MOBILE UAV
                 ↓
          PATROL SECTOR
```

For persistent zones:

```
SOLAR / GRID
     ↓
GROUND POWER STATION
     ↓
TETHERED UAV
     ↓
HIGH-RISK ZONE
```

A practical multirotor concept in our research targets roughly **25–35 minutes per sortie**, depending on aircraft and payload.

---

## CONNECTIVITY

### If network is available:

**Detection → Edge AI → Alert → Control Room**

### If network is unavailable:

**Detection → Local processing → Store event → GPS/time/evidence → Transmit when available**

The research identifies onboard/local processing and store-and-forward alerts as possible approaches.

---

## SCALABILITY

### Prototype

**1 UAV**

↓

### Pilot sector

**2–4 UAVs**

↓

### Range

**Multiple sectors + forward bases**

↓

### Large deployment

**Central control room + distributed UAV network**

Don't say:

> ❌ "One drone covers the entire sanctuary."

Our research explicitly rejects that assumption.

---

# SLIDE 6 — IMPACT, VALIDATION & FUTURE

# **FROM DETECTION TO FASTER RESPONSE**

This is where we finish the story.

---

## EXPECTED IMPACT

### Current challenge

**Large area**

↓

**Limited continuous surveillance**

↓

**Detection delay**

↓

**Manual verification**

↓

**Delayed response**

---

### With our system

**Continuous/periodic aerial observation**

↓

**AI-assisted detection**

↓

**Multi-sensor verification**

↓

**Threat prioritization**

↓

**GPS-tagged alert**

↓

**Faster human response**

---

# MEASURABLE KPIs

Don't write vague things like "save more animals."

Measure the system using:

### Detection

- Human detection precision/recall
- Animal classification accuracy
- Unknown classification rate

### Alerting

- Detection → alert latency
- False-positive rate
- Threat-score precision

### UAV

- Patrol time
- Battery turnaround
- Sector coverage
- Response time

### Operations

- Alert → verification time
- Number of actionable alerts
- Patrol efficiency

---

# DEMONSTRATION

### Our SIH demo scenario

```
Unauthorized person
        ↓
Restricted zone
        ↓
Nighttime detection
        ↓
Thermal + RGB
        ↓
AI: HUMAN
        ↓
Acoustic event
        ↓
Authorization check: NOT EXPECTED
        ↓
🔴 HIGH THREAT
        ↓
GPS ALERT
        ↓
FOREST CONTROL ROOM
```

This gives the judges something concrete to see rather than just listening to claims.

---

# LIMITATIONS — AND HOW WE HANDLE THEM

|Limitation|Mitigation|
|---|---|
|Dense vegetation|Multi-angle + sensor fusion|
|Complete concealment|Acknowledge detection limitation|
|False gunshot detection|Acoustic + visual/thermal confirmation|
|Battery|Forward bases + battery swap|
|Connectivity|Edge processing + store-and-forward|
|False positives|Unknown class + threat scoring|
|Wildlife disturbance|Controlled operating zones|
|AI error|Human verification|

---

# FUTURE ROADMAP

### NOW — SIH MVP

**1 UAV + RGB + Thermal + AI + Dashboard**

↓

### NEXT

**Acoustic network + sensor fusion**

↓

### PILOT

**Multi-UAV + forward stations**

↓

### DEPLOYMENT

**Tethered persistent zones + centralized control room**

---

# FINAL LINE

Put this in **large text** at the bottom:

> ### **“We don't replace the forest guard. We give the forest guard earlier information, better evidence and faster response capability.”**

---

# The 6-slide story

The judges should mentally walk away with exactly this:

### **SLIDE 1**

> There is a real surveillance problem.

### **SLIDE 2**

> We have designed a complete system to address it.

### **SLIDE 3**

> It is more than just a drone—it has genuine system-level innovation.

### **SLIDE 4**

> We understand the technical details and limitations.

### **SLIDE 5**

> We know how to actually build and deploy it.

### **SLIDE 6**

> We can measure its impact and scale it.

---

## One critical thing

**Don't put all this text literally onto the slides.**

This is the **content master**. The actual PPT should visually compress it into:

- ~30–50 words of primary text per slide
- Diagrams
- Icons
- Architecture
- 1–2 key numbers
- Screenshots/prototype evidence
- Very short labels

The detailed explanations above become your **speaker notes / pitch preparation**.

And there are still some numbers we should **not invent yet**—especially final cost, thermal detection range, communication range, AI accuracy, and actual coverage. Those need hardware selection/testing first. Our research itself warns that coverage depends on the real drone, sensor FOV, vegetation, weather, target size and detection requirements.