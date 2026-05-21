# 🤖 Automated Wall Painting Machine
### Final Year Engineering Project | B.E. Mechanical Engineering
**Don Bosco College of Engineering, Goa University | 2022–23**  
**Team of 5 | Guide: Prof. Sachin Turi | Grade: O (Outstanding)**

---

## 📌 Problem Statement

| | Manual Painting | MYRO Commercial Robot | Our Machine |
|---|---|---|---|
| Cost | ₹3,000 labour/1,500 sq.ft | ₹15,00,000+ | **₹27,857** |
| Max height | Human reach (~2m) | 1.83m | **3.0m** |
| Portability | N/A | ❌ No | **✅ Yes** |
| Chemical exposure | High (VOCs) | Low | **Low** |

Manual wall painting exposes workers to toxic VOCs (benzene, toluene) and is limited by human reach. Commercial robots are unaffordable for typical use. This project builds a low-cost, portable, automated alternative.

---

## 🎥 System Overview

> *<img width="802" height="826" alt="17793391355977349903158325774500" src="https://github.com/user-attachments/assets/cf4d7e35-b8b8-4314-bfd1-da6655405e08" />
*

The machine covers **3 metres height × 2 metres width** — standard Indian room dimensions. It operates autonomously once placed on the track, detecting and avoiding obstacles such as windows and switchboards.

---

## ⚙️ System Architecture
┌─────────────────────────────────────────┐
│              BASE ASSEMBLY              │
│  PMDC Motor (350W) + Arduino Uno        │
│  Geared Box Motor + 2m Lateral Track    │
└────────────────┬────────────────────────┘
│
┌────────────────▼────────────────────────┐
│         FRAME ASSEMBLY (x2)             │
│  Telescopic mild steel frames           │
│  Rope-pulley vertical drive             │
│  Reaches ~3m height                     │
└────────────────┬────────────────────────┘
│
┌────────────────▼────────────────────────┐
│       PAINT DISPENSING SYSTEM           │
│  HVLP Spray Gun + 3D-printed bracket   │
│  100N Linear Actuator (trigger)         │
│  HC-SR04 Ultrasonic Sensors (x2)        │
└─────────────────────────────────────────┘

---

## 🔄 Control Logic (Arduino State Machine)
STARTUP → Reset to zero position (home)
│
└── LOOP:
├── 1. Activate spray gun (linear actuator ON)
├── 2. Move paint system UPWARD (PMDC motor)
├── 3. Ultrasonic sensor check:
│       obstacle detected? → pause spray, continue movement
│       no obstacle?       → spray active
├── 4. Top limit switch triggered → deactivate spray
├── 5. Move DOWNWARD to home position
├── 6. Lateral shift: 75mm sideways (geared box motor)
└── 7. Repeat until full wall covered
---

## 🔧 Key Design Iterations

| Subsystem | Attempt 1 | Attempt 2 | Final Solution | Reason |
|---|---|---|---|---|
| Vertical drive | Lead-screw | — | **Rope-pulley** | Lighter, simpler, lower cost |
| Lateral movement | Mecanum wheels | — | **Track system** | More reliable, no slippage |
| Spray trigger | Servo motor | Solenoid valve | **100N Linear Actuator** | Only option with sufficient force |
| Obstacle detection | Multiple sensor types | — | **Single HC-SR04** | Simplified wiring, sufficient accuracy |

---

## 🛠️ Technical Specifications

| Parameter | Value |
|---|---|
| Vertical reach | ~3.0 metres |
| Lateral coverage | 2.0 metres (2m track) |
| Lateral strip width | 75mm per pass |
| Gun-to-wall distance | 190mm |
| Operating pressure | 100 PSI |
| Motor power (vertical) | 350W PMDC |
| Trigger actuator force | 100N |
| Obstacle detection | HC-SR04 ultrasonic (range: 2cm–400cm) |
| Control unit | Arduino Uno |
| Build cost | **₹27,857** |

---

## 📐 CAD Models

> SolidWorks files available in [`/CAD-Models`](/CAD-Models)

Three iterative design models were developed in SolidWorks:
- Model 1 — Initial concept with lead-screw drive and Mecanum wheels
- Model 2 — Revised frame geometry with rope-pulley integration  
- Model 3 — Final design with track system and modular dismountable base

> *[Insert screenshots of your SolidWorks models here]*

---

## 📊 FEA Structural Validation

> ANSYS results available in [`/FEA-Results`](/FEA-Results)

Static load case analysis performed on the main frame assembly under operational forces:
- Load: weight of paint dispensing system + dynamic forces during vertical movement
- Material: Mild steel (IS 2062)
- Analysis type: Static structural
- Result: Frame passes safety factor requirement under maximum operational load

> *[Insert your ANSYS stress/deformation screenshots here]*

---

## 🧪 Testing Results

| Test parameter | Value |
|---|---|
| Test area painted | 1.5m × 0.6m board |
| Time taken | 238 seconds (~4 minutes) |
| Number of test runs | 12 |
| Predicted 2.5m × 2.5m wall time | ~17 minutes |
| Final test outcome | Dispensing bracket slipped mid-run (mounting design gap identified) |

---

## ⚠️ Limitations & Lessons Learned

- Paint dispensing bracket slipped during final validation run → clamp mechanism needs redesign
- HVLP gun requires external air compressor → portability constraint
- Currently paints vertical strips only (no horizontal or diagonal capability)
- Obstacle detection is basic threshold-based ultrasonic — no computer vision

---

## 🚀 Future Scope

- **Computer vision** — replace ultrasonic with camera + YOLO object detection for smarter surface mapping
- **Adaptive path planning** — AI-based coverage optimisation for irregular walls
- **Mobile app control** — Bluetooth/WiFi interface for remote operation
- **Multi-colour capability** — solenoid-switched colour channels
- **Improved clamping** — redesigned mounting bracket for dispensing system

---

## 📁 Repository Structure
├── /CAD-Models/       SolidWorks part and assembly files
├── /Cut-Sheets/       2D production drawings (PDF)
├── /Arduino-Code/     Control logic (.ino)
├── /Images/           Machine photos and test run images
├── /FEA-Results/      ANSYS stress analysis outputs
├── /Documentation/    Full project report (PDF)
└── /BOM/              Bill of Materials

---

## 🏷️ Topics

`arduino` `automation` `robotics` `mechatronics` `embedded-systems` 
`solidworks` `ansys-fea` `mechanical-engineering` `final-year-project` 
`cad` `control-systems` `computer-vision-future`

---

## 👤 Author

**Abdul Aziz Salman Mohammed**  
B.E. Mechanical Engineering | Goa University 
