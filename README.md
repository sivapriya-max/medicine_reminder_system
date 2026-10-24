# Smart Medicine Reminder System

##  Project Overview

The **Smart Medicine Reminder System** is an Arduino-based embedded system designed to help users take their medicines on time. It uses a Real-Time Clock (RTC) module to schedule medicine reminders, an LCD to display the current time and reminder messages, and a buzzer to alert users when it is time to take their medication. An IR sensor is used to check whether the medicine has been taken, while a servo motor provides a simple mechanism for medicine dispensing or compartment control.

This project aims to improve medication adherence through automated reminders and basic medicine-taking detection.

##  Objectives

- Provide timely reminders for scheduled medication.
- Display the current time and reminder status on an LCD.
- Generate audible alerts using a buzzer.
- Use an IR sensor to detect medicine-taking activity.
- Control a servo motor based on the sensor's response.
- Develop a simple, low-cost embedded healthcare solution.

##  Components Required

| S. No. | Component | Purpose |
|---|---|---|
| 1 | Arduino board | Main controller |
| 2 | DS3231 RTC module | Maintains accurate time |
| 3 | 16×2 I2C LCD | Displays time and messages |
| 4 | IR sensor | Detects the presence of an object |
| 5 | Buzzer | Provides audio alerts |
| 6 | Servo motor | Controls the dispensing mechanism |
| 7 | Jumper wires | Circuit connections |
| 8 | Power supply | Powers the system |

##  Working Principle

1. **Time Tracking:** The DS3231 RTC module provides the current time to the Arduino.
2. **Scheduled Reminders:** The system checks three preset reminder times: 8:00 AM, 1:00 PM, and 8:00 PM.
3. **Alert Generation:** When a scheduled time is reached, the LCD displays the corresponding dose reminder and the buzzer sounds for five seconds.
4. **Medicine Detection:** After the alert, the IR sensor is monitored for approximately three seconds to check for object detection.
5. **Servo Operation:** If the sensor detects an object, the LCD displays a confirmation message and the servo motor rotates to 90° before returning to its initial position.
6. **Missed Reminder Response:** If no object is detected, the LCD displays a notification and the buzzer sounds again.

##  Technologies Used

- **Programming Language:** Embedded C/C++ (Arduino)
- **Platform:** Arduino IDE
- **Microcontroller:** Arduino-compatible board
- **Communication Protocol:** I2C for the LCD and I2C-based RTC communication
- **Embedded Concepts:** Real-time clock interfacing, sensor input processing, actuator control, and scheduled event handling

##  Libraries Required

Install the following libraries in the Arduino IDE:

- `Wire.h` – I2C communication
- `RTClib.h` – RTC module interfacing
- `LiquidCrystal_I2C.h` – I2C LCD control
- `Servo.h` – Servo motor control

##  Pin Configuration

| Component | Arduino Pin |
|---|---|
| Buzzer | Digital Pin 8 |
| IR Sensor Output | Digital Pin 7 |
| Servo Motor Signal | Digital Pin 9 |
| I2C LCD SDA/SCL | Board-specific I2C pins |
| DS3231 SDA/SCL | Board-specific I2C pins |

The LCD and RTC share the I2C communication bus.

##  Getting Started

1. Clone or download this repository.
2. Connect the components according to the pin configuration.
3. Install the required libraries in Arduino IDE.
4. Open the Arduino source file.
5. Set the required alarm times in the `alarmHours[]` and `alarmMinutes[]` arrays.
6. Upload the code to the Arduino board.
7. Ensure the RTC module is set to the correct date and time.
8. Observe the LCD messages, buzzer alerts, and servo response during the scheduled reminders.

##  Customization

The reminder times can be modified in the following arrays:

```cpp
int alarmHours[3] = {8, 13, 20};
int alarmMinutes[3] = {0, 0, 0};
```

For example, change these values to configure different reminder times. The current implementation supports three daily reminders.

##  Key Features

- Three programmable daily medicine reminders
- Real-time clock-based scheduling
- LCD-based time and status display
- Audible alerts for scheduled reminders
- IR sensor-based object detection
- Servo motor actuation
- Simple and affordable embedded system design

##  Future Enhancements

- Add more configurable medicine schedules.
- Integrate a mobile application for reminders and notifications.
- Add Wi-Fi connectivity for remote monitoring.
- Include a real medicine-compartment sensor for more reliable confirmation.
- Store medicine schedules and reminder history in memory.
- Implement a button-based interface to acknowledge or snooze reminders.

##  Limitations

The current system uses IR-based object detection as an indication of medicine-taking activity. It cannot independently confirm that a user has actually swallowed the medicine. The alarm schedule is configured directly in the source code, and the current implementation supports three daily reminder times.
