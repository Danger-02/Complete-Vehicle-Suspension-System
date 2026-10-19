# Automobile Suspension System - Modelling and Analysis

3D CAD model of a front double-wishbone suspension assembly (SolidWorks), with FEA of the **Lower A-Arm** and **Shock Absorber** in Ansys Workbench. Developed as a personal project at MNNIT Allahabad.

[![SolidWorks](https://img.shields.io/badge/SolidWorks-MODELLING-%23C71D23?style=for-the-badge&logo=dassaultsystemes&logoColor=white&labelColor=%23111111)](https://www.solidworks.com/)
[![Ansys](https://img.shields.io/badge/-ANALYSIS-%23FFB71B?style=for-the-badge&logo=ansys&logoColor=black&labelColor=%23111111&logoSize=auto)](https://www.ansys.com/)

---

## Overview

This project covers the complete workflow from CAD to FEA for a vehicle suspension system. The **Complete Vehicle Suspension System** was modelled and assembled in SolidWorks. The two most heavily loaded parts, the **Lower A-Arm (Control arm)** and the **Shock Absorber Assembly**, were then taken into Ansys to check stress, deformation, factor of safety, and fatigue life under peak off-road loads. Modal analysis was also performed on the A-Arm.

## Project Details

- **Project Type:** Personal Project, 7th Semester B.Tech Mechanical Engineering
- **Institute:** Motilal Nehru National Institute of Technology Allahabad, Prayagraj
- **Duration:** August 2026 - September 2026
- **Tools:** SolidWorks 2025, Ansys Workbench 2022 R1 (Static Structural, Modal, Fatigue Tool)
- **Full Report:** [`Report/Suspension_System_Project_Report.pdf`](Report/Suspension_System_Project_Report.pdf)

---

## CAD Model (SolidWorks)

<div align="center">
  <img src="Renders/preview.PNG" alt="Complete Automobile System Assembly" width="75%">
  <p><i>Complete Automobile System Assembly.</i></p>
</div>

<div align="center">
  <img src="Renders/preview2.PNG" alt="Lower A-Arm Part" width="60%">
  <p><i>Lower A-Arm (Control Arm).</i></p>
</div>

<div align="center">
  <img src="Renders/preview3.PNG" alt="Shock Absorber Assembly" width="60%">
  <p><i>Shock Absorber Assembly.</i></p>
</div>

---

## Materials Assigned

| Component | Material | Density (kg/m³) | Young's Modulus (GPa) | Poisson's Ratio | Yield Strength (MPa) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| A-Arm Model| Aluminium Alloy 6061-T6 | 2713 | 69.036 | 0.33 | 259.2 |
| Helical spring | ASTM A228 Music Wire | 7850 | 203 | 0.30 | 1590 |
| Piston rod, structural shafts | Low Alloy Steel 4140 (Hardened and Tempered) | 7850 | 205 | 0.29 | 655 |
| Locking rings, collars | Carbon Steel 1095 (Hardened and Tempered) | 7850 | 200 | 0.29 | 525 |

<div align="center">
  <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/01. A-Arm Model/02. Material Selection.png" width="70%">
  <p><i>Material Assignment on A-Arm.</i></p>
</div>

---

## FEA Setup

| Parameter | Shock Absorber | Lower A-Arm |
| :--- | :--- | :--- |
| **Analyses** | Static Structural, Fatigue | Static Structural, Fatigue, Modal |
| **Mesh** | Quadratic tetrahedral | Quadratic tetrahedral |
| **Fixed Support** | Bottom mounting eye (fixed) + cylindrical support (0 mm radial) on piston rod | Both chassis mounting hinge holes |
| **Load** | 3,000 N remote compressive force | 10,000 N remote force |
| **Load Basis** | 4x dynamic multiplier on static corner weight, worst-case bump or jump landing | 4g - 5g impact with extra factor for combined braking and steering |

<div align="center">
  <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/02. Static Structural and Fatigue Analysis/01. Forces and Supports.png" width="70%">
  <p><i>Boundary conditions on the Lower A-Arm.</i></p>
</div>

<div align="center">
  <img src="Analysis_Results/a_arm_supports_and_load.png" alt="Shock absorber boundary conditions" width="70%">
  <p><i>Boundary conditions on the Shock Absorber.</i></p>
</div>

---

## Results

### (A) Lower A-Arm - Static Structural & Fatigue Analysis

<table align="center">
  <tr>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/01. A-Arm Model/02. Material Selection.png" width="100%">
      <p><i>A-Arm Material Selection.</i></p>
    </td>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/01. A-Arm Model/03. Meshing.png" width="100%">
      <p><i>A-Arm Meshing.</i></p>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/02. Static Structural and Fatigue Analysis/02. Equivalent Stress.png" width="100%">
      <p><i>Equivalent stress on the Lower A-Arm (45.386 MPa max).</i></p>
    </td>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/02. Static Structural and Fatigue Analysis/03. Total Deformation.png" width="100%">
      <p><i>Total deformation on the Lower A-Arm (0.022823 mm max).</i></p>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/02. Static Structural and Fatigue Analysis/04. Factor of Safety.png" width="100%">
      <p><i>Static factor of safety on the Lower A-Arm (5.711 min).</i></p>
    </td>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/02. Static Structural and Fatigue Analysis/07. Fatigue Safety Factor.png" width="100%">
      <p><i>Fatigue factor of safety on the Lower A-Arm (2.3223 min).</i></p>
    </td>
  </tr>
</table>

<div align="center">

| Parameter | Value | Parameter | Value |
| :--- | :---: | :--- | :---: |
| **Max Equivalent Stress** | 45.386 MPa | **Minimum Static FoS** | 5.711 |
| **Fatigue Life** | $1 \times 10^8$ cycles | **Minimum Fatigue FoS** | 2.3223 |

</div>
---

### (B) Lower A-Arm - Modal Analysis

<table align="center">
  <tr>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/03. Modal Analysis/Total Deformation 01.png" width="100%">
      <p><i>Mode Shape 1</i></p>
    </td>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/03. Modal Analysis/Total Deformation 02.png" width="100%">
      <p><i>Mode Shape 2</i></p>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/03. Modal Analysis/Total Deformation 03.png" width="100%">
      <p><i>Mode Shape 3</i></p>
    </td>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/03. Modal Analysis/Total Deformation 04.png" width="100%">
      <p><i>Mode Shape 4</i></p>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/03. Modal Analysis/Total Deformation 05.png" width="100%">
      <p><i>Mode Shape 5</i></p>
    </td>
    <td align="center" width="50%">
      <img src="Ansys_Files/A-Arm Analysis/Ansys_Report/Results/03. Modal Analysis/Total Deformation 06.png" width="100%">
      <p><i>Mode Shape 6</i></p>
    </td>
  </tr>
</table>

| Mode | Frequency (Hz) |
| :---: | :---: |
| 1 | 1,425.4 |
| 2 | 1,650.2 |
| 3 | 1,878.7 |
| 4 | 2,043.8 |
| 5 | 2,945.1 |
| 6 | 3,420.5 |
| 7 | 3,563.9 |

> *Note: All natural frequencies are far above typical off-road excitation frequencies, so resonance is not a concern. Deformation values shown on mode shape plots are normalized and do not represent real physical displacement.*

---

### (C) Shock Absorber - Static Structural & Fatigue Analysis

| Result | Value |
| :--- | :---: |
| **Max Equivalent (von Mises) Stress** | 67.155 MPa |
| **Max Total Deformation** | 7.0508 mm |
| **Minimum Static Factor of Safety** | 3.8597 |
| **Minimum Fatigue Factor of Safety** | 1.921 |

---

## Conclusions

- All peak stresses stay well below the yield strengths of the assigned materials, ensuring both components remain elastic under peak design loads.
- Static safety factors are **5.711** (A-Arm) and **3.8597** (Shock Absorber).
- Fatigue lives reach $10^7 - 10^8$ cycles with fatigue safety factors comfortably above 1.9.
- The A-Arm's lowest natural frequency (**1,425.4 Hz**) is far above normal off-road input frequencies, preventing resonance failures.

---

## Bill of Materials (BOM)

| ITEM NO. | COMPONENT NAME | FILE TYPE | QTY. |
| :---: | :--- | :--- | :---: |
| 1 | Lower A-Arm | `.SLDPRT` | 1 |
| 2 | Upper A-Arm | `.SLDPRT` | 1 |
| 3 | Shock Absorber | `.SLDASM` | 1 |
|   | Coil Spring | `.SLDPRT` | 1 |
|   | Piston Rod | `.SLDPRT` | 1 |
|   | Damper Body | `.SLDPRT` | 1 |
| 4 | Assembly Fasteners & Hardware | Standard | As Req. |

---

## Repository Structure

```text
Automobile-Suspension-System_Design-and-Analysis/
├── BOM/                        # Bill of Materials (.xlsx and .pdf)
├── CAD_Files/                  # Full assembly (.SLDASM) and all .SLDPRT files
├── A-Arm_Analysis/
│   ├── CAD/                    # A-Arm .SLDPRT and .STEP
│   ├── Ansys_Project/          # Ansys Workbench project (.wbpj)
│   └── Ansys_Report/           # Exported Ansys reports
├── Shock_Absorber_Analysis/
│   ├── CAD/                    # Shock Absorber .
