# Home-Automation-with-Bluetooth
ChatGPT
You said:
Uploaded image
Give answer 
ChatGPT said:
The CodTech Internship Task-1 is titled:

Push Button Counter
✅ Instructions Summary (from the image):
🔸 Use a temperature sensor to read and display temperature data on an LCD or Serial Monitor.
🔸 Deliverable: Circuit design, code, and output demonstration.

However, there seems to be a mismatch:

The task title says "Push Button Counter".

But the instructions talk about a temperature sensor project.

This likely means one of the two is incorrect.

✅ Likely Correct Task Interpretation:
Assuming "Push Button Counter" is the actual task (as written in bold at the top), here's what you should deliver:

🔧 Project Task: Push Button Counter
🧰 Components Needed:
Arduino UNO

Push Button

Resistor (10kΩ)

Breadboard and jumper wires

LCD (16x2) or Serial Monitor

🔌 Circuit Design:
Connect the push button to a digital pin (e.g., pin 2) with a pull-down resistor.

Connect the LCD or prepare

You said:
Or create 
ChatGPT said:
Sure! Here's a full Push Button Counter project with circuit design, code, and output demonstration steps — perfect for your CodTech Internship Task - 1.

🔧 Project Title: Push Button Counter
🧰 Components Required:
Arduino UNO

Push Button

10kΩ Resistor (for pull-down)

16x2 LCD (or use Serial Monitor)

Breadboard and Jumper Wires

Potentiometer (if using LCD for contrast)

🔌 Circuit Diagram:
For Push Button:
One leg of the button → Digital Pin 2

Same leg → 10kΩ resistor → GND

Other leg of the button → +5V

For LCD (16x2 with I2C or parallel):
Optional: You can use the Serial Monitor instead.

💻 Arduino Code (for Serial Monitor version):
int buttonPin = 2;         // Push button connected to pin 2
int buttonState = 0;
int lastButtonState = 0;
int count = 0;

void setup() {
  Serial.begin(9600);
  pinMode(buttonPin, INPUT);
  Serial.println("Push Button Counter Initialized");
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH && lastButtonState == LOW) {
    count++;
    Serial.print("Button Pressed Count: ");
    Serial.println(count);
    delay(200); // Debouncing delay
  }

  lastButtonState = buttonState;
}
📟 LCD Version Code (16x2 Parallel Wiring)
#include <LiquidCrystal.h>

// RS, E, D4, D5, D6, D7
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

int buttonPin = 7;
int buttonState = 0;
int lastButtonState = 0;
int count = 0;

void setup() {
  pinMode(buttonPin, INPUT);
  lcd.begin(16, 2);
  lcd.print("Push Counter");
  delay(1000);
  lcd.clear();
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH && lastButtonState == LOW) {
    count++;
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Button Count:");
    lcd.setCursor(0, 1);
    lcd.print(count);
    delay(200); // Debouncing
  }

  lastButtonState = buttonState;
}
✅ Deliverables:
✅ Circuit diagram (as described)

✅ Arduino code (above)

✅ Output demonstration (either via Serial Monitor or LCD)

Would you like me to generate a circuit diagram image or upload code to GitHub for submission?

You said:
Yess
ChatGPT said:
You said:
Uploaded image
Give 
ChatGPT said:
Here are the full project guides for CodTech Internship Task - 2 and Task - 3 based on the instructions from your uploaded image:

🔧 Task - 2: Home Automation with Bluetooth
📌 Objective:
Design a Bluetooth-controlled home automation system to switch devices ON and OFF.

🧰 Components Required:
Arduino UNO

HC-05 Bluetooth Module

Relay Module (1/2/4 channel)

Bulb or LED + 230V/5V device (for demo)

Android Smartphone with Bluetooth Terminal App

Jumper Wires + Breadboard

🔌 Circuit Connections:
HC-05 Bluetooth Module:

VCC → 5V

GND → GND

TX → RX (pin 0 of Arduino)

RX → TX (pin 1 of Arduino) (use voltage divider for safety)

Relay Module:

IN1 → Arduino pin 8

VCC → 5V

GND → GND

Connect a lamp or bulb to NO and COM terminals

💻 Arduino Code:
int relayPin = 8;
char data = 0;

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, LOW);
}

void loop() {
  if (Serial.available()) {
    data = Serial.read();
    if (data == '1') {
      digitalWrite(relayPin, HIGH); // Turn ON
    } else if (data == '0') {
      digitalWrite(relayPin, LOW); // Turn OFF
    }
  }
}
📱 Working:
Open a Bluetooth Terminal app.

Pair with HC-05 (default password: 1234 or 0000).

Send '1' to turn ON, '0' to turn OFF.

✅ Deliverables:
Circuit diagram

Arduino code

Video or live demo showing device ON/OFF via Bluetooth

🌡️ Task - 3: Temperature Monitoring
📌 Objective:
Use a temperature sensor to monitor and display temperature on LCD or Serial Monitor.

🧰 Components Required:
Arduino UNO

LM35 Temperature Sensor

LCD (16x2) or Serial Monitor

Jumper wires + Breadboard

🔌 Circuit:
LM35:

VCC → 5V

GND → GND

OUT → A0

LCD (if used):

RS → pin 12

E → pin 11

D4-D7 → pins 5, 4, 3, 2

Connect VSS, VDD, and VO properly

💻 Code (Serial Monitor Version):
int tempPin = A0;
float temp;

void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(tempPin);
  temp = (val / 1024.0) * 5000; // in mV
  temp = temp / 10; // Convert to °C
  Serial.print("Temperature: ");
  Serial.print(temp);
  Serial.println(" C");
  delay(1000);
}
✅ Deliverables:
Circuit diagram

Code

Output (via LCD or serial)

Would you like me to create circuit diagrams for both Task 2 and 3 as images?

You said:
Give task 2
ChatGPT said:
Sure! Here's the complete solution for CodTech Internship Task - 2: Home Automation with Bluetooth — including circuit design, code, and working demo steps.

🔧 CodTech Task - 2: Home Automation with Bluetooth
📌 Objective:
Design a Bluetooth-controlled home automation system to switch appliances ON and OFF using a smartphone.

🧰 Components Required:
Component	Quantity
Arduino UNO	1
HC-05 Bluetooth Module	1
Relay Module (1-Channel)	1
LED or 230V bulb	1
Jumper Wires + Breadboard	-
1kΩ + 2kΩ resistors (for voltage divider)	1 each
🔌 Circuit Diagram (Description):
🔹 HC-05 Bluetooth Module:
VCC → 5V on Arduino

GND → GND

TX → RX (pin 0 on Arduino)

RX → TX (pin 1) (via a voltage divider: TX from Arduino → 1kΩ → RX of HC-05; between 1kΩ and HC-05 RX, connect a 2kΩ to GND)

🔹 Relay Module:
IN1 → Pin 8 on Arduino

VCC → 5V

GND → GND

Connect a lamp or fan to the COM and NO terminals of relay for switching.

💻 Arduino Code:
int relayPin = 8;   // Relay control pin
char data = 0;

void setup() {
  Serial.begin(9600);        // Initialize Bluetooth communication
  pinMode(relayPin, OUTPUT); // Set relay pin as output
  digitalWrite(relayPin, LOW); // Initially OFF
}

void loop() {
  if (Serial.available()) {
    data = Serial.read(); // Read data from Bluetooth
    if (data == '1') {
      digitalWrite(relayPin, HIGH); // Turn ON relay
    } 
    else if (data == '0') {
      digitalWrite(relayPin, LOW); // Turn OFF relay
    }
  }
}
📱 Smartphone Control:
Install Bluetooth Terminal or Serial Bluetooth app from Play Store.

Pair with HC-05 module (default PIN: 1234 or 0000).

Send '1' → Turns ON the device (relay activates).

Send '0' → Turns OFF the device.

✅ Deliverables:
✅ Circuit Diagram (can be hand-drawn or software-generated)

✅ Arduino Code (above)

✅ Video/Photo of Working Demo

Would you like me to now generate a visual circuit diagram for this task?

You said:
Give for submission 
ChatGPT said:
You said:
Give task 2 answer 
ChatGPT said:
Here is the complete submission-ready answer for Task - 2 of the CodTech Internship:

🛠️ CodTech Internship – Task 2
📌 Title: Home Automation with Bluetooth
🔶 Objective
To design a Bluetooth-controlled home automation system using an Arduino UNO and HC-05 module, allowing users to switch devices ON/OFF wirelessly using a smartphone.

🔧 Components Used
S.No.	Component	Quantity
1	Arduino UNO	1
2	HC-05 Bluetooth Module	1
3	1-Channel Relay Module	1
4	LED / Bulb (for output)	1
5	Resistors (1kΩ, 2kΩ)	1 each
6	Jumper Wires	As needed
7	Breadboard	1
8	Android Phone with Bluetooth Terminal App	1
⚙️ Working Principle
The HC-05 Bluetooth module receives ON/OFF commands from a smartphone.

Arduino reads this data via serial communication.

Based on input ('1' or '0'), Arduino toggles the relay to switch the appliance ON or OFF.

🔌 Circuit Description
📲 HC-05 Bluetooth Module:
VCC → Arduino 5V

GND → Arduino GND

TX → Arduino RX (Pin 0)

RX → Arduino TX (Pin 1) via Voltage Divider (1kΩ & 2kΩ)

⚡ Relay Module:
IN → Arduino Pin 8

VCC → Arduino 5V

GND → Arduino GND

Output Load (LED/Bulb) → Connected to COM and NO terminals
ChatGPT
You said:
Uploaded image
Give answer 
ChatGPT said:
The CodTech Internship Task-1 is titled:

Push Button Counter
✅ Instructions Summary (from the image):
🔸 Use a temperature sensor to read and display temperature data on an LCD or Serial Monitor.
🔸 Deliverable: Circuit design, code, and output demonstration.

However, there seems to be a mismatch:

The task title says "Push Button Counter".

But the instructions talk about a temperature sensor project.

This likely means one of the two is incorrect.

✅ Likely Correct Task Interpretation:
Assuming "Push Button Counter" is the actual task (as written in bold at the top), here's what you should deliver:

🔧 Project Task: Push Button Counter
🧰 Components Needed:
Arduino UNO

Push Button

Resistor (10kΩ)

Breadboard and jumper wires

LCD (16x2) or Serial Monitor

🔌 Circuit Design:
Connect the push button to a digital pin (e.g., pin 2) with a pull-down resistor.

Connect the LCD or prepare

You said:
Or create 
ChatGPT said:
Sure! Here's a full Push Button Counter project with circuit design, code, and output demonstration steps — perfect for your CodTech Internship Task - 1.

🔧 Project Title: Push Button Counter
🧰 Components Required:
Arduino UNO

Push Button

10kΩ Resistor (for pull-down)

16x2 LCD (or use Serial Monitor)

Breadboard and Jumper Wires

Potentiometer (if using LCD for contrast)

🔌 Circuit Diagram:
For Push Button:
One leg of the button → Digital Pin 2

Same leg → 10kΩ resistor → GND

Other leg of the button → +5V

For LCD (16x2 with I2C or parallel):
Optional: You can use the Serial Monitor instead.

💻 Arduino Code (for Serial Monitor version):
int buttonPin = 2;         // Push button connected to pin 2
int buttonState = 0;
int lastButtonState = 0;
int count = 0;

void setup() {
  Serial.begin(9600);
  pinMode(buttonPin, INPUT);
  Serial.println("Push Button Counter Initialized");
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH && lastButtonState == LOW) {
    count++;
    Serial.print("Button Pressed Count: ");
    Serial.println(count);
    delay(200); // Debouncing delay
  }

  lastButtonState = buttonState;
}
📟 LCD Version Code (16x2 Parallel Wiring)
#include <LiquidCrystal.h>

// RS, E, D4, D5, D6, D7
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

int buttonPin = 7;
int buttonState = 0;
int lastButtonState = 0;
int count = 0;

void setup() {
  pinMode(buttonPin, INPUT);
  lcd.begin(16, 2);
  lcd.print("Push Counter");
  delay(1000);
  lcd.clear();
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH && lastButtonState == LOW) {
    count++;
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("Button Count:");
    lcd.setCursor(0, 1);
    lcd.print(count);
    delay(200); // Debouncing
  }

  lastButtonState = buttonState;
}
✅ Deliverables:
✅ Circuit diagram (as described)

✅ Arduino code (above)

✅ Output demonstration (either via Serial Monitor or LCD)

Would you like me to generate a circuit diagram image or upload code to GitHub for submission?

You said:
Yess
ChatGPT said:
You said:
Uploaded image
Give 
ChatGPT said:
Here are the full project guides for CodTech Internship Task - 2 and Task - 3 based on the instructions from your uploaded image:

🔧 Task - 2: Home Automation with Bluetooth
📌 Objective:
Design a Bluetooth-controlled home automation system to switch devices ON and OFF.

🧰 Components Required:
Arduino UNO

HC-05 Bluetooth Module

Relay Module (1/2/4 channel)

Bulb or LED + 230V/5V device (for demo)

Android Smartphone with Bluetooth Terminal App

Jumper Wires + Breadboard

🔌 Circuit Connections:
HC-05 Bluetooth Module:

VCC → 5V

GND → GND

TX → RX (pin 0 of Arduino)

RX → TX (pin 1 of Arduino) (use voltage divider for safety)

Relay Module:

IN1 → Arduino pin 8

VCC → 5V

GND → GND

Connect a lamp or bulb to NO and COM terminals

💻 Arduino Code:
int relayPin = 8;
char data = 0;

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, LOW);
}

void loop() {
  if (Serial.available()) {
    data = Serial.read();
    if (data == '1') {
      digitalWrite(relayPin, HIGH); // Turn ON
    } else if (data == '0') {
      digitalWrite(relayPin, LOW); // Turn OFF
    }
  }
}
📱 Working:
Open a Bluetooth Terminal app.

Pair with HC-05 (default password: 1234 or 0000).

Send '1' to turn ON, '0' to turn OFF.

✅ Deliverables:
Circuit diagram

Arduino code

Video or live demo showing device ON/OFF via Bluetooth

🌡️ Task - 3: Temperature Monitoring
📌 Objective:
Use a temperature sensor to monitor and display temperature on LCD or Serial Monitor.

🧰 Components Required:
Arduino UNO

LM35 Temperature Sensor

LCD (16x2) or Serial Monitor

Jumper wires + Breadboard

🔌 Circuit:
LM35:

VCC → 5V

GND → GND

OUT → A0

LCD (if used):

RS → pin 12

E → pin 11

D4-D7 → pins 5, 4, 3, 2

Connect VSS, VDD, and VO properly

💻 Code (Serial Monitor Version):
int tempPin = A0;
float temp;

void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(tempPin);
  temp = (val / 1024.0) * 5000; // in mV
  temp = temp / 10; // Convert to °C
  Serial.print("Temperature: ");
  Serial.print(temp);
  Serial.println(" C");
  delay(1000);
}
✅ Deliverables:
Circuit diagram

Code

Output (via LCD or serial)

Would you like me to create circuit diagrams for both Task 2 and 3 as images?

You said:
Give task 2
ChatGPT said:
Sure! Here's the complete solution for CodTech Internship Task - 2: Home Automation with Bluetooth — including circuit design, code, and working demo steps.

🔧 CodTech Task - 2: Home Automation with Bluetooth
📌 Objective:
Design a Bluetooth-controlled home automation system to switch appliances ON and OFF using a smartphone.

🧰 Components Required:
Component	Quantity
Arduino UNO	1
HC-05 Bluetooth Module	1
Relay Module (1-Channel)	1
LED or 230V bulb	1
Jumper Wires + Breadboard	-
1kΩ + 2kΩ resistors (for voltage divider)	1 each
🔌 Circuit Diagram (Description):
🔹 HC-05 Bluetooth Module:
VCC → 5V on Arduino

GND → GND

TX → RX (pin 0 on Arduino)

RX → TX (pin 1) (via a voltage divider: TX from Arduino → 1kΩ → RX of HC-05; between 1kΩ and HC-05 RX, connect a 2kΩ to GND)

🔹 Relay Module:
IN1 → Pin 8 on Arduino

VCC → 5V

GND → GND

Connect a lamp or fan to the COM and NO terminals of relay for switching.

💻 Arduino Code:
int relayPin = 8;   // Relay control pin
char data = 0;

void setup() {
  Serial.begin(9600);        // Initialize Bluetooth communication
  pinMode(relayPin, OUTPUT); // Set relay pin as output
  digitalWrite(relayPin, LOW); // Initially OFF
}

void loop() {
  if (Serial.available()) {
    data = Serial.read(); // Read data from Bluetooth
    if (data == '1') {
      digitalWrite(relayPin, HIGH); // Turn ON relay
    } 
    else if (data == '0') {
      digitalWrite(relayPin, LOW); // Turn OFF relay
    }
  }
}
📱 Smartphone Control:
Install Bluetooth Terminal or Serial Bluetooth app from Play Store.

Pair with HC-05 module (default PIN: 1234 or 0000).

Send '1' → Turns ON the device (relay activates).

Send '0' → Turns OFF the device.

✅ Deliverables:
✅ Circuit Diagram (can be hand-drawn or software-generated)

✅ Arduino Code (above)

✅ Video/Photo of Working Demo

Would you like me to now generate a visual circuit diagram for this task?

You said:
Give for submission 
ChatGPT said:
You said:
Give task 2 answer 
ChatGPT said:
Here is the complete submission-ready answer for Task - 2 of the CodTech Internship:

🛠️ CodTech Internship – Task 2
📌 Title: Home Automation with Bluetooth
🔶 Objective
To design a Bluetooth-controlled home automation system using an Arduino UNO and HC-05 module, allowing users to switch devices ON/OFF wirelessly using a smartphone.

🔧 Components Used
S.No.	Component	Quantity
1	Arduino UNO	1
2	HC-05 Bluetooth Module	1
3	1-Channel Relay Module	1
4	LED / Bulb (for output)	1
5	Resistors (1kΩ, 2kΩ)	1 each
6	Jumper Wires	As needed
7	Breadboard	1
8	Android Phone with Bluetooth Terminal App	1
⚙️ Working Principle
The HC-05 Bluetooth module receives ON/OFF commands from a smartphone.

Arduino reads this data via serial communication.

Based on input ('1' or '0'), Arduino toggles the relay to switch the appliance ON or OFF.

🔌 Circuit Description
📲 HC-05 Bluetooth Module:
VCC → Arduino 5V

GND → Arduino GND

TX → Arduino RX (Pin 0)

RX → Arduino TX (Pin 1) via Voltage Divider (1kΩ & 2kΩ)

⚡ Relay Module:
IN → Arduino Pin 8

VCC → Arduino 5V

GND → Arduino GND

Output Load (LED/Bulb) → Connected to COM and NO terminals

💻 Arduino Code
int relayPin = 8;
char data = 0;

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, LOW); // Initially OFF
}

void loop() {
  if (Serial.available()) {
    data = Serial.read();
    if (data == '1') {
      digitalWrite(relayPin, HIGH); // Turn ON device
    } else if (data == '0') {
      digitalWrite(relayPin, LOW); // Turn OFF device
    }
  }
}
📱 How to Control via Smartphone
Download Bluetooth Terminal from Play Store.

Pair with HC-05 module (PIN: 1234 or 0000).

Open terminal → connect to HC-05.

Send:

'1' → to Turn ON the device.

'0' → to Turn OFF the device.

📸 Deliverables
✅ Circuit Diagram (you can draw based on the above circuit description)

✅ Arduino Code (provided above)

✅ Demo Video or Photos (showing relay switching via phone)
