# Custom 5" Freestyle FPV Build (Mark4 + DJI O4 Air Unit Pro)

**Type:** 5" freestyle | **FC/ESC:** SpeedyBee F405 V4 + 60A BLS 4-in-1 | **RX:** ExpressLRS 2.4G | **Video:** DJI O4 Air Unit Pro | **Props:** 5x3.3  
Demo video: _[[link](https://www.instagram.com/reel/DLZa7YPyZ9yfRRH4GAgoWavU5bKhOaAaTe52I00/?igsh=MXVkb3AwZjJoZG41NA==)]_ • Build photos: _[link to /media/photos]_ • Config diff: _[link to /config/betaflight_diff_all.txt]_


---

![fpv_image](https://github.com/user-attachments/assets/5bd8090f-1f3f-4780-9512-368025ca3670)

## 1) Overview
- **Why I built this:** short motivation (freestyle practice, durability, HD video).
- **Key specs:** AUW, battery, flight time, hover throttle, top speed (if measured).
- **What’s unique here:** printed O4 mounts to fit a Mark4 frame designed for the O3.

### 1.1 Features
- DJI O4 digital video with ND filters  
- ExpressLRS 2.4G link (low latency, long range)  
- Clean wiring, soft-mounted stack, smoke-stopper bring-up

---

## 2) Bill of Materials (BOM)
| Item | Model / Notes | Qty |
|---|---|---|
| Frame | **Mark4 5-inch** | 1 |
| Motors | **T-Motor Velox V2207 V3 1750KV** | 4 |
| FC & ESC | **SpeedyBee F405 V4** + **BLS 60A 4-in-1 ESC** | 1 |
| Receiver | **SpeedyBee Nano 2.4G ExpressLRS** | 1 |
| Video TX | **DJI O4 Air Unit Pro** | 1 |
| Goggles | **DJI Goggles N3** | 1 |
| Radio | **RadioMaster Pocket (ELRS)** | 1 |
| Props | **HQProp Ethix P3.3 (5")** | 2 CW + 2 CCW |
| Battery | **CNHL Black Series 1500mAh 22.2V 6S 100C (XT60)** | 1+ |
| Storage | **Kingston Canvas Go Plus microSD** | 1 |
| Filters | **iFlight ND filters (for O4)** | set |
| Safety | **VIFLY ShortSaver V2 (smoke stopper)** | 1 |
| Comfort | **iFlight Transmitter Neck Strap** | 1 |
| Printed Parts | **O4 → Mark4 TPU mounts, antenna bracket** (see `/print`) | — |
| Consumables | 14–16AWG silicone wire, 470–1000µF low-ESR cap, heat-shrink, Loctite, zip ties | — |

> STL files and print settings are in `/print`.

---

## 3) Printed Parts (DJI O4 on Mark4)
- **What & why:** O4 unit/mast spacing differed from O3 mounts on Mark4, so I designed TPU brackets.
- **Files:** see `/print`.
- **Print settings:** TPU 95A, 0.2–0.28 mm layer, 3–4 perimeters, 20–30% infill, no support if oriented as shown.
- **Install notes:** route O4 antennas clear of props; avoid sharp bends; add zip-tie strain relief.

---

## 4) Wiring & Assembly
### 4.1 Wiring Diagram
See `docs/wiring-diagram.png` (O4 → FC, ESC → FC, ELRS → UART).

### 4.2 UART Map
Documented in `docs/uart-map.md`:
- **UARTx:** ExpressLRS (CRSF)
- **UARTy:** DJI O4 MSP/OSD
- **LED/Beeper:** [if used]
- **Blackbox:** onboard flash or SD [if available on this FC]

### 4.3 Assembly Steps
1. Frame prep: sand edges, add arm guards, install gummies.  
2. Stack: ESC on bottom, FC on top, capacitor across main leads.  
3. Motors: tin leads, route cleanly, confirm phases reach ESC pads.  
4. Receiver: ELRS to 5V/GND/TX/RX (inverted **off**), bind button accessible.  
5. O4 unit: mount TPU parts, connect power/ground/UART, manage antenna coax.  
6. Final checks: continuity, smoke-stop with props **off**, motor direction, failsafe.

---

## 5) Firmware & Configuration
- **Flight Controller:** Betaflight `4.x` (target for SpeedyBee F405 V4).  
- **Receiver:** ExpressLRS 2.4G (bind phrase or manual bind).  
- **DJI O4 & Goggles:** pair, set recording options, bitrate, OSD/Canvas Mode if used.

### 5.1 Betaflight Basics
- Ports: enable **CRSF** on RX UART, **MSP** on O4 UART.  
- Receiver: set **Serial-based receiver (CRSF)**.  
- Modes: Arm, Angle/Horizon (optional), Beeper, Turtle (optional).  
- Motor idle: ~5–6% for freestyle.  
- `diff all`: `/config/betaflight_diff_all.txt`.

### 5.2 ExpressLRS
- Packet rate, RF power, Dynamic Power (notes in `/config/elrs-binding-notes.md`).  
- Channel map to match radio.

### 5.3 O4 Video
- Recording: 4K/60 (example), RockSteady as preferred.  
- ND filter selection by lighting (see `/docs/assembly-notes.md`).

---

## 6) Tuning
### 6.1 Preset / Base Tune
- Start from Betaflight 5" Freestyle preset, enable **RPM filtering**.

### 6.2 My Final Settings
- **PIDs:** see `/tuning/pids.md`.  
- **Filters:** `/tuning/filters.md`.  
- **Rates:** `/config/rates.json` (same in sims for muscle memory).

### 6.3 Blackbox
- Log files in `/tuning/blackbox`; brief notes on vibrations/notches.

---

## 7) Simulator Practice
- **Path:** started on **SkyDrive**, moved to **Liftoff** (worth it).  
- **Goal:** stick discipline & rate matching before maiden.  
- **My sim rates:** in `/config/rates.json`.  
- **Notes:** transmitter setup & endpoint calibration.

---

## 8) Testing & Safety
- Pre-power continuity → smoke-stopper → USB setup with props off.  
- Motor test and direction swap in Betaflight.  
- Failsafe check (radio off).  
- First hover checklist + pack storage/charging notes (6S LiPo safety).

---

## 9) Troubleshooting
| Symptom | Likely Cause | Quick Fix |
|---|---|---|
| No ELRS link | wrong UART or CRSF disabled | check Ports; bind again |
| No OSD in goggles | MSP not enabled on O4 UART | enable MSP; canvas mode |
| Jello in HD | loose camera mount / soft TPU | stiffen mount; add ND; retune |
| Desync on punchouts | filters/PID or motor screws touching windings | check screws; increase filtering |
| Reboot on throttle | insufficient cap / bad joint | add 470–1000µF cap; re-solder XT60 |

---

## 10) Performance
- **AUW (6S 1500):** _xxx g_  
- **Typical flight time:** _x–x min (freestyle)_  
- **Hover throttle:** _x%_  
- **Notes:** motor temps, DVR links.

---

## 11) Future Work
- GPS + Rescue, beeper, LEDs, GoPro mount, battery pad upgrades, tune refinements.

---

## 12) Acknowledgments
- YouTube tutorials I followed: _[list creators/video titles]_  
- Community presets & docs.

---

## 13) License
Choose a license (e.g., MIT for docs/STLs). STL licensing note if different.
