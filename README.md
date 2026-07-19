# anu-xyz
Voice-controlled human-following assistive cart using HuskyLens and DFRobot voice module.
# Voice-Controlled Human-Following Assistive Cart

## Overview

This project is a **Voice-Controlled Human-Following Assistive Cart for Elderly or Hospital Use**.  
The robot acts like a small smart cart/trolley that follows a specific person using HuskyLens AI vision, responds to voice commands with the DFRobot offline voice recognition module, and helps carry items or alert family/caregivers.

## Real-Life Problem

- Elderly people, patients, or people with limited mobility find it hard to carry groceries, school bags, or medical items while walking.
- Traditional carts need to be pushed; there is a risk of falls, fatigue, and difficulty navigating.
- This project proposes a hands-free assistant cart that can follow the user and respond to simple spoken commands, improving convenience and safety in homes, hospitals, and shopping environments.

## Core Functions

### 1. Human-Following using HuskyLens (Vision AI)

- HuskyLens is mounted on the chassis facing forward.
- The sensor is trained to recognize the main user’s face or a specific color marker on their back (for example, a colored card).
- HuskyLens outputs (x-position and bounding-box size) are used to drive the motors so that the cart stays behind the person at a safe distance.
- Real-life effect: The cart walks behind the person, carrying weight and reducing physical strain.

### 2. Voice-Controlled Behavior

Using the **DFRobot Gravity Offline Voice Recognition Module (DF2301Q series)**:

- Supports 100+ built-in commands and up to 17 custom commands, all offline.
- Connected via I2C or UART to an Arduino Uno or ESP32.
- Example voice commands:
  - `Follow me` → enable HuskyLens following mode.
  - `Stop` → halt the motors and stay in place.
  - `Come here` → move towards the user if they are within camera range.
  - `Emergency` → trigger a buzzer and send a signal to the ESP32 IoT module to notify a caregiver (future extension).
- This makes the cart hands-free and friendly for elderly or visually impaired users.

### 3. Safe Motion and Alerts

- Uses DC motors and a chassis in a differential-drive configuration.
- Basic safety features:
  - Buzzer or beeper to warn if an obstacle is detected or if the user is lost.
  - Optional ultrasonic sensor for obstacle detection and collision avoidance.
- Real-life effect: Safer movement in a home, hospital corridor, or shopping aisle.

### 4. Controller Choice: Arduino Uno + ESP32

- **Arduino Uno** is used for low-level control:
  - Reading HuskyLens data (object/face tracking).
  - Motor driver control and cart movement.
  - Integration with the voice recognition module.
- **ESP32** is used for wireless and IoT features (optional, Phase 2):
  - Sending notifications to a phone or web dashboard when the user speaks “Emergency” or when the cart loses track of the user.
  - Logging usage data for future health or activity analysis.
- In documentation, ESP32 is highlighted as a platform for IoT connectivity and future expansion, even if the initial prototype runs fully offline.

## Hardware Used

- HuskyLens AI vision sensor.
- DFRobot Gravity Offline Voice Recognition Module (DF2301Q series).
- DC motors and motor driver (e.g., L298N) with mobile chassis.
- Arduino Uno for motion and sensor integration.
- ESP32 board for IoT/notification features.
- Power supply units (battery + regulators).
- Centrado / breakout boards, jumper wires, buzzer, optional ultrasonic sensor.
- Optional display (LCD/OLED) for mode, status, and command feedback.

## Repository Layout

- `hardware/` – Diagrams and connection details for HuskyLens, voice module, motors, and power.
- `firmware/` – Arduino and ESP32 code for cart control and IoT features.
- `docs/` – Extended documentation (problem statement, use cases, future work).
- `images/` – Photos and schematic diagrams (to be added as the build progresses).

## Future Work

- Add obstacle detection and path planning to avoid furniture and people.
- Add a display to show mode, battery status, and recognized voice commands.
- Integrate ESP32 with a cloud service or mobile app for remote monitoring of elderly users.
- Extend voice commands to simple math or educational Q&A for children, turning the cart into a mobile learning assistant.
