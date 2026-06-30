# 🚗 Smart Automatic Car Washing System using Siemens PLC

> A sequential industrial automation project developed using **Siemens TIA Portal V17**, **S7-1500 PLC (CPU 1511-1 PN)** and **PLCSIM** implementing a fully automatic car washing system based on a finite state machine architecture.

---

## Project Overview

This project simulates the working of a fully automatic commercial car washing station.

Once the vehicle reaches the correct washing position and payment is successfully verified, the PLC automatically performs the complete washing cycle without any human intervention.

The entire sequence is controlled using Ladder Logic, memory bits, timers and sequential state transitions.

The system executes every washing stage in a fixed order while ensuring that **only one process is active at any instant**, closely resembling industrial automation practices.

---

# Industrial Working Principle

The operator does **not** manually control each washing stage.

Instead,

1. Customer parks the vehicle.
2. Position sensor confirms correct vehicle placement.
3. Payment server authorizes transaction.
4. PLC automatically starts washing sequence.
5. Each stage finishes after its timer expires.
6. PLC switches to the next state.
7. After completion, the machine automatically returns to Idle state.

---

# Project Objectives

- Design an industrial sequential automation system.
- Learn Siemens Ladder Logic programming.
- Implement State Machine architecture.
- Practice Timer based sequencing.
- Understand Memory Bit based process control.
- Simulate complete industrial workflow using PLCSIM.

---

# Software Used

- Siemens TIA Portal V17
- Siemens PLCSIM
- Siemens S7-1500 CPU 1511-1 PN
- Ladder Logic (LAD)

---

# System Architecture

```
                 Vehicle Arrives
                        │
                        ▼
          Car Position Sensor Activated
                        │
                        ▼
          Payment Authorization Received
                        │
                        ▼
                 Water Spray (10 s)
                        │
                        ▼
            Soap + Brush (30 s)
                        │
                        ▼
               Clean Water Rinse
                    (20 s)
                        │
                        ▼
                Air Dryer (20 s)
                        │
                        ▼
               Completion Buzzer
                    (3 s)
                        │
                        ▼
                 Return to Idle
```

---

# Input Devices

| Address | Tag | Description |
|---------|-----|-------------|
| I0.0 | Car_Position_Sensor | Detects correct vehicle position |
| I0.1 | Payment_Authorized | Payment confirmation from server |
| I0.2 | Emergency_Stop | Immediately stops the entire system |

---

# Output Devices

| Address | Tag | Description |
|---------|-----|-------------|
| Q0.0 | Water_Pump | Water spray pump |
| Q0.1 | Soap_Pump | Soap spraying pump |
| Q0.2 | Brush_Motor | Soft brush motor |
| Q0.3 | Rinse_Pump | Clean water rinse |
| Q0.4 | Air_Dryer | High speed blower |
| Q0.5 | Completion_Buzzer | Wash completion indication |

---

# Internal Memory Bits

| Address | Description |
|---------|-------------|
| M0.0 | Water State |
| M0.1 | Soap & Brush State |
| M0.2 | Rinse State |
| M0.3 | Dry State |
| M0.4 | Completion State |

---

# Timers Used

| Timer | Function | Preset |
|-------|----------|---------|
| Water Timer | Water Spray | 10 s |
| Soap Timer | Soap + Brush | 30 s |
| Rinse Timer | Water Rinse | 20 s |
| Dry Timer | Air Dryer | 20 s |
| Buzzer Timer | Completion Delay | 3 s |

---

# State Machine Logic

Idle

↓

Water Spray

↓

Soap + Brush

↓

Rinse

↓

Air Dry

↓

Completion

↓

Idle

Only one state remains active at any time.

Each timer completion resets the current state and sets the next state.

This architecture simplifies debugging, maintenance and future scalability.

---

# Safety Features

✅ Emergency Stop immediately resets every active state.

✅ Prevents simultaneous activation of multiple washing stages.

✅ Washing cycle starts only after

- Vehicle Position Confirmed
- Payment Authorized

---

# Engineering Design Decisions

During development the following industrial practices were adopted:

- One network = One responsibility
- One state controls one output group
- Timer driven state transitions
- Set / Reset memory bit architecture
- Sequential execution
- Modular ladder logic
- Easy maintenance and debugging
- Industrial style commenting for every network

---

# PLC Program Structure

Network 1
Start washing cycle

↓

Network 2
Control Water Pump

↓

Network 3
Water Timer

↓

Network 4
Transition to Soap

↓

Network 5
Soap Pump & Brush

↓

Network 6
Soap Timer

↓

Network 7
Transition to Rinse

↓

Network 8
Rinse Pump

↓

Network 9
Rinse Timer

↓

Network 10
Transition to Dryer

↓

Network 11
Air Dryer

↓

Network 12
Dry Timer

↓

Network 13
Transition to Completion

↓

Network 14
Completion Buzzer

↓

Network 15
Completion Timer

↓

Network 16
Return to Idle

↓

Network 17
Emergency Stop Reset Logic

---

# Simulation

Simulation was performed using Siemens PLCSIM.

Verified scenarios:

- Correct vehicle detection
- Payment validation
- Complete automatic washing cycle
- Sequential output activation
- Timer transitions
- Emergency Stop behaviour
- Automatic return to Idle

---

# Screenshots

## PLC Tags

`Images/tags.png`

---

## Watch Table

`Images/watch_table.png`

---

## Ladder Logic

`Images/logic_ladder_01.png`

`Images/logic_ladder_02.png`

`Images/logic_ladder_03.png`

`Images/logic_ladder_04.png`

---

# Future Improvements

- HMI Interface
- Vehicle Length Detection
- Analog Water Level Sensor
- Water Tank Monitoring
- Fault Diagnostics
- PROFINET Communication
- Data Logging
- SCADA Integration

---

# Learning Outcomes

This project helped me understand:

- Siemens PLC Programming
- Ladder Logic
- PLC Tag Management
- Memory Bits
- TON Timers
- State Machine Programming
- Sequential Automation
- Industrial Debugging
- PLCSIM Testing
- Industrial Documentation

---

# Author

**Prashant Gupta**

B.Tech Mechanical Engineering

Jamia Millia Islamia

Automation | PLC | Industrial Control Systems | Robotics
