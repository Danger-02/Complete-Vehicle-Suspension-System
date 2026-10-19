# Automobile Suspension System - Modelling and Analysis

3D CAD model of a front double-wishbone suspension assembly (SolidWorks), with FEA of the **Lower A-Arm** and **Shock Absorber** in Ansys Workbench. Developed as personal project at MNNIT Allahabad.

[![SolidWorks](https://img.shields.io/badge/SolidWorks-white?style=flat&logo=dassaultsystemes&logoColor=white&logoSize=auto&labelColor=%23EE0000&color=%23EE0000&cacheSeconds=3600)](https://www.solidworks.com/)
[![Ansys](https://img.shields.io/badge/Workbench-black?style=flat&logo=ansys&logoColor=white&logoSize=auto&labelColor=black&color=black&cacheSeconds=3600)
](https://ansys.synopsys.com/en-in)
[![Github](https://img.shields.io/badge/Github-black?style=flat&logo=github&logoColor=white&logoSize=auto&labelColor=black&color=black&cacheSeconds=3600)
](https://github.com/)



---

## Overview :

This project covers the complete workflow from CAD to FEA for a vehicle suspension system. The complete vehicle suspension system was modelled and assembled in SolidWorks. The two most heavily loaded parts, the **Lower A-Arm (Control arm)** and the **Shock Absorber Assembly**, were then taken into Ansys to check stress, deformation, factor of safety and fatigue life under peak off-road loads, and the A-Arm was also checked for natural frequencies (Modal).

## Project Details :

- **Project Type:** Personal Project, 7th Semester B.Tech Mechanical Engineering
- **Institute:** Motilal Nehru National Institute of Technology Allahabad, Prayagraj
- **Duration:** August 2026 - September 2026
- **Tools:** SolidWorks 2025, Ansys Workbench 2022 R1 (Static Structural, Modal, Fatigue Tool)
- **Full Report:** `Report/Suspension_System_Project_Report.pdf`

---

## CAD Model (SolidWorks) :

<div align="center">
  <img src="Renders/preview.PNG" alt="Complete Automobile System Assembly" width="75%" height="80%"">
  <p><i>Complete Automobile System Assembly.</i></p>
</div>

<div align="center">
  <img src="Renders/preview2.PNG" alt="Lower A-Arm Part" width="75%" height="80%"">
  <p><i>Lower A-Arm (Control Arm).</i></p>
</div>

<div align="center">
  <img src="Renders/preview3.PNG" alt="Shock Absorber Assembly" width="75%">
  <p><i>Shock Absorber assembly (Assembled shock body, Shock spring adjustment nut, Suspension coil spring, Assembled shock strut).</i></p>
</div>

---

## Materials Assigned :

| Component | Material | Density (kg/m³) | Young's Modulus (GPa) | Poisson's Ratio | Yield Strength (MPa) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| Lower A-Arm, housing caps, mounting eyes | Aluminium Alloy 6061-T6 | 2700 | 69.036 | 0.33 | 259.2 |
| Helical spring | ASTM A228 Music Wire | 7850 | 203 | 0.30 | 1590 |
| Piston rod, structural shafts | Low Alloy Steel 4140 (Hardened and Tempered) | 7850 | 205 | 0.29 | 655 |
| Locking rings, collars | Carbon Steel 1095 (Hardened and Tempered) | 7850 | 200 | 0.29 | 525 |

---

## FEA Setup :

| Parameter | Shock Absorber | Lower A-Arm |
| :--- | :--- | :--- |
| Analyses | Static Structural, Fatigue | Static Structural, Fatigue, Modal |
| Mesh | Quadratic tetrahedral | Quadratic tetrahedral |
| Fixed Support | Bottom mounting eye (fixed) + cylindrical support (0 mm radial) on piston rod | Both chassis mounting hinge holes |
| Load | 3,000 N remote compressive force | 10,000 N remote force |
| Load Basis | 4x dynamic multiplier on static corner weight, worst-case bump or jump landing | 4g - 5g impact with extra factor for combined braking and steering |

<div align="center">
  <img src="Analysis_Results/shock_absorber_supports_and_load.png" alt="Shock absorber boundary conditions" width="70%">
  <p><i>Boundary conditions on the Shock Absorber.</i></p>
</div>

<div align="center">
  <img src="Analysis_Results/a_arm_supports_and_load.png" alt="A-Arm boundary conditions" width="70%">
  <p><i>Boundary conditions on the Lower A-Arm.</i></p>
</div>

---

## Results :

### Shock Absorber (3,000 N)

| Result | Value |
| :--- | :---: |
| Max Equivalent (von Mises) Stress | 67.155 MPa |
| Max Equivalent Elastic Strain | 0.1066 mm/mm |
| Max Total Deformation | 7.0508 mm |
| Minimum Static Factor of Safety | 3.8597 |
| Max Fatigue Damage Index | 0.1 |
| Fatigue Life | 1 x 10⁷ cycles (minimum) |
| Minimum Fatigue Factor of Safety | 1.9908 |

### Lower A-Arm (10,000 N)

| Result | Value |
| :--- | :---: |
| Max Equivalent (von Mises) Stress | 45.386 MPa |
| Max Total Deformation | 0.0228 mm |
| Minimum Static Factor of Safety | 5.711 |
| Fatigue Life | 1 x 10⁸ cycles (max of the scale across the entire body) |
| Minimum Fatigue Factor of Safety | 2.3223 |

### Lower A-Arm - Modal Analysis

| Mode | Frequency (Hz) |
| :---: | :---: |
| 1 | 1,425.4 |
| 2 | [check from Ansys] |
| 3 | 1,878.7 |
| 4 | 2,043.8 |
| 5 | 2,945.1 |
| 6 | 3,420.5 |
| 7 | 3,563.9 |

All natural frequencies are far above typical off-road excitation frequencies, so resonance is not a concern. Deformation values shown on mode shape plots are relative (normalised) and do not represent real displacement.

<div align="center">
  <img src="Analysis_Results/shock_absorber_von_mises_stress.png" alt="Shock absorber von Mises stress" width="75%">
  <p><i>Equivalent stress on the Shock Absorber (67.155 MPa max).</i></p>
</div>

<div align="center">
  <img src="Analysis_Results/shock_absorber_total_deformation.png" alt="Shock absorber total deformation" width="75%">
  <p><i>Total deformation on the Shock Absorber (7.0508 mm max).</i></p>
</div>

<div align="center">
  <img src="Analysis_Results/a_arm_von_mises_stress.png" alt="A-Arm von Mises stress" width="75%">
  <p><i>Equivalent stress on the Lower A-Arm (45.386 MPa max, near the inner hinge and neck).</i></p>
</div>

<div align="center">
  <img src="Analysis_Results/a_arm_factor_of_safety.png" alt="A-Arm factor of safety" width="75%">
  <p><i>Static factor of safety on the Lower A-Arm (5.711 min).</i></p>
</div>

<div align="center">
  <img src="Analysis_Results/a_arm_modal_mode_1.png" alt="A-Arm modal shape 1" width="75%">
  <p><i>Lower A-Arm Modal Shape 1 (1,425.4 Hz).</i></p>
</div>

## Conclusions :

- All peak stresses stay well below the yield strengths of the assigned materials, so both components remain elastic under the design loads.
- Static safety factors are 5.711 (A-Arm) and 3.8597 (Shock Absorber).
- Fatigue lives reach 10⁷ - 10⁸ cycles with fatigue safety factors above 1.9.
- The A-Arm's lowest natural frequency (1,425.4 Hz) is far above normal off-road input frequencies.

---

## Bill of Materials (BOM) :

<!-- Paste your full assembly BOM here (export from SolidWorks as .xlsx and also upload it in the BOM/ folder) -->

| ITEM NO. | COMPONENT NAME | FILE TYPE | QTY. |
| :---: | :--- | :--- | :---: |
| 1 | Lower A-Arm | `.SLDPRT` | [ ] |
| 2 | Upper A-Arm | `.SLDPRT` | [ ] |
| 3 | Shock Absorber | `.SLDASM` | [ ] |
|  |    Coil Spring | `.SLDPRT` | [ ] |
|  |    Piston Rod | `.SLDPRT` | [ ] |
|  |    Damper Body | `.SLDPRT` | [ ] |
| 4 | [Add remaining parts: hub, wheel, fasteners...] | `.SLDPRT` | [ ] |

---

## Repository Structure :

```
Automobile-Suspension-System_Design-and-Analysis/
├── BOM/                          # Bill of Materials (.xlsx and .pdf)
├── CAD_Files/                    # Full assembly (.SLDASM) and all .SLDPRT files
├── A-Arm_Analysis/
│   ├── CAD/                      # A-Arm .SLDPRT and .STEP
│   ├── Ansys_Project/            # Ansys Workbench project (.wbpj)
│   └── Ansys_Report/             # Exported Ansys reports
├── Shock_Absorber_Analysis/
│   ├── CAD/                      # Shock Absorber .SLDPRT and .STEP
│   ├── Ansys_Project/            # Ansys Workbench project (.wbpj)
│   └── Ansys_Report/             # Exported Ansys reports
├── Analysis_Results/             # Stress, deformation, FoS, fatigue, modal images
├── Renders/                      # Assembly and component render images
├── Report/                       # Full project report (PDF)
└── README.md                     # Project documentation page
```

## How To Open :

1. Download or clone the repository.
2. Open the `.SLDASM` / `.SLDPRT` files from `CAD_Files/` in SolidWorks 2025 or later.
3. No SolidWorks? Use the `.STEP` files in `A-Arm_Analysis/CAD/` and `Shock_Absorber_Analysis/CAD/` with any CAD software.
4. To re-run the FEA, open the `.wbpj` in Ansys Workbench 2022 R1 or later.

## Credits :

Developed by **Chaitanya Gajbhiye** (Reg. No. 20236048), B.Tech Mechanical Engineering, MNNIT Allahabad. The baseline assembly layout followed standard automotive architecture and SolidWorks tutorial guidance; the A-Arm and Shock Absorber were scaled to real-world dimensions and analysed independently. Methodology references: Shigley's Mechanical Engineering Design and the Ansys Mechanical User's Guide.

## License :

Shared for educational and portfolio purposes.
