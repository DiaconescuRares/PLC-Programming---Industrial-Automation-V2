# 🏭 Industrial Bottling Plant Simulation (PLC)

A comprehensive simulation of an automated bottling line, developed in **Structured Text (ST)** according to **IEC 61131-3** standards.

This project demonstrates advanced PLC programming concepts including State Machines, Shift Registers, and Safety Logic.

### 🎥 Watch the Full Demo

[![YouTube Demo](https://img.youtube.com/vi/M52Y_MFmcZU/maxresdefault.jpg)](https://www.youtube.com/watch?v=M52Y_MFmcZU)
*> Click the image above to watch the full explanation on YouTube.*

---

### ⚡ Quick Preview
![Simulation GIF](https://i.imgur.com/xh608S3.gif)

---

## 🚀 Project Overview

The system controls a conveyor belt that processes bottles through multiple stations: **Filling, Capping, Inspection, and Sorting**. It features a robust **Finite State Machine (FSM)** to handle operations, safety protocols, and a smooth production flow.

The logic tracks each bottle's position and properties (Type: Water/Juice, Status: Defective/OK) using bitwise shift registers, simulating a real industrial tracking system.

### Key Features
* **Dynamic Speed Control:** Real-time adjustment of conveyor belt speed via HMI.
* **Multi-Product Handling:** Logic for processing two types of liquids (Water & Juice) with different filling times.
* **Quality Control:** Automatic detection and rejection of defective bottles (Red bottles).
* **Sorting System:** Separation of products based on type at the end of the line.
* **Safety Logic:** Priority-based **Emergency Stop (E-Stop)** and **Pause (Hold)** functionalities.
* **Graceful Shutdown:** "Cycle Stop" feature that stops generation but clears the line before shutting down motors.

## ⚙️ Technical Concepts & Architecture

This project was built to demonstrate proficiency in:

* **Finite State Machine (FSM):** Structured management of machine states (`INIT`, `READY`, `RUNNING`, `HOLD`, `STOPPING`, `ERROR`).
* **Shift Registers & Bitwise Operations:** Efficient tracking of bottle position and data (`DWORD` shifting) instead of resource-heavy arrays.
* **Pseudo-Random Number Generation (LCG):** Custom mathematical algorithm ensuring uniform distribution of bottle types/defects, independent of the PLC cycle time.
* **Modular Programming:** Encapsulation of logic within Function Blocks (`FB_Masina`).
* **IEC Timers (TON, TP) & Edge Detection:** Precise timing for filling valves and pneumatic pistons.
* **HMI Data Binding:** Dynamic visualization using color mapping (`SEL` logic) and status feedback.

## 🕹️ Controls & Logic

| Control | Function | Logic Description |
| :--- | :--- | :--- |
| **START** | Begins production. | Transitions FSM to `RUNNING`. |
| **STOP** | Soft stop. | Transitions to `STOPPING` (clears conveyor before stop). |
| **HOLD** | Pauses process. | Freezes timers and motors; resumes exactly where left off. |
| **E-STOP** | Emergency. | Cuts all power, resets output variables, requires hard reset. |
| **RESET** | System Reset. | Re-initializes counters and state after an Error. |
| **Slider** | Speed Adj. | Modifies the `PT` (Pulse Time) of the main system clock. |

## 💻 How to Run

1.  Open the project in an IEC 61131-3 compatible IDE (e.g., **CODESYS** or **TwinCAT**).
2.  Import the project files.
3.  Compile and Login to the Simulation Device.
4.  Open the **Visualization** tab.
5.  Press **START**.

---
*Created by Diaconescu Rares Theodor*
