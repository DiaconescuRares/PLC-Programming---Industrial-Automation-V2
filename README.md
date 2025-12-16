# 🏭 Industrial Bottling Plant Simulation (PLC)

A comprehensive simulation of an industrial bottling line control system, developed in **Structured Text (ST)** according to **IEC 61131-3** standards.

![Project Demo](https://imgur.com/a/4xIkvfX.gif)

### 📺 [Watch the Full Presentation on YouTube](https://youtu.be/M52Y_MFmcZU)

---

## 🚀 Overview

The system controls a conveyor belt that processes bottles through multiple stations. It features a robust **Finite State Machine (FSM)** to handle operations, safety protocols, and a smooth production flow. The logic tracks each bottle's position and properties (Type, Defect status) using bitwise shift registers.

### Key Features
* **Dynamic Speed Control:** Real-time adjustment of conveyor belt speed.
* **Multi-Product Handling:** Logic for processing two types of liquids (Water & Juice) with different filling times.
* **Quality Control:** Automatic detection and rejection of defective bottles.
* **Sorting System:** Separation of products based on type at the end of the line.
* **Safety Logic:** Priority-based Emergency Stop (E-Stop) and Pause (Hold) functionalities.
* **Graceful Shutdown:** "Cycle Stop" feature that stops generation but clears the line before shutting down motors.

## ⚙️ Technical Concepts & Architecture

This project implements advanced PLC programming concepts:

* **Finite State Machine (FSM)** – Structured management of states (`INIT`, `READY`, `RUNNING`, `HOLD`, `STOPPING`, `ERROR`).
* **Shift Registers & Bitwise Operations** – Efficient tracking of bottle position and data (`DWORD` shifting).
* **Pseudo-Random Number Generation (LCG)** – Custom mathematical algorithm ensuring uniform distribution independent of cycle time.
* **Modular Programming** – Encapsulation logic within Function Blocks (`FB_Masina`).
* **IEC Timers (TON, TP) & Edge Detection** – Precise timing for actuators.
* **Safety Interlocks & Priority Logic** – Handling critical safety signals.
* **HMI Data Binding & Dynamic Coloring** – Visual feedback using `SEL` logic and HEX color codes.

## 🕹️ Controls & Logic

| Control | Function | Logic |
| :--- | :--- | :--- |
| **START** | Begins production. | Transitions FSM to `RUNNING`. |
| **STOP** | Soft stop. | Transitions to `STOPPING` (clears conveyor before stop). |
| **HOLD** | Pauses process. | Freezes timers and motors; resumes on release. |
| **E-STOP** | Emergency. | Cuts all power, resets variables, requires hard reset. |
| **RESET** | System Reset. | Re-initializes counters and state after an Error. |
| **Slider** | Speed Adj. | Modifies the `PT` (Pulse Time) of the main clock. |

## 💻 How to Run

1.  Open the project in an IEC 61131-3 compatible IDE (e.g., **CODESYS** or **TwinCAT**).
2.  Import the project files.
3.  Compile and Login to the Simulation Device.
4.  Open the **Visualization** tab.
5.  Press **START**.

---
*Created with Structured Text (ST).*
