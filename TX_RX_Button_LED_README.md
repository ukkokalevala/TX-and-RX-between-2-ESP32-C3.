How the System Works
 ESP-NOW Basics
ESP-NOW is a fast, low-power wireless protocol created by Espressif.
It lets ESP32 boards send small messages to each other without WiFi, without routers, without SSID/password, and without pairing.
Think of it like:
“Instant walkie-talkie for microcontrollers.”
________________________________________
Broadcast Mode — The Trick That Removes MAC Addresses
Normally, ESP-NOW requires you to specify the MAC address of the receiver.
But we use a special broadcast MAC address:
FF:FF:FF:FF:FF:FF
This means:
 “Send this message to EVERY ESP32 nearby.”
Any ESP32-C3 listening in ESP-NOW mode will receive that message automatically.
So:
•	TX sends → All receivers get it
•	No pairing
•	No setup
•	No MAC searching
•	No mistakes
•	Instant communication
________________________________________
TX (Transmitter) Side
The transmitter has two buttons.
When you press:
Button 1
TX sends a broadcast message:
BTN1
Button 2
TX sends:
BTN2
These messages are tiny text packets (just 4 bytes) sent over ESP-NOW.
________________________________________
RX (Receiver) Side
The receiver is always listening.
When it gets a packet:
•	It checks if the message is "BTN1"
→ Turns LED1 ON for 200ms
•	Or if the message is "BTN2"
→ Turns LED2 ON for 200ms
Nothing complicated — just simple message recognition.
________________________________________
Why It Works Instantly
Because:
•	Both ESP32-C3 boards are set to WIFI_STA mode
•	Both are using ESP-NOW
•	TX sends to broadcast address
•	RX listens to everything
No scan.
No registration.
No pairing.
No MAC filtering.
Just simple broadcast messaging, like shouting “BTN1” and every ESP32 in the room hears it.
________________________________________
Summary in 10 Seconds
•	TX sends text messages "BTN1" or "BTN2" using ESP-NOW broadcast.
•	RX hears every broadcast message and checks the content.
•	If it matches, RX flashes the correct LED.
•	No MAC address is required because we use broadcast mode.
