## Name : Het Parekh
## Company : CODTECH IT SOLUTIONS
## ID : CT0806DH
## Domain : Embedded Systems
## Duration : December 2024 to January 2025
## Mentor : Muzammil Ahmed
---
### Interfacing DHT Sensor with Arduino
This project demonstrates how to interface a DHT (Temperature and Humidity) sensor with an Arduino and display the temperature and humidity readings on an LCD screen using Proteus for simulation. The project introduces concepts of sensor interfacing, data display, and simulation tools like Proteus, making it ideal for those learning embedded systems.

### Technology Used  
- *Arduino IDE*  
- *Proteus Design Suite* (for simulation and design of the circuit)

 ---

### Components Required  
- Arduino Board  
- DHT 11 Sensor
- LCD 16*2 Display  
- Connecting wires  

---

### Circuit Diagram  
The circuit consists of an Arduino UNO Microcontroller interfaced with a DHT 11 ( Temperature & Humidity ) Sensor and a LCD 16*2 Display to show Readings. Power Supply & GND Terminal has been provided to DHT 11 Sesnor and LCD Display
![WhatsApp Image 2024-12-27 at 20 01 33_8570b9b2](https://github.com/user-attachments/assets/1c0fd8d7-825d-4f13-b784-b8725cd60715)

---

### Features 

- *Arduino Uno* controls the sensor and LCD.
- *DHT11 Sensor* measures temperature and humidity. Its *Data* pin is connected to *Pin 7* on Arduino.
- *16x2 LCD* displays the sensor data. The LCD’s control and data pins are connected to Arduino pins *12, 11, 5, 4, 3, 2*.
- The setup reads temperature and humidity and displays them on the LCD screen.

---

### Code 

```cpp

#include <DHT.h>
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

#define DHT11_PIN 13
DHT dht(DHT11_PIN, DHT11);

void setup() {
  lcd.begin(16, 2);
  dht.begin();
  lcd.setCursor(0, 0);
  lcd.print("DHT11 Sensor");
  lcd.setCursor(0, 1);
  lcd.print("Initializing...");
  delay(2000);
  lcd.clear();
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  if (isnan(temperature) || isnan(humidity)) {
    lcd.setCursor(0, 0);
    lcd.print("Sensor Error");
    delay(2000);
    return;
  }

  lcd.setCursor(0, 0);
  lcd.print("Temp: ");
  lcd.print(temperature, 1);
  lcd.print(" C");

  lcd.setCursor(0, 1);
  lcd.print("Humidity: ");
  lcd.print(humidity, 1);
  lcd.print(" %");

  delay(1000);
}

---
##Simulation Video



https://github.com/user-attachments/assets/6204e1e3-cd06-46df-a900-cdb08181ae42

