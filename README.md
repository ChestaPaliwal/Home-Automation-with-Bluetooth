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
