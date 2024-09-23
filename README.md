# VSD_SEMICON2024-VSDNAVICAR
VSD NAVICAR made using VSDQUADRON RISCV MINI Board . Presented at SEMICON INDIA 2024 

***The SEMICON_VSDNaviCar, Powered by the VSDSquadron Mini***
***“Avoid the Unseen ,the future of mobility”***

TEAM VSD SAFE VISIONARIES


# Table of the Content
- [Introduction to the VSDSquadron Mini](#Introduction-to-the-VSDSquadron-Mini)
- [Key Features of the VSDSquadron Mini](#Key-Features-of-the-VSDSquadron-Mini)
- [Introduction to the VSDNAVICAR](#Introduction-to-the-VSDNAVICAR)
- [Table of Connections of the circuit](#Table-of-Connections-of-the-circuit)
- [Source code of Arduino IDE with comments](#Source-code-of-Arduino-IDE-with-comments)
- [Image of the SEMICON_VSDNAVICAR](#Image-of-the-SEMICON-VSDNAVICAR)
- [Demonstration Video of the SEMICON_VSDNAVICAR](#Demonstration-Video-of-the-VSDNAVICAR)
- [Conclusion](#Conclusion)
- [Representation of VSDNAVICAR at SEMICON INDIA Event 2024](#Representation-of-VSDNAVICAR-at-SEMICON-INDIA-Event-2024)
- [Acknowledgement](#Acknowledgement)
- [Author](#Author)
# Introduction to the VSDSquadron Mini 
The VSDSquadron Mini, is a mini board which is powered by RISCV 32 bit instruction set that elevates the development of the the board to a open source community and give it a new heights in the field of semiconductorIndustry . Whether you’re a new to this board or any experienced person will come to use this board who knows about RISC-V , he/she will be able to program and use this board easily which gives them the real exposure of the embedded system as well as the exposure to real world applications. The VSDSquadron Mini is your ideal companion, of Arduino UNO which is based on 28nm technology and it seamlessly bridges the gap between theory and practical application problems of the real world, offering an on-board flash programmer with single-wire programming protocol to jumpstart your projects in education and development with proficiency and ease with flexibility to powered it with c-type cable.


![vsdquadron mini](https://github.com/user-attachments/assets/8a530c0b-33b5-4ae6-a46f-1c009003b58a)



# Key Features of the VSDSquadron Mini 

**Core Processor**


- The board is powered by CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set, which is optimized for high-performance computing providing support for 2-level interrupt pins and supports 24MHz system main clock frequency in the product function itself.

**Robust GPIO Support**


- It Boasts 3 groups of GPIO ports, totalling 15 I/O ports, which enables extensive peripheral connections to other pins and mapping it to the external interrupt capabilities as well.

**High-Speed Memory**


- The VSDQUADRON Mini Board is itself Equipped with 2KB SRAM for volatile data storage, 16KB CodeFlash for programming memory, and it's also providing the additional 1920B for bootloader functionalities.

**Clock and Reset Systems**


- It also Includes a built-in factory-trimmed 24MHz RC oscillator and a 128kHz RC oscillator, plus an external 24MHz oscillator option for variying clocking frequency requirements.



**Flexible Communication Interfaces**


- Offers multiple communication protocols including USART, I2C, and SPI to provide versatile connectivity options.

**On-board Programmer**


- It has a feature of Features on-board CH32V305FBP6 single-wire programming protocol, enhancing development efficiency with seamless code deployment and debugging.

**BOARD SPECS**

The Board specifications in the table format is given below:- 

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

The NaviCar has been named as NaviCar because it's a combination of 2 names Navigating + Car = Navi Car , which means it's Navigating the obstacle automatically and hence changes , its diurection either left or right in the forward motion accordingly whenever any obstacle come in front of it  and it also buzzes whenever any obstacle or hindrance come in front of it. 

### NAVICAR - Avoid the unseen , the Future of Mobility ###

The NaviCar, powered by the VSDSquadron Mini board, is a cutting-edge vehicle designed for multiple applications. This car has been Equipped with Bluetooth control Module and obstacle avoidance which is equipped with 2 IR sensors as well as buzzer , it can navigate autonomously whenever any obstacle come in front of it while ensuring safety as well as, the buzzer is used. 

## Applications of VSDNaviCar

Meet Our Navicar; it Concisely Addresses in many Areas , In hospitals, it can be used for transporting medicines which limits human interaction as well as enhances the rate of delivery. It recognizes as well as circumvents hindrances or obstacles while traveling on road, hence preventing any potential road accidents. In warehouses, NaviCar can assist in the transportation of materials from the maximizing productivity and minimizing the eradication of such materials to wear and tear. This smart vehicle offers a kind of precision, safety and automation in all areas. This will also help to any person with disability who are on wheelchair and cannot able to walk so, they can control this car by their phone by connecting it with their phone with bluetooth and can send it for bringing medicines from another room, or if the same person needs any other thing he/she will get the other things by sitting only at one place . Hence, our NaviCar is providing the versatile assistance to those as well who are in need by avoiding all obstacles in between.

## Working of NaviCar with VSDQUADRON MINI BOARD

VSDQUADRON RISCV MINI BOARD is the main brain/CPU of the NaviCar which is providing power and all the communication and flexibility for controlling the car with bluetooth, providing power to IR sensor and buzzer as well .

The UART (Universal Asynchronous Receiver-Transmitter) is a widely used serial communication protocol in embedded systems. In the NaviCar which is powered by VSDSquadron Mini, this protocol has been used to provide serial communication between the bluetooth module and vsdquadron mini board. Hence, it enables data transmission between devices by converting parallel data to serial form and vice versa. UART communication is constituted by two wire connections: the TX wire and the RX wire. The transmission of the data is done in an asynchronous manner which means that there is no clock signal to be used although there is a common baud rate which both devices must comply to. It is made sure that the use of the UART in the Bluetooth modules within the NaviCar enables the applications to safely control devices wirelessly.

In an IR sensor, there is an IR LED that emits infrared light to detect obstacles. If there is an obstacle, the beam of light is reflected back to the receiving part of the sensor (photodiode), which creates the signal. If however there is no obstacle, the IR light does not in any way reflect back thus no signal is created. 
In NaviCar , as soon as obstacle is detected , the beam of the light will reflects back to the receiver which gets receiving signal  , and hence, it creates a signal which is sent to the buzzer , the buzzer starts buzzing indicating that there is any obstacle come in between , and when from the remote control or from our phone we take back or chnages the direction of NaviCar to the right or left or obstacle is removed in front of the car, buzzer automatically stops buzzing indicating that there, is no obstacle now, and the way is clean Navicar can go further. 

Other than this, Motor driver has also been used in this for providing power and controlling motors of the tyres of the NaviCar. This Car can also be controlled with chargeable as well as with Rechargeable batteries dependinng as per the user requirements.

# Circuit Connections with VSDQUADRON RISCV Mini Board with all the components  

| **Component**           | **Pin/Connection with RISCV Mini**             | **Connected To MINI**              |
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
# Image of the SEMICON_VSDNAVICAR
![IMG_20240903_161651](https://github.com/user-attachments/assets/470946a1-47eb-4c72-950f-2135dd46e3fc)


# Demonstration Video of the SEMICON_VSDNAVICAR

[Demo video](https://drive.google.com/file/d/1VoYM0Dw4-xRLTiy9zCtznBR6Xd3ewQOk/view?usp=sharing)

- The NaviCar demonstration showcases its smooth integration with the VSDSquadron Mini board, providing effortless Bluetooth connectivity via a mobile interface. Through the user-friendly app, you can wirelessly maneuver the car with precise commands. The car comes with obstacle avoidance technology, ensuring it stops in front of obstacles while still allowing activation of reverse or turning in other directions. This feature makes it especially valuable in the medical field for supply delivery, in traffic management to prevent accidents, and in warehouses for secure material handling.


# Conclusion
- In conclusion,the NaviCar, powered by the VSDSquadron RISCV Mini, illustrates the capabilities of advanced Bluetooth-controlled, obstacle-avoiding technology, offering practical applications across various fields. Itsproviding user-friendly mobile interface which allows seamless wireless control, making it highly adaptable for use in the medical field, traffic management, and warehousing. The integration of the UART protocol ensures dependable communication, enhancing the car's efficiency and safety.Similarly, the integration of IR sensor with buzzer an dmotor drivers providing it enhanced capability and efficiency for safety purpose. This project demonstrates the potential of automation and intelligent navigation in efficiently addressing real-world challenges.



# Representation of VSDNAVICAR at SEMICON INDIA Event 2024 

Here, are some of the glimpses of our VSDNAVICAR which is presented at SEMICON INDIA 2024, held in IEML Expo Mart ,Greater Noida ,Uttar Pradesh .

![IMG20240912132150](https://github.com/user-attachments/assets/d358d3f2-3167-49ab-8824-42b12744de06)



![ss9](https://github.com/user-attachments/assets/6ba0fccc-ce77-47c8-bf47-d4caae206981)



![ss2](https://github.com/user-attachments/assets/a868a0bb-b81e-491e-9174-ae1d21c9332b)

![ss3](https://github.com/user-attachments/assets/435429bb-ca59-4dc8-abd5-9d76cdb353f4)



#### Here, are some of the other Memorable Glimpse with the VSD Team at the SEMICON INDIA Event 2024 ....


![ss10](https://github.com/user-attachments/assets/1b85d98c-5a2b-4295-a6a2-0910ad388781)


![ss11](https://github.com/user-attachments/assets/4e7d4e2b-36e8-4892-bc9e-008614a46d30)


![ss5](https://github.com/user-attachments/assets/ed896e7c-7bae-47b4-b183-c874e5c34097)

![ss1](https://github.com/user-attachments/assets/d9396582-7133-4298-94b9-810223f5772b)


![ss8](https://github.com/user-attachments/assets/f9ce7a15-8b94-4f1e-91a7-2188514ff391)







https://github.com/user-attachments/assets/8b3b3826-3a0f-4d5a-9a5e-8d52eb4473f4



![ss7](https://github.com/user-attachments/assets/d40fec5e-f184-4c6a-af6e-ec1532eb628d)




## Acknowledgement
- [Anagha Ghosh](https://github.com/vsdip), Founder, VSD Corp. Pvt. Ltd
- [Kunal Ghosh](https://github.com/kunalg123), Co-Founder, VSD Corp. Pvt. Ltd

## Author


- [Vanshika Tanwar](https://github.com/VanshikaTanwar), Bachelor of Technology in Electronics & Communication Engineering,Dronacharya Group of Institutions,Greater Noida, U.P.
- [Rajashekhar Kanukuntla](https://github.com/RAJASHEKHAR-KANUKUNTLA), Bachelor of Technology in Electronics &Communication Engineering , University College Of Engineering Kakatiya University, kothagudem,Telangana.

 
