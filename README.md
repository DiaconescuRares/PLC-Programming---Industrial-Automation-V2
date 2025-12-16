# 🏭 Industrial Bottling Plant Simulation (PLC)

A comprehensive simulation of an industrial bottling line control system, developed in **Structured Text (ST)** according to **IEC 61131-3** standards.

This project simulates a complete production cycle including bottle generation, filling (Water/Juice), capping, quality inspection, defect rejection, and sorting.

![Project Demo](path_to_your_gif_or_screenshot.gif) 
*(Replace this line with a link to your screenshot or the video/GIF you created)*

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

* **Finite State Machine (FSM):** Structured management of machine states (`INIT`, `READY`, `RUNNING`, `HOLD`, `STOPPING`, `ERROR`).
* **Bitwise Operations & Shift Registers:** Efficient tracking of bottle position and data (`DWORD` shifting) instead of resource-heavy arrays.
* **Linear Congruential Generator (LCG):** Custom mathematical algorithm to ensure true pseudo-random distribution of bottle types and defects, independent of the PLC cycle time.
* **Modular Programming:** Encapsulation of logic within Function Blocks (FB).
* **IEC Timers (TON/TP):** Precise timing for filling valves and pneumatic pistons.
* **HMI Data Binding:** Dynamic visualization using color mapping (`SEL` logic) and status feedback.

## 🕹️ Controls & Logic

| Control | Function | Logic |
| :--- | :--- | :--- |
| **START** | Begins production. | Transitions FSM to `RUNNING`. |
| **STOP** | Soft stop. | Transitions to `STOPPING` (clears conveyor before stop). |
| **HOLD** | Pauses process. | Freezes timers and motors; resumes on release. |
| **E-STOP** | Emergency. | Cuts all power, resets variables, requires hard reset. |
| **RESET** | System Reset. | Re-initializes counters and state after an Error. |
| **Slider** | Speed Adj. | Modifies the `PT` (Pulse Time) of the main clock. |

## 🛠️ Simulation Logic

The simulation uses a mathematically generated random seed to create inputs:
* **Bottle Presence:** 60% chance.
* **Type:** 50% Water / 50% Juice.
* **Defect Rate:** ~20%.

**Process Flow:**
1.  **Generation:** Bottles enter the shift register.
2.  **Filling:** * Water: 1000ms (Valve 1).
    * Juice: 2000ms (Valve 2).
3.  **Capping:** Piston activation.
4.  **Inspection:** Red bottles (Defects) are rejected.
5.  **Sorting:** Juice bottles are pushed to a secondary lane.

## 💻 How to Run

1.  Open the project in an IEC 61131-3 compatible IDE (e.g., **CODESYS**, **TwinCAT**, or **eCockpit**).
2.  Import the `.export` or project files.
3.  Compile and Login to the Simulation Device.
4.  Open the **Visualization** tab (`PLC_PRG` mapping).
5.  Press **START**.

## 📝 License

This project is open-source and available for educational purposes.
