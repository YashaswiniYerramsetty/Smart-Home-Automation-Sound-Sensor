# Smart Home Automation Using Sound Sensor

This project demonstrates a simple home automation system that turns an LED ON or OFF when a clap or loud sound is detected. It uses a sound sensor connected to an Arduino board. This project is beginner-friendly and shows basic knowledge of sensors, Arduino coding, and circuit building.

## Components Used
- Arduino Uno
- Sound Sensor Module
- LED
- 220-ohm resistor
- Jumper wires
- Breadboard

------------------------------------------------------------

## Circuit Connections

Sound Sensor → Arduino  
- VCC → 5V  
- GND → GND  
- OUT → Digital Pin 2  

LED → Arduino  
- LED positive (long leg) → Pin 13 (through 220-ohm resistor)  
- LED negative → GND  

------------------------------------------------------------

## How It Works
1. The sound sensor detects loud noise.
2. The sensor output becomes HIGH.
3. Arduino reads this signal.
4. Arduino toggles (switches) the LED ON or OFF.
5. Each clap or sound will toggle the LED.

------------------------------------------------------------

## Arduino Code

```cpp
int sensorPin = 2;
int ledPin = 13;
int sensorState = 0;
bool ledState = false;

void setup() {
  pinMode(sensorPin, INPUT);
  pinMode(ledPin, OUTPUT);
  digitalWrite(ledPin, LOW);
  Serial.begin(9600);
}

void loop() {
  sensorState = digitalRead(sensorPin);

  if (sensorState == HIGH) {
    ledState = !ledState;
    digitalWrite(ledPin, ledState);
    Serial.println("Sound detected. LED toggled.");
    delay(300);
  }
}
