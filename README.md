# Smart-Dustbin-using-Arduino-Uno 

An IoT-enabled smart dustbin system designed for automated, touchless waste disposal using motion sensors. Built with Arduino Uno, this project enhances hygiene and efficiency by detecting hand movement and automatically opening/closing the lid.

## Features

- Automatic lid opening using ultrasonic motion detection
- Touchless operation for improved hygiene
- Real-time response and smooth lid control
- Power-efficient design for continuous usage
- Easy to replicate with minimal hardware

## Technologies & Components Used

- Arduino Uno
- Ultrasonic Sensor (HC-SR04)
- Servo Motor
- Jumper Wires
- Dustbin Lid (custom or existing)
- 9V Battery
- Arduino IDE (C++)

## Working Principle

1. The ultrasonic sensor detects motion (i.e., a hand approaching the bin).
2. If motion is detected within a predefined range (e.g., 10–15 cm), the servo motor rotates to lift the dustbin lid.
3. After a short delay, the lid automatically closes.
4. The process resets and waits for the next detection cycle.

## Circuit Diagram
![image](https://github.com/user-attachments/assets/fba71f89-ee43-488b-8f3d-37a72b678197)





## Code
#include <Servo.h>

Servo lidServo;
int trigPin = 9;
int echoPin = 10;
long duration;
int distance;

void setup() {
  lidServo.attach(3);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
  lidServo.write(0); // Lid closed
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  if (distance < 15) {
    lidServo.write(90); // Open lid
    delay(3000);        // Keep open for 3 seconds
    lidServo.write(0);  // Close lid
  }

  delay(100);
}

## Smart Dustbin - Model
![image](https://github.com/user-attachments/assets/b2a5e8f2-4ce1-45f2-ae6e-8e735a689695)
![image](https://github.com/user-attachments/assets/e1d7e884-c2a2-4cff-9f0f-0782360d1046)


