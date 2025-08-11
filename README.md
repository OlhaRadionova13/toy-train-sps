# Programmable Toy Railway on SPS (TwinCAT 3)

## 📜 Project Description
This project implements a **programmable toy railway** on **SPS (PLC)** using **Beckhoff TwinCAT 3**.  
The system automatically switches rails based on **RFID sensor** readings and controls the **start/stop** of trains via logical conditions.  
It simulates a miniature railway system where each wagon can be detected, routed, and managed independently.

The automation logic is implemented using function blocks:

- `FB_SerialCOM` — Handles serial communication with RFID reader.
- `FB_Start` — Controls the start sequence for train movement.
- `MAIN` — Main program loop integrating all function blocks.
- `RIFD` — Processes RFID data for wagon detection and routing logic.

---

## ⚙️ Used Equipment

| Component | Model / Description | Purpose |
|-----------|--------------------|---------|
| **PLC (SPS)** | Beckhoff CX-series (e.g., CX9020) with TwinCAT 3 | Main controller |
| **RFID Reader** | Serial communication interface | Reads wagon IDs |
| **RFID Tags** | Attached to wagons | Identification of each wagon |
| **Sensors** | Digital/analog (depending on setup) | Detect train position |
| **Rail Switches (Weichen)** | Motorized switch units | Route train to correct track |
| **Train** | Toy electric train | Main moving element |
| **Power Supply** | Compatible with PLC and train | Power system |
| **PC / HMI** | TwinCAT 3 development environment | Programming and monitoring |

---

## 🔄 How It Works

1. **Wagon Detection**  
   Each wagon has an RFID tag. When it passes the RFID reader, the `FB_SerialCOM` block receives and processes the ID.

2. **Routing Decision**  
   The `RIFD` block compares the detected ID with predefined routes and decides whether to switch the rails.

3. **Rail Switching**  
   The PLC sends a control signal to the motorized rail switch to route the train to the correct track.

4. **Train Start/Stop**  
   The `FB_Start` block manages the starting or stopping of the train based on logic conditions (e.g., switch position, track occupancy).

5. **Main Program Control**  
   The `MAIN` block coordinates all operations and ensures safe sequence execution.

---

## 🗂 Project Structure

```
/src
 ├── FB_SerialCOM.TcPOU   # Serial communication handler for RFID
 ├── FB_Start.TcPOU       # Train start logic
 ├── MAIN.TcPOU           # Main control program
 ├── RIFD.TcPOU           # RFID data processing and routing
/docs
 ├── wiring_diagram.png   # Electrical connections (optional)
 ├── rfid_reader_manual.pdf
/media
 ├── demo.gif             # Demonstration of system in action
 ├── train_photo.jpg
```

---

## 🚀 Getting Started

1. Open the project in **TwinCAT 3**.
2. Map I/O variables to your hardware configuration.
3. Deploy the program to the PLC.
4. Place RFID tags on wagons and position the RFID reader along the track.
5. Start the system and observe automatic rail switching.

---

## 📜 License
This project is released under the MIT License.
