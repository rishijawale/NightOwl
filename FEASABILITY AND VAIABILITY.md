
---
# Rushikesh-->
# 🎤 FEASIBILITY & VIABILITY — PRESENTATION SCRIPT

### Opening

> **“Now I would like to explain the feasibility and viability of our proposed system.”**

> **“Our approach is based on existing and commercially available technologies, so we are not trying to invent a completely new UAV platform. Instead, our innovation is in integrating these technologies into a phased, intelligent surveillance system.”**

---

## 1. Technical Feasibility

Point toward the first section:

> **“From the feasibility perspective, our system can be developed using established components such as a Pixhawk or ArduPilot-based flight stack, commercial RGB and thermal cameras, GPS, and standard AI object-detection models.”**

> **“We are also following a phased MVP approach rather than trying to build the entire system at once.”**

Then explain the four stages:

> **“In the first stage, we perform RGB, thermal and GPS-based detection.”**

> **“In the second stage, we introduce acoustic sensing and sensor fusion.”**

> **“The third stage adds threat scoring and patrol integration.”**

> **“And finally, we integrate the dashboard and UAV response, along with tethered UAVs for selected high-risk zones.”**

### Transition

> **“This phased approach makes the core system achievable within the scope of our prototype.”**

---

# 2. Explain the 30 → 22 → 11 → 2.2 Calculation

Point to the graphic.

> **“The next question is endurance and coverage.”**

> **“For an illustrative mission, we consider approximately 30 minutes of nominal flight time.”**

> **“We reserve around 8 minutes for safety and return-to-home, leaving approximately 22 minutes of usable patrol time.”**

> **“At an illustrative cruising speed of 30 kilometres per hour, this gives approximately 11 kilometres of patrol path.”**

> **“If we assume an illustrative effective surveillance width of 200 metres, this corresponds to approximately 2.2 square kilometres of nominal surveillance corridor per sortie.”**

Then **very importantly**:

> **“However, this is only a planning estimate and should not be interpreted as guaranteed human-detection coverage. Actual coverage depends on factors such as altitude, camera field of view, vegetation, weather, target size and detection performance.”**

This last sentence is important because it prevents the judge from attacking your calculation.

---

# 3. Move to Risks

> **“However, a real forest environment introduces several challenges, so we have specifically designed the system around these risks.”**

Now go through each one.

---

## 🌳 Risk 1 — Dense Vegetation

Point to **Occlusion**.

> **“The first challenge is occlusion. Dense vegetation can completely conceal a person, and thermal imaging cannot simply see through trees.”**

> **“Therefore, we don't claim through-vegetation detection. Instead, we use multi-angle observation, sensor fusion and repeated observations to increase the probability of detection.”**

---

## 🧍 Risk 2 — Human vs Animal

Point to **Misclassification**.

> **“The second challenge is distinguishing a human from an animal, because both can produce thermal signatures.”**

> **“We address this using RGB and thermal information, movement patterns and multi-frame analysis, while also maintaining an Unknown class when the evidence is insufficient.”**

---

## 🔫 Risk 3 — False Acoustic Alarms

Point to **False alarms**.

> **“The third challenge is false acoustic alarms. An acoustic event should not automatically be treated as a poaching incident.”**

> **“Therefore, acoustic detection acts as an alert trigger, which can then be confirmed using thermal and RGB observations.”**

---

## 📡 Risk 4 — Connectivity

Point to **Connectivity**.

> **“Another challenge is connectivity because remote forest areas may not have reliable network coverage.”**

> **“Our approach is to perform critical processing locally on the UAV and store GPS-tagged events locally, so the information can be forwarded when connectivity becomes available.”**

---

## 🔋 Risk 5 — Endurance

Point to **Endurance**.

> **“The final major challenge is limited UAV endurance.”**

> **“We address this through forward or mobile drone bases, battery swapping, multiple UAVs and tethered UAVs for selected high-risk areas.”**

Then explain the architecture:

> **“So rather than expecting one drone to continuously cover an entire sanctuary, we divide the area into sectors and use the appropriate type of UAV for each requirement.”**

# ---
# PRIYA----->
# 4. Bring in Viability

Your current slide doesn't explicitly have a large "viability" section, so **this is where you should add your verbal explanation**.

Say:

> **“Coming to viability, our system is designed as an early-warning layer for the Forest Department rather than a replacement for forest personnel.”**

> **“The objective is to help limited personnel focus their attention on the most important events by providing them with a location, evidence and threat priority.”**

Then:

> **“This also makes the system scalable. We can start with one UAV as a pilot, expand to multiple sectors, introduce forward bases, and eventually build a range-level surveillance network.”**

---

# 5. Environmental Viability

Because this is a wildlife project, mention the noise issue even though it isn't prominent on the current slide:

> **“There is also an environmental consideration: UAV noise can disturb wildlife and can interfere with acoustic monitoring.”**

> **“Therefore, we aim to minimize unnecessary hovering, optimize the propulsion system for lower noise, use controlled flight zones, and use ground acoustic sensors where persistent acoustic monitoring is required.”**

This is a strong point because you're showing that you've considered a **problem caused by your own solution**.

---

# 6. Final conclusion

Finish strongly:

> **“So overall, the core MVP is technically feasible because it is built from established hardware and AI technologies.”**

> **“Its viability comes from the fact that we are not depending on a single drone or a single sensor. We combine sensor fusion, risk-based deployment, battery infrastructure and human verification to create a scalable early-warning system.”**

Then your final line:

> **“Our goal is not to replace the forest guard; it is to give the forest guard earlier information, better evidence and faster response capability.”**

**Stop there.**

---

# 🧠 Short version to memorize

If you don't want to memorize the entire script, remember this sequence:

### **FEASIBILITY**

> Existing technology → Phased MVP → Endurance calculation

### **RISKS**

> Occlusion → Misclassification → False alarms → Connectivity → Endurance

### **MITIGATION**

> Sensor fusion → Unknown + verification → Acoustic confirmation → Local processing → Battery swap + tethered UAV

### **VIABILITY**

> Forest Department → Risk-based deployment → Human verification → Scalable network

### **CLOSE**

> **“Buildable today, scalable tomorrow, and designed around real-world constraints.”**

---

## 🎯 Questions the judge may immediately ask after this slide

Practice these **without looking at your notes**:

**Q: “Can thermal cameras see through trees?”**

> “No. We don't claim that; we address partial occlusion through multi-angle observation and sensor fusion.”

**Q: “How much area can one drone cover?”**

> “Our 2.2 km² figure is only an illustrative nominal corridor calculation; actual detection coverage depends on the UAV, sensor FOV, altitude, vegetation and detection requirements.”

**Q: “What happens when the battery dies?”**

> “We maintain a safety reserve, use battery swapping and forward bases, and use multiple UAVs and tethered UAVs for persistent coverage.”

**Q: “What if the AI mistakes an animal for a human?”**

> “We use RGB, thermal and movement information, an Unknown class and human verification before high-priority action.”

**Q: “What makes this viable if drones are expensive?”**

> “We use risk-based deployment, so expensive UAV and thermal resources are concentrated in high-risk sectors rather than deployed everywhere.”

**Q: “What about drone noise?”**

> “We minimize unnecessary flight and hovering, optimize propulsion for lower noise, and can separate persistent acoustic monitoring from the UAV using ground acoustic sensor