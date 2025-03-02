# Automated Floor Cleaning Robot

## Introduction
This project involves designing an autonomous floor cleaning robot that uses Bluetooth control and ultrasonic navigation to efficiently clean floor surfaces. The robot features a water pump-driven cleaning mechanism, integrated with a glucose drip water delivery system, and uses sensor data to navigate obstacles and optimize its cleaning route.

## Essential Components
- Arduino Nano 
- HC-05 Bluetooth Module
- L293D Motor Driver Board
- 3 HC-SR04 Ultrasonic Sensors
- 16x2 LCD Display
- Single Channel 5V Relay Module
- 100RPM Geared Motors (pair)
- Wheels (pair)
- 12V Water Pump
- 3 4V Lithium-ion Batteries
- 3 cell battery holder
- 7805 Voltage Regulator
- Resistors (1K, 2K, 10K)
- Toggle Switch
- Breadboard
- Mop Attachment
- Vinyl Tubing
- Glucose Drip Pipe
- Small Water Bottle to act as reservoir

## Code & Working Explanation
**Initialization:**  
The code begins by initializing all hardware components. This includes setting up the ultrasonic sensors for obstacle detection, configuring the LCD for real-time status updates, and defining the motor driver and pump control pins. A welcome message is displayed on the LCD during startup.

**Mode Selection:**  
A switch toggles between two operational modes:
- **Manual Mode:**  
  In manual mode, the robot listens for serial commands via the HC-05 Bluetooth module. Commands such as 'F' (forward), 'B' (backward), 'L' (left), 'R' (right), 'S' (stop), 'P' (pump on), and 'p' (pump off) control the robot’s movement and pump activation. The LCD displays the current command for user feedback.
  
- **Automatic Mode:**  
  In automatic mode, the robot continuously reads distance values from three ultrasonic sensors (left, middle, right). These sensor readings are displayed on the LCD and sent to the serial monitor for debugging. Based on the distance thresholds, the robot automatically decides whether to move forward, reverse, or turn to avoid obstacles. For example, if an obstacle is detected in the middle, the robot may reverse and turn left or right depending on which side has more clearance.

**Motor Control:**  
The motors are controlled via the L293D motor driver. The code uses a combination of digital and analog writes to set the direction and speed of the motors. Motor speed can be adjusted using serial commands (e.g., sending '1', '2', or '3' for different speed levels).

**Pump Control:**  
A water pump is operated using a single channel 5V relay module. The pump can be activated or deactivated via serial commands, with the LCD providing immediate status updates (displaying "Pump ON" or "Pump OFF").

**Safety & Debugging:**  
To ensure stable operation, the code incorporates delays that allow for reliable sensor readings and smoother motor transitions. Serial print statements provide real-time feedback on sensor data and command execution, facilitating debugging and fine-tuning during development.

Overall, the integrated system combines sensor-based navigation with manual override capabilities, enabling robust autonomous cleaning while allowing for user control when needed.

*Inspired by The Ultimate Floor Cleaning Robot (v2.0) by Saiyam Agrawal.*  
