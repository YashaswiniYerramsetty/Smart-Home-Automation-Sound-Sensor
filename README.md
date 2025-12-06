Sound Sensor Based LED Control System

This project uses an Arduino board and an analog sound sensor to detect surrounding noise levels and operate an LED accordingly. The purpose of this experiment is to understand how analog sensor values are read through the ADC (Analog-to-Digital Converter) of a microcontroller and how threshold-based decision making can be implemented in embedded C.

Objective

The aim of this project is to design a simple circuit that can identify variations in sound intensity and activate an LED when the sound exceeds a predefined threshold value. This demonstrates basic signal sensing, analog input handling, and actuator control.

Components Used 

Arduino Uno or Arduino Nano
Analog sound sensor module LM393
Single LED 
220-ohm resistor for the LED
Breadboard for assembling the circuit
Jumper wires for connections
USB cable for uploading the code

Circuit Diagram (Text Description)

Sound Sensor AO → Arduino A0
Sound Sensor VCC → 5V
Sound Sensor GND → GND
LED Anode → D13
LED Cathode → GND through 220Ω resistor

Program

int soundPin = A0;
int ledPin = 13;
int threshold = 300;

void setup() {
    pinMode(ledPin, OUTPUT);
    Serial.begin(9600);
}

void loop() {
    int soundValue = analogRead(soundPin);
    Serial.println(soundValue);

    if (soundValue > threshold) {
        digitalWrite(ledPin, HIGH);
    } else {
        digitalWrite(ledPin, LOW);
    }

    delay(100);
}

Working Principle

The sound sensor outputs an analog voltage between 0 and 5V depending on the loudness. The Arduino converts this into a 10-bit digital value (0–1023). A threshold value is set based on the environment. When the sound intensity crosses this value, the LED turns on.

Output Observation

When sound intensity (e.g., claps, taps, voices) rises above the threshold, the LED lights up.
Serial Monitor displays the actual analog values, which helps in selecting the correct threshold.

Applications

Noise monitoring
Sound-activated switches
Basic automation
Clap-based control systems

Limitations

Highly sensitive to vibration
Not suitable for accurate sound measurement
Threshold must be manually calibrated
