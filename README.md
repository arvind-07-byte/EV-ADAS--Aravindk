Real-Time Electric Vehicle ADAS & Dashboard System

Developer: Aravind K


[🎥 Click Here to Watch the EV ADAS Video Demo](https://drive.google.com/file/d/11PGekTZaZrhi9Ks6Yccx4JKAVe4xqt6A/view?usp=drive_link)

Modern electric vehicles generate enormous volumes of real-time sensor data, and without a centralized dashboard, critical safety faults can go undetected. This project is a hardware-in-the-loop simulation of an EV Advanced Driver Assistance System (ADAS) designed to aggregate multi-dimensional sensor metrics into a centralized, priority-tiered engine

Key Features

1.Real-Time EV Dynamics Engine: The system computes vehicle speed using a physics-based inertia model, deducts battery State of Charge (SOC) based on continuous power draw, and supports ECO, NORMAL, and SPORT drive modes with torque scaling. 

2.Ultrasonic ADAS Safety: Three HC-SR04 sensors (Front, Left, Right) are sequentially polled every 100 ms to calculate Time-To-Collision (TTC) and provide Forward Collision Warnings (FCW) and Blind Spot Detection (BSD). 

3.Deterministic Fault Management: The STM32 executes a strict state machine that monitors for hardware faults, such as a motor over-temperature (>90°C) or a critically low SOC (< 2%). Upon detection, the system drops motor torque to zero in under 10 ms to ensure safety.

4-Level Alarm Priority: A tiered alarm system (None, Advisory, Warning, Critical) maps active threats to specific dashboard indicators, LED flashes, and frequency-modulated active buzzer tones.  

5. Live Python Dashboard: The STM32 streams structured ASCII telemetry frames over a high-speed UART connection (115200 bps) at 10 Hz. A host PC runs a Python Matplotlib GUI that parses these strings to dynamically animate a speedometer, SOC bar, speed history trace, and an ADAS bird-eye view at 10 fps.
6.   UART Diagnostic Shell: Mimicking an OBD-II diagnostic port, the bidirectional shell allows for live parameter injection, manual fault triggering, and deterministic testing of alarm boundaries without moving physical hardware.

7. System ArchitectureHardware / Simulation: STM32F103C8T6 (Blue Pill) microcontroller simulated in PICSimLab.
Sensor Inputs: 12-bit ADC analog potentiometers acting as variable pedals/temperature inputs, and HC-SR04 ultrasonic panels.
Firmware Environment: Developed in C using STM32 HAL in CubeIDE.
Frontend Visualization: Python 3 utilizing the matplotlib and pyserial libraries
