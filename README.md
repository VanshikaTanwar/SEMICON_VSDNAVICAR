# VSDNAVICAR
***The NaviCar, Powered by the VSDSquadron Mini***
***“Avoid the Unseen ,the future of mobility”***

TEAM VSD SAFE VISIONARIES


# Table of the Content
- [Introduction to the VSDSquadron Mini](#Introduction-to-the-VSDSquadron-Mini)
- [Key Features of the VSDSquadron Mini](#Key-Features-of-the-VSDSquadron-Mini)
- [Introduction to the VSDNAVICAR](#Introduction-to-the-VSDNAVICAR)
- [Table of Connections of the circuit](#Table-of-Connections-of-the-circuit)
- [Source code of Arduino IDE with comments](#Source-code-of-Arduino-IDE-with-comments)
- [Image of the VSDNAVICAR](#Image-of-the-VSDNAVICAR)
- [Demonstration Video of the VSDNAVICAR](#Demonstration-Video-of-the-VSDNAVICAR)
- [Conclusion](#Conclusion)
- [Acknowledgement](#Acknowledgement)
- [Author](#Author)
# Introduction to the VSDSquadron Mini 
The VSDSquadron Mini, a versatile powerhouse within the RISC-V landscape that elevates Your development to new heights. Whether you’re a newcomer delving into the realm of embedded systems or an experienced developer crafting intricate device, the VSDSquadron Mini is your ideal companion. It seamlessly bridges the gap between theory and practical application, offering an on-board flash programmer with single-wire programming protocol to jumpstart your projects in education and development with proficiency and ease.

# Key Features of the VSDSquadron Mini 

**Core Processor**


- The board is powered by CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set, optimized for high-performance computing with support for 2-level interrupt nesting and supports 24MHz system main frequency in the product function.

**Robust GPIO Support**


- Boasts 3 groups of GPIO ports, totalling 15 I/O ports, enabling extensive peripheral connections and mapping to external interrupt capabilities.

**High-Speed Memory**


- Equipped with 2KB SRAM for volatile data storage, 16KB CodeFlash for program memory, and additional 1920B for bootloader functionalities.

**Clock and Reset Systems**


- Includes a built-in factory-trimmed 24MHz RC oscillator and a 128kHz RC oscillator, plus an external 24MHz oscillator option for varied clocking requirements.



**Flexible Communication Interfaces**


- Offers multiple communication protocols including US- ART, I2C, and SPI for versatile connectivity options.

**On-board Programmer**


- Features on-board CH32V305FBP6 single-wire programming protocol, enhancing development efficiency with seamless code deployment and debugging.

**BOARD SPECS**

| **CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set** |
| ------------------------------------------------------------------------- 
| SRAM                                                                       2kb onchip volatile sram     16kb external program memory                                    |
| Processor                                                                  24 MHz                                                                                       |
| Sink Current per I/O Pin                                                   8 mA                                                                                         |
| Source Current per I/O Pin                                                 8 mA                                                                                         |
| Input voltage (nominal)                                                    5 V                                                                                          |
| I/O voltage                                                                3.3 V                                                                                        |
| Programmer/debugger                                                        Onboard RISC-V programmer/debugger, USB to TTL serial port support                           |
| SPI                                                                        1x, PC5(SCK), PC1(NSS), PC6(MOSI), PC7(MISO)                                                 |
| I2C                                                                        1x, PC1(SDA), PC2(SCL)                                                                       |
| USART                                                                      1x, PD6(RX), PD5(TX)|

# Introduction to the VSDNAVICAR

The NaviCar, powered by the VSDSquadron Mini board, is a cutting-edge vehicle designed for multiple applications. Equipped with Bluetooth control and obstacle avoidance, it can navigate autonomously while ensuring safety. In hospitals, it can transport medicines, reducing human contact and speeding up delivery. On the road, it detects and avoids obstacles, preventing traffic accidents. In warehouses, NaviCar can automate material transport, increasing efficiency and reducing the risk of damage. This smart vehicle offers a blend of precision, safety, and automation across various sectors.

The UART (Universal Asynchronous Receiver-Transmitter) protocol is a widely used serial communication standard in embedded systems, in the NaviCar powered by VSDSquadron Mini. It enables data transmission between devices by converting parallel data to serial form and vice versa. UART communication involves two wires: TX (transmit) and RX (receive). The data is transferred asynchronously, meaning no clock signal is required, and both devices must agree on a common baud rate. UART is ideal for Bluetooth modules in NaviCar, ensuring reliable wireless control.

# Table of Connections of the circuit 

| **Component**           | **Pin/Connection**             | **Connected To MINI**              |
|-------------------------|--------------------------------|-------------------------------|
| Bluetooth               |   TX,RX                        |  PD6,PD7                      |
| MotorDriver             |  IN1,IN2,IN3,IN4,                    | PC7,PD2,PD3,PD4 |
| IR Sensor 1              | OUT                            | PC1|
|IR Sensor 2 | OUT| PC2|
|Buzzer| IN | PC3|
|POWER | VCC| 5V|
|POWER |GND| GND|

# Source code of Arduino IDE with comments 
``` c++
#define BLUETOOTH_RX_PIN PD6  // Onboard RX pin (Bluetooth)
#define BLUETOOTH_TX_PIN PD7  // Onboard TX pin (Bluetooth)

// Motor A connections (for left motor)
#define IN1 PC7  // Motor A IN1
#define IN2 PD2  // Motor A IN2

// Motor B connections (for right motor)
#define IN3 PD3  // Motor B IN3
#define IN4 PD4  // Motor B IN4

// IR sensor connections
#define IR_LEFT PC1  // IR sensor for left side
#define IR_RIGHT PC2 // IR sensor for right side

// Buzzer connection
#define BUZZER_PIN PC3  // Pin for the buzzer

void setup() {
  // Start serial communication for Bluetooth
  Serial.begin(9600);
  while (!Serial) {
    ; // Wait for serial port to connect. Needed for native USB port only
  }
  
  // Set motor control pins as outputs
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  
  // Set IR sensors and buzzer pins
  pinMode(IR_LEFT, INPUT);
  pinMode(IR_RIGHT, INPUT);
  pinMode(BUZZER_PIN, OUTPUT);
}

void loop() {
  // Read obstacle detection from IR sensors
  bool obstacleLeft = digitalRead(IR_LEFT) == LOW;  // LOW means obstacle detected
  bool obstacleRight = digitalRead(IR_RIGHT) == LOW; // LOW means obstacle detected

  if (obstacleLeft || obstacleRight )
   {
   // Stop the car if obstacle is detected
    digitalWrite(BUZZER_PIN, HIGH);
    stopCar();



    Serial.println("Obstacle detected! Stopping car.");
  } else {
    digitalWrite(BUZZER_PIN, LOW);  // Turn off the buzzer

    // Only accept and execute commands if no obstacles are detected
    if (Serial.available()) {
      char incomingChar = Serial.read();  // Read the incoming character from Bluetooth
      Serial.print("Received: ");
      Serial.println(incomingChar);

      // Based on the character, perform motor actions
      switch (incomingChar) {
        case 'F':  // Move forward
          moveForward();
          break;
          
        case 'B':  // Move backward
          moveBackward();
          break;
          
        case 'L':  // Turn left
          turnLeft();
          break;
          
        case 'R':  // Turn right
          turnRight();
          break;
          
        case 'S':  // Stop the car
          stopCar();
          break;
          
        default:
          // Do nothing for unrecognized characters
          break;
      }
    }
  }

  delay(10);  // Add a small delay
}

// Function to move the car forward
void moveForward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

// Function to move the car backward
void moveBackward() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

// Function to turn the car left
void turnLeft() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

// Function to turn the car right
void turnRight() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

// Function to stop the car
void stopCar() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}
```
# Image of the VSDNAVICAR
![IMG_20240903_161651](https://github.com/user-attachments/assets/470946a1-47eb-4c72-950f-2135dd46e3fc)


# Demonstration Video of the VSDNAVICAR
```
https://drive.google.com/file/d/1VoYM0Dw4-xRLTiy9zCtznBR6Xd3ewQOk/view?usp=sharing
```
- The NaviCar demonstration highlights its seamless integration with the VSDSquadron Mini board, offering easy Bluetooth connectivity through a mobile interface. The user-friendly app allows you to control the car wirelessly, with precise commands. The car is equipped with obstacle avoidance technology, ensuring it halts when facing obstacles while other directions, like reverse or turns, can still be activated. This makes it particularly useful in the medical field for delivering supplies, in traffic management to avoid collisions, and in warehouses for safe material handling.

# Conclusion
- In conclusion, the NaviCar powered by the VSDSquadron Mini demonstrates the capabilities of advanced Bluetooth-controlled, obstacle-avoiding technology, offering practical applications across diverse fields. Its user-friendly mobile interface allows seamless wireless control, making it highly versatile for use in the medical field, traffic management, and warehousing. The integration of the UART protocol ensures reliable communication, enhancing the car's efficiency and safety. This project showcases the potential of automation and intelligent navigation in solving real-world challenges efficiently.



## Acknowledgement
- [Anagha Ghosh](https://github.com/vsdip), Founder, VSD Corp. Pvt. Ltd
- [Kunal Ghosh](https://github.com/kunalg123), Co-Founder, VSD Corp. Pvt. Ltd

## Author

- [Rajashekhar Kanukuntla](https://github.com/RAJASHEKHAR-KANUKUNTLA), Bachelor of Technology in Electronics &Communication Engineering , University College Of Engineering Kakatiya University, kothagudem,Telangana.
- [Vanshika Tanwar](https://github.com/vanishka-tanwar), Bachelor of Technology in Electronics & Communication Engineering,Dronacharya Group of Institutions,Greater Noida, U.P.

 
