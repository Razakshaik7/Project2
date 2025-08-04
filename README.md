***HAND GESTURE REMOTE CONTROLLED CAR***

***OVERVIEW***

A hand gesture remote controlled car lets you steer and command an RC vehicle by moving your hand, rather than using a traditional joystick or button‐based remote. It typically uses motion sensors to read the orientation or gestures of your hand and wirelessly transmits commands to the car’s motors. This intuitive interface offers a more engaging, immersive driving experience.

***WORKING PRINCIPLE***
Hand gestures are detected by wearable sensors—most commonly a 3-axis accelerometer and gyroscope module (like the MPU6050). The module measures tilt angles (roll, pitch, yaw) of the user’s hand. These readings are sent from a transmitter (often based on an Arduino Nano) over a low-power 2.4 GHz radio link (using nRF24L01+ modules) to a receiver unit on the car. The receiver feeds angle values into a motor driver (such as the L298N), which adjusts wheel speeds and directions accordingly.

***COMPONENTS***
Transmitter (Hand Controller)

Arduino Nano microcontroller
MPU6050 accelerometer/gyroscope module
nRF24L01+ radio transceiver with adapter
LiPo battery (7–12 V)
Breadboard, jumper wires, double-sided tape

Receiver (Car Unit)
Arduino Nano microcontroller
nRF24L01+ radio transceiver with adapter
L298N dual H-bridge motor driver
4 WD chassis with four TT DC gear motors
LiPo battery (7–12 V)
Breadboard, wiring harness, mounting hardware

***SOFTWARE ARCHITECTURE***
Sensor Reading The MPU6050 provides raw acceleration and rotational velocity data over I²C. A library like I2CDev and MPU6050 processes these into tilt angles.
Wireless Transmission Tilt angle values are packaged and sent via the nRF24L01+ module from transmitter to receiver.
Command Interpretation The receiver unpacks angle data and translates it into motor speed and direction signals.
Motor Control The L298N receives PWM and direction signals from the Arduino, driving each motor channel to execute forward, reverse, or turning maneuvers.

***STEP-BY-STEP BUILD PROCESS***
Assemble the transmitter circuit on a breadboard: connect MPU6050 to Arduino, mount nRF24L01+ on adapter.
Upload transmitter code that reads MPU6050 data, formats a payload, and sends via the radio module.
Build the receiver circuit: wire nRF24L01+ to Arduino and L298N driver to the motors.
Upload receiver code that listens for packets, parses angles, and outputs proper PWM and direction signals to the driver.
Strap batteries, secure all boards, test in open space. Fine-tune mapping between hand tilt and wheel velocity for smooth control.
