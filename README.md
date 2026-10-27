# 🌫️ Active Rotary Cylindrical Fog Harvester

> **Design Practicum — Group 36 | IIT Mandi (& SKUAST Kashmir)**
> Mentor: Prof. Atul Dhar

A low-cost, solar-powered, 360° rotating mesh system that harvests potable water from orographic fog for remote hill-village households in Himachal Pradesh.

---

## 📋 Table of Contents

- [Problem Statement](#-problem-statement)
- [Proposed Solution](#-proposed-solution)
- [System Architecture](#-system-architecture)
- [Key Features](#-key-features)
- [Repository Structure](#-repository-structure)
- [CAD Model](#-cad-model)
- [Design Specifications](#-design-specifications)
- [Benchmarking Summary](#-benchmarking-summary)
- [Team](#-team)
- [References](#-references)
- [License](#-license)

---

## 🧩 Problem Statement

Remote hill-village households in Himachal Pradesh face **recurring water shortages** during the pre-monsoon months (March–June). Springs dry up, groundwater becomes unreliable, and water-tanker delivery is impractical across mountain terrain. Yet these same altitudes are regularly immersed in **orographic fog** — a large, untapped atmospheric water resource.

**How can a low-cost, low-maintenance system capture atmospheric moisture from fog, treat it to potable standards, and store it reliably for daily household use?**

### Target User

The design persona is **Sunita Thakur**, a 38-year-old homemaker in a remote HP hill village, whose primary pain points include:
- Daily time burden of fetching water from distant sources
- Reliance on firewood for water purification
- Seasonal source unreliability
- Mistrust of novel water technologies without visible, consistent results

### Project Objectives

1. Convert natural fog into a reliable, meaningful daily water yield
2. Maintain effective water capture under variable, low-wind orographic fog conditions
3. Purify harvested water for household use
4. Enable easy installation and local repairability (budget ceiling ₹50,000)
5. Ensure trusted performance through daily yield visibility

---

## 💡 Proposed Solution

After evaluating **14 concepts** through weighted multi-criteria decision analysis, the **Active Rotary Cylindrical Fog Harvester** was selected as the top-scoring design (97/110).

| Rank | Concept | Score |
|------|---------|-------|
| 1 | **Active Rotary Cylindrical Fog Harvester** | **97.00** |
| 2 | Reinforced Passive SFC | 96.41 |
| 3 | Roof-Eave Integrated Fog Strip | 93.78 |
| 4 | Kirigami / Cactus-Geometry Starter Panel | 91.73 |
| 5 | Modular V-Shaped Collector | 89.49 |

The rotary design was chosen specifically because it addresses the two most critical objectives:
- **Objective 2** — Omnidirectional capture eliminates yield losses from shifting fog direction
- **Objective 5** — ESP32-based monitoring provides daily yield visibility, building user trust

---

## 🏗️ System Architecture

The system comprises **five subsystems**:

```
┌─────────────────────────────────────────────────────────┐
│                  ACTIVE ROTARY FOG HARVESTER            │
│                                                         │
│  ┌──────────────┐    ┌──────────────┐    ┌───────────┐  │
│  │   ROTARY     │    │  COLLECTION  │    │  STORAGE  │  │
│  │   DRUM       │───▶│   GUTTER     │───▶│   TANK    │  │
│  │  (Raschel    │    │ (Annular     │    │           │  │
│  │   Mesh)      │    │  Trough)     │    │           │  │
│  └──────┬───────┘    └──────────────┘    └───────────┘  │
│         │                                               │
│  ┌──────┴───────┐    ┌──────────────────────────────┐   │
│  │    DRIVE     │    │   MONITORING & CONTROL       │   │
│  │  MECHANISM   │    │  ┌────────┐  ┌────────────┐  │   │
│  │ (Geared DC   │    │  │ ESP32  │  │  Sensors:  │  │   │
│  │  Motor)      │    │  │  MCU   │──│ Temp, RH,  │  │   │
│  └──────┬───────┘    │  └────────┘  │ Water Lvl, │  │   │
│         │            │              │ Motor I    │  │   │
│  ┌──────┴───────┐    │              └────────────┘  │   │
│  │    POWER     │    └──────────────────────────────┘   │
│  │  SUBSYSTEM   │                                       │
│  │ (Solar PV +  │                                       │
│  │  Li Battery) │                                       │
│  └──────────────┘                                       │
└─────────────────────────────────────────────────────────┘
```

### Subsystem Details

| Subsystem | Description |
|-----------|-------------|
| **Rotary Drum Collector** | Vertical cylinder wrapped in double-layer 35% shade-coefficient Raschel polypropylene mesh. Slowly rotates about vertical axis, sweeping fog-laden air across 360° of collection surface. |
| **Collection Gutter** | Circumferential annular trough at drum base. Droplets shed by gravity + centrifugal force, drained to storage by gravity. |
| **Drive Mechanism** | Geared DC motor via solar charge controller + lithium battery. Rotation rate tuned for centrifugal droplet removal without re-entrainment. |
| **Power Subsystem** | Photovoltaic panel → charge controller → Li battery. Fully off-grid autonomous operation. |
| **Monitoring & Control** | ESP32 microcontroller reading temperature, relative humidity, trough water level, motor current. Data logged locally; Wi-Fi/BT telemetry optional. Visual yield indicator for household user. |

---

## ✨ Key Features

- **🔄 Omnidirectional (360°) fog capture** — independent of wind direction; the system's primary technical differentiator
- **💨 Centrifugal-assisted self-cleaning** — reduces re-evaporation losses and manual cleaning frequency
- **☀️ Solar-battery powered** — no grid dependency; operates in off-grid hill-village locations
- **📡 ESP32-based sensor monitoring** — daily yield tracking and remote diagnostics
- **🧵 Raschel mesh drum surface** — directly comparable to international fog-collection benchmark data
- **🔧 Modular subsystem architecture** — individual subsystem repair without full-unit replacement

---

## 📁 Repository Structure

```
DP_36_FogHarvesting/
├── README.md                       ← This file
├── .gitignore                      ← Git ignore rules
├── .gitattributes                  ← Git LFS config for large binaries
│
├── cad/                            ← CAD models (SolidWorks)
│   └── cad_final_assembly.SLDASM   ← Final assembly (SolidWorks 2024+)
│
└── docs/                           ← Reports and documentation
    └── Mid-Term_Report_G36.pdf     ← Mid-term design report (10 pages)
```

---

## 🖥️ CAD Model

**Software:** SolidWorks

**Modelling Strategy:** Bottom-up assembly — each sub-assembly modelled independently, then merged into the final assembly.

### Key Components Modelled

| Component | Material | Purpose |
|-----------|----------|---------|
| Vertical Cylindrical Drum | Stainless steel / Aluminium support rings + Raschel mesh wrap | Fog collection surface |
| Support Frame / Base | Galvanized iron (GI) structural members | Wind-load anchoring |
| Collection Trough / Piping | Sloped annular gutter | Gravity drainage to storage through filtration |

### Opening the Model

1. Install **SolidWorks 2024** or later
2. Open `cad/cad_final_assembly.SLDASM`
3. If prompted for missing parts, ensure all part files from the same directory are accessible

> **☁️ Cloud Access:** The full CAD model is also available on [Google Drive](https://drive.google.com/file/d/1eKHoZYQ22MyeX2aUzWRM1QhblzkkW54_/view?usp=drive_link).

---

## 📐 Design Specifications

| Parameter | Value |
|-----------|-------|
| Collection Geometry | Vertical rotating cylinder, 360° sweep |
| Mesh Material | Double-layer Raschel polypropylene, 35% shade coefficient |
| Drive | Geared DC motor, slow rotation |
| Power Source | Solar PV panel + Li-ion battery |
| Controller | ESP32 microcontroller |
| Sensors | Temperature, RH, water level, motor current |
| Connectivity | Wi-Fi / Bluetooth (optional) |
| Target Budget | ≤ ₹50,000 |
| Target Deployment | Single-household, off-grid hill village |

---

## 📊 Benchmarking Summary

14 existing fog/atmospheric water harvesting solutions were benchmarked. Key comparisons:

| Benchmark System | Similarity | Key Insight for This Design |
|-----------------|------------|----------------------------|
| CloudFisher Pro (Aqualonis) | 90% | 3D mesh geometry; wind-resistant to 120 km/h; 10–66 L/m²/day |
| Warka Water Tower | 90% | Community assembly model; shade canopy prevents re-evaporation |
| FogQuest SFC | 90% | Raschel mesh baseline; 2–10 L/m²/day typical yield |
| MIT-14 Hydrophobic SS Mesh | 60% | Outperforms Raschel by +3% (low wind) to +41% (4–5 m/s) |
| Janus Tri-Layer Collector (Li et al.) | 60% | Omnidirectional capture validated at 79.2 L/m²/day — directly validates the rotary concept |
| Uravu AWH (India) | 90% | Confirms commercial viability in Indian hill/tribal contexts |

### Key Improvements Incorporated

1. **Hydrophobic mesh coating** (inspired by MIT-14): +3% to +41% yield improvement across wind speeds
2. **Omnidirectional capture validation** (Li et al.): Academic proof that 360° collection works
3. **Dry-season supplementation pathway** (UT Austin SHPF): Hygroscopic film for low-fog May–June months

---

## 👥 Team

| Name | Affiliation |
|------|-------------|
| Vaibhav Chaudhary | IIT Mandi |
| Thakker Krisha | IIT Mandi |
| Aarav Bhukhmaria | IIT Mandi |
| Aamir Dhariwal | IIT Mandi |
| Manjeet Janghu | IIT Mandi |
| Anzar Ashraf | SKUAST Kashmir |
| Kartik Dalvi | IIT Mandi |

**Mentor:** Prof. Atul Dhar, IIT Mandi

---

## 📚 References

1. Aqualonis GmbH, "CloudFisher Pro: Technical Specifications and Global Installations," WasserStiftung, Munich, 2021.
2. Architecture & Vision, "Warka Water Tower: Biomimetic Atmospheric Water Harvesting for Rural Communities," Rome, 2020.
3. R. Shannon, "Standard Fog Collector Manual: Design and Field Installation Guide," FogQuest, Canada, 2018.
4. Bayside Fog Collectors, "Research-Grade Standard Fog Collector Kit Assembly and Calibration Guide," CSU Monterey Bay, 2022.
5. K. C. Garrett and H. S. Gharib, "Hydrophobic Coated Stainless-Steel Mesh for Enhanced Atmospheric Fog Capture," *ACS Appl. Mater. Interfaces*, vol. 12, no. 14, 2020.
6. Y. Li et al., "Janus Tri-Layer Fog Collector for High-Efficiency Omnidirectional Atmospheric Water Harvesting," *J. Mater. Chem. A*, vol. 9, no. 22, 2021.
7. Dar Si Hmad Association, "Aït Baamrane Community Fog Water Project: Operational Impact and Sustainability Report," Morocco, 2019.
8. Uravu Indigenous Science, "Solar-Assisted Atmospheric Water Generation Systems for Decentralized Rural Communities," Kerala, India, 2023.
9. J. Song, M. Liu, and W. Wu, "Janus Mesh with Alternating Wettability Pattern for Directional Droplet Transport and Rapid Drainage," *Nature Sustain.*, vol. 7, no. 3, 2024.
10. Atelier ND, "FogDome: Integrated Community Shelter and Fog Harvesting Structures in Highland Regions," Beirut, Lebanon, 2022.
11. T. Zhang Lab, "Super-Hygroscopic Polymer Films (SHPF) for Low-Humidity Atmospheric Water Harvesting," UT Austin, 2022.
12. Marienberg S.A., "Polypropylene Raschel Nets with 35% Shade Coefficient for Agricultural and Fog Collection Applications," Santiago, Chile, 2021.
13. M. Alazzam et al., "Dual PV Panel and Fog/Rain Water Harvester," *Energy Convers. Manag.*, vol. 301, 2024.
14. A. Dhaouadi and M. Abdelrahman, "Living Green Façade with Integrated Fog-Harvesting Mesh for Urban and Rural Microclimate Enhancement," *Build. Environ.*, vol. 250, 2024.

---

## 📄 License

This project is developed as part of the **Design Practicum** coursework at **IIT Mandi**. All rights reserved by the authors. For academic use and collaboration inquiries, please contact the team members.

---

<p align="center">
  <i>Designed with 💧 for the hill villages of Himachal Pradesh</i>
</p>