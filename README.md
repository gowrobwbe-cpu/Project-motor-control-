\# 🤖 MYRAA — ESP32-S3 Wi-Fi Motor Control Robot



A simple Wi-Fi-controlled robot car built with an \*\*ESP32-S3 development board and an L298N motor driver\*\*. Control the robot wirelessly from a smartphone, tablet, or computer using a web browser — no dedicated mobile app required.



\## ✨ Features



\- 📶 Wi-Fi Access Point mode — works without a router or internet connection.

\- 🌐 Built-in web control dashboard.

\- ⬆️ Forward, backward, left, and right movement.

\- ⏹️ Stop button.

\- ⚡ Three speed levels: LOW, MID, and HIGH.

\- 📱 Smartphone, tablet, and computer browser support.

\- 🔧 Simple Arduino code that can be customized.



\## 🧰 Required Hardware



\- ESP32-S3 development board

\- L298N dual H-bridge motor driver

\- Two DC gear motors, or a compatible two-channel motor arrangement

\- Robot chassis and wheels

\- Suitable motor power supply

\- USB data cable

\- Smartphone or computer with Wi-Fi



\*\*Important:\*\* Use a motor power supply appropriate for your motors and driver. Do not power the motors directly from the ESP32-S3 GPIO pins.



\## 🔌 Wiring Connections



Connect the ESP32-S3 to the L298N as follows:



| ESP32-S3 GPIO | L298N connection |

|---|---|

| GPIO 4 | ENA |

| GPIO 5 | IN1 |

| GPIO 6 | IN2 |

| GPIO 7 | ENB |

| GPIO 15 | IN3 |

| GPIO 16 | IN4 |

| GND | GND |



\### Motor connections



\- Right motor → L298N OUT1 and OUT2

\- Left motor → L298N OUT3 and OUT4

\- Motor battery → L298N motor power input, according to the driver's specifications

\- ESP32-S3 GND and L298N GND → common ground



Keep the motor power wiring separate from the ESP32-S3's regulated logic supply. Use an appropriate regulated supply for the ESP32-S3.



\*\*Note:\*\* Remove the L298N ENA/ENB jumpers if required for GPIO speed control. Check your specific L298N board's jumper arrangement and power requirements before connecting the battery.



\## 💻 Software Requirements



1\. Install the \[Arduino IDE](https://www.arduino.cc/en/software).

2\. Install ESP32 board support using the \[Espressif Arduino-ESP32 guide](https://docs.espressif.com/projects/arduino-esp32/en/latest/installing.html).

3\. Select the appropriate ESP32-S3 board in Arduino IDE.

4\. Open `motor control code.txt` and copy its contents into a new Arduino sketch.

5\. Save the sketch as `MYRAA\_Motor\_Control.ino`.



The code uses the following standard ESP32 Arduino libraries:



\- `WiFi.h`

\- `WebServer.h`



These are included with the ESP32 Arduino board package.



\## 🚀 Upload and Run



1\. Connect the ESP32-S3 to your computer using a USB data cable.

2\. Open the sketch in Arduino IDE.

3\. Select your ESP32-S3 board and the correct COM port.

4\. Click \*\*Verify\*\* to compile the sketch.

5\. Click \*\*Upload\*\* to flash the firmware.

6\. Open Serial Monitor and set the baud rate to `115200`.

7\. Wait for the startup messages.



The robot creates its own Wi-Fi network.



| Setting | Value |

|---|---|

| Wi-Fi name (SSID) | `MYRAA\_ROBOT` |

| Default password | `12345678` |

| Web control address | `http://192.168.4.1` |



\## 📱 How to Control the Robot



1\. Turn on the ESP32-S3 and motor power supply.

2\. On your phone or computer, open Wi-Fi settings.

3\. Connect to `MYRAA\_ROBOT` using the password `12345678`.

4\. If your device reports that the network has no internet, choose the option to stay connected.

5\. Open a web browser.

6\. Visit \*\*http://192.168.4.1\*\*.

7\. Use the on-screen buttons to control the robot.



\### Control buttons



| Button | Action |

|---|---|

| ▲ | Move forward |

| ▼ | Move backward |

| ◀ | Turn left |

| ▶ | Turn right |

| ■ | Stop |

| LOW | Set speed to 150 |

| MID | Set speed to 200 |

| HIGH | Set speed to 255 |



The speed values use the 0–255 range. The selected speed is applied to subsequent motor movement commands.



\*\*Safety:\*\* Test with the wheels lifted off the ground first. The current code stops the motors when the movement button is released, but a Wi-Fi disconnection or browser failure is not guaranteed to trigger an immediate stop. Keep the robot on a clear surface and within reach of its power switch.



\## ⚙️ Customization



\### Change the Wi-Fi name and password



Edit these lines in the sketch:



```cpp

const char\* ssid = "MYRAA\_ROBOT";

const char\* password = "12345678";

```



Use a unique Wi-Fi password of at least eight characters.



\### Change motor GPIO pins



Update the `#define` values in the L298N pin configuration section. Make sure the selected pins are available on your particular ESP32-S3 board and do not conflict with USB, flash, PSRAM, or other hardware functions.



\### Change speed levels



Modify these variables:



```cpp

const int speedLow  = 150;

const int speedMid  = 200;

const int speedHigh = 255;

```



\## 🛠️ Troubleshooting



\*\*The Wi-Fi network does not appear\*\*

\- Check USB power and the ESP32-S3 startup messages.

\- Confirm that the firmware uploaded successfully.

\- Restart the board and check Serial Monitor.



\*\*The dashboard does not open\*\*

\- Confirm that your phone is connected to `MYRAA\_ROBOT`.

\- Open `http://192.168.4.1` rather than searching for the address.

\- Keep the phone connected to the robot's Wi-Fi network.



\*\*The motors do not move\*\*

\- Check the motor battery and common ground.

\- Check ENA/ENB jumpers and the six GPIO connections.

\- Verify motor wiring and the L298N power input.

\- Test with the wheels lifted off the ground.



\*\*The robot moves in the wrong direction\*\*

\- Check the motor output wiring.

\- Swap the two wires of the affected motor if necessary, with power disconnected.



\## 🔒 Security Notes



\- The default Wi-Fi password is intended for initial testing only.

\- Change the password before using the robot in a shared environment.

\- This example is a local control project, not an internet-accessible remote-control service.

\- Do not expose the control interface to an untrusted network without appropriate security protections.



\## 📌 Current Project Scope



This firmware provides manual Wi-Fi motor control and three speed presets. It does \*\*not\*\* currently implement autonomous navigation, obstacle detection, camera streaming, voice control, or battery telemetry.



\## 🤝 Contributions



Contributions, bug reports, wiring improvements, and feature suggestions are welcome. Test changes on your own hardware before operating the robot.



\## 📄 License



Choose a license before allowing others to reuse, modify, or redistribute this project. For example, an MIT License can be added in a separate `LICENSE` file if that is your intended licensing choice.



\---



\*\*Project:\*\* MYRAA ESP32-S3 Wi-Fi Motor Control  

\*\*Platform:\*\* Arduino-ESP32  

\*\*Interface:\*\* Web browser  

\*\*Control:\*\* Local Wi-Fi Access Point



