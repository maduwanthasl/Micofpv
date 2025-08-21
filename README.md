# Custom 5" Freestyle FPV Build (Mark4 + DJI O4 Air Unit Pro)

**Type:** 5" freestyle • **FC/ESC:** SpeedyBee F405 V4 + 60A BLS 4-in-1 • **RX:** ExpressLRS 2.4G • **Video:** DJI O4 Air Unit Pro • **Props:** 5×3.3

**Demo video:** [Instagram Reel](https://www.instagram.com/reel/DLZa7YPyZ9yfRRH4GAgoWavU5bKhOaAaTe52I00/?igsh=MXVkb3AwZjJoZG41NA==)  
**Build photo:** [Image](https://github.com/maduwanthasl/Micofpv/blob/main/Images/fpv_image.jpg)

---

![Freestyle FPV — Mark4 + O4](https://github.com/user-attachments/assets/5bd8090f-1f3f-4780-9512-368025ca3670)

## Overview
- **Why:** I’m deeply interested in FPV drones and built this for hobby freestyle and stress relief (durability + clean HD video).  
- **Key specs (current):** ~5–6 min freestyle flights, hover ~17% throttle, weight ~680 g (AUW, 6S 1500 mAh), top speed ≈150 km/h.  
- **What’s unique:** Custom 3D-printed mounts to fit the DJI **O4** Air Unit Pro on a **Mark4** frame originally intended for O3, plus simple printed feet for landing practice.

### Features
- DJI O4 digital video with iFlight ND filters  
- ExpressLRS 2.4G link (low latency, long range)  
- Clean wiring, soft-mounted stack, smoke-stopped first power-up

---

## Bill of Materials (BOM)

| Item | Model / Notes | Qty |
| --- | --- | ---: |
| **Frame** | Mark4 5-inch | 1 |
| **Motors** | T-Motor Velox V2207 V3 1750 KV | 4 |
| **FC & ESC** | SpeedyBee F405 V4 + BLS 60A 4-in-1 ESC | 1 |
| **Receiver** | SpeedyBee Nano 2.4G **ExpressLRS** | 1 |
| **VTX / Camera** | **DJI O4 Air Unit Pro** | 1 |
| **Goggles** | DJI Goggles N3 | 1 |
| **Radio** | RadioMaster Pocket (ELRS) | 1 |
| **Propellers** | HQProp Ethix P3.3 (5″) | 2×CW + 2×CCW |
| **Battery** | CNHL Black Series 1500 mAh 22.2 V 6S 100C (XT60) | 1+ |
| **Storage** | Kingston Canvas Go Plus microSD | 1 |
| **Filters** | iFlight ND set for O4 | 1 |
| **Safety** | VIFLY ShortSaver V2 (smart smoke stopper) | 1 |
| **Comfort** | iFlight Transmitter Neck Strap | 1 |
| **Printed Parts** | O4 → Mark4 camera/air-unit mounts, antenna bracket, landing feet | — |
| **Consumables** | 14–16 AWG silicone wire, 470–1000 µF low-ESR cap, heat-shrink, zip ties, threadlocker | — |

---

## Printed Parts (DJI O4 on Mark4)
- **Why:** O4 unit/mast spacing differs from O3-based mounts on the Mark4, so I designed **PLA+** brackets. (TPU is also an option for added vibration resistance.)  
- **Files:** see `3d-printed-parts/` (camera cage, rear mount, antenna bracket, landing feet).  
- **Install notes:** route O4 antennas clear of props, avoid sharp coax bends, and add zip-tie strain relief.

---

## Wiring & Assembly

### 4.1 Wiring Diagram
See **`wiring-diagram`** (O4 → FC, ESC → FC, ELRS → UART).

![Wiring Diagram](https://github.com/maduwanthasl/Micofpv/blob/main/Images/image.png)

### 4.2 UART Map
- **UARTx:** ExpressLRS
- **UARTy:** DJI O4 OSD

### 4.3 Assembly Steps
1. **Frame prep:** lightly sand carbon edges, add arm guards, install gummies.  
2. **Stack:** **ESC on bottom, FC on top** (or as your frame allows); add low-ESR cap across main leads.  
3. **Motors:** tin leads, route cleanly, and confirm phases reach correct ESC pads.  
4. **Receiver:** wire ELRS to 5 V/GND/TX/RX (no inversion); keep bind button accessible.  
5. **O4 unit:** mount 3D-printed parts, connect power/ground/UART, and manage antenna coax carefully.  
6. **Final checks:** continuity test → smoke stopper power-up (props **off**) → motor direction test → failsafe test.

---

## Firmware & Configuration
- **Flight Controller:** Betaflight `4.5` (SpeedyBee F405 V4 target).  
- **Receiver:** ExpressLRS 2.4G (manual bind).  
- **DJI O4 & Goggles:** pair, set recording options/bitrate; enable OSD/Canvas Mode if used.

### 5.1 Betaflight Basics
- **Receiver tab:** **Serial-based receiver (CRSF)**.  
- **Modes:** Arm, Angle/Horizon (optional), Beeper (DShot).  
- **Motor idle:** ~5–6% (freestyle starting point).

### 5.2 ExpressLRS
- Match **channel map** to the radio; confirm endpoints and RSSI/Link Quality.

### 5.3 O4 Video
- Typical recording: **4K/60** (RockSteady optional).  
- Choose **ND filter** based on lighting to reduce jello and maintain shutter speed.

---

## Simulator Practice
- **Path:** started on **SkyDrive**, then moved to **Liftoff** (worth buying after basics).  
- **Goal:** stick discipline and rate matching **before** maiden.  
- **Notes:** transmitter setup and endpoint calibration to match Betaflight.

---

## Testing & Safety
- Pre-power continuity → **smoke-stopper** → USB setup with props off.  
- Motor test + direction swap in Betaflight.  
- Failsafe check (radio off).  
- First hover checklist; LiPo storage/charging safety (6S).

---

## Performance (current)
- **Typical flight time:** 5–6 min (freestyle)  
- **Hover throttle:** ~17%  
- **Weight:** ~680 g (AUW with 6S 1500 mAh)

---

## Future Work
- GPS + Rescue, beeper, LEDs, GoPro mount, better battery pad, further tune refinements.

---

## Acknowledgments
Tutorials and references I followed:
- [Rogue FPV Build Series](https://www.youtube.com/watch?v=zWR0B7xqwMg&list=PLgRKeXqwf6Q2vFpVJjNjZdjeIQmNUhvDn&ab_channel=RogueFPV)  
- [Joshua Bardwell — 5″ Build Guide](https://www.youtube.com/watch?v=Zytp-J14evo&list=PLgRKeXqwf6Q2vFpVJjNjZdjeIQmNUhvDn&index=2&ab_channel=JoshuaBardwell)  
- [ELRS Setup](https://youtu.be/XB6b0HrDGeA?si=0KDyoqJ684y_nBzz)  
- [Betaflight Beginner Setup](https://youtu.be/zj90LK8XR68?si=Ff384E5LzpYpau6v)  
- [ESC & Motor Direction](https://youtu.be/-jT_25XurcM?si=VqhFGBFgVTrHDFWf)  
- [DJI O4 Tips](https://youtu.be/xZ465T5B0Ls?si=CluL7JrLkbhmzXJg)  
- [General Troubleshooting](https://youtu.be/mhkMIsVJD4c?si=JrtRLWs-BKeLUrqn)

Community presets & docs were also super helpful—thanks!

---

