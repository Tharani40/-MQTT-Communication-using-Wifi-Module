# EXP 1(E) CLOUD-BASED DEVICE CONTROL USING MQTT AND WI-FI COMMUNICATION

## Aim

To control an electrical device remotely through a cloud platform using MQTT communication and a Wi-Fi module.

# Hardware / Software Tools Required

- Arduino UNO / ESP32 / ESP8266 Wi-Fi Module
- USB Cable
- PC/Laptop
- Arduino IDE
- Wi-Fi Network
- Relay Module
- LED / DC Load
- Breadboard
- Jumper Wires
- Cloud Platform such as Blynk or ThingSpeak
- MQTT Broker / MQTT Service

# Procedure

## Step 1: Assemble the Circuit

1. Place the microcontroller board, Wi-Fi module, relay module, LED/load, and breadboard on the workbench.
2. Connect the required power supply and GND connections.
3. Ensure that the Wi-Fi module and controller operate at their specified voltage levels.

## Step 2: Connect the Relay Module

1. Connect the **VCC** of the relay module to the appropriate power supply.
2. Connect the **GND** of the relay module to **GND**.
3. Connect the relay input pin to a suitable digital output pin of the controller.
4. Connect the LED or other low-voltage load through the relay contacts.
5. Do not connect mains voltage directly during laboratory testing unless the setup is specifically designed and supervised for it.

## Step 3: Configure Wi-Fi Communication

1. Connect the Wi-Fi-enabled controller to the required Wi-Fi network.
2. Enter the Wi-Fi SSID and password in the program.
3. Verify that the device obtains an IP address.
4. Confirm that the controller can establish an Internet connection.

## Step 4: Configure the Cloud / MQTT Platform

1. Create an account on the selected cloud platform such as **Blynk** or **ThingSpeak**, as applicable.
2. Configure the required device, virtual control, channel, or dashboard.
3. Configure the MQTT broker/server details.
4. Set the MQTT topic used for ON/OFF control.
5. Define the payload values, for example:
   - `ON` – Switch device ON
   - `OFF` – Switch device OFF

## Step 5: Write and Upload the Program

1. Open the Arduino IDE.
2. Include the required Wi-Fi and MQTT libraries.
3. Enter the Wi-Fi credentials and MQTT broker details.
4. Configure the relay output pin.
5. Establish a connection with the Wi-Fi network.
6. Establish a connection with the MQTT broker.
7. Subscribe to the required MQTT topic.
8. Write the callback function to process ON/OFF commands.
9. Verify the program using the **Verify** button.
10. Upload the program to the controller.

## Step 6: Execute the Program

1. Power ON the controller and Wi-Fi module.
2. Open the configured cloud dashboard or MQTT client.
3. Send an **ON** command through the configured MQTT topic.
4. Observe that the relay activates and the connected device turns ON.
5. Send an **OFF** command.
6. Observe that the relay deactivates and the connected device turns OFF.
7. Monitor the Serial Monitor to verify MQTT connection and received commands.

## Step 7: Verify the Output

1. Check whether the controller successfully connects to Wi-Fi.
2. Verify the MQTT broker connection.
3. Send an ON command from the cloud platform.
4. Observe the device switching ON.
5. Send an OFF command from the cloud platform.
6. Observe the device switching OFF.
7. Record the commands and corresponding device states.

# Program
```
#define BLYNK_TEMPLATE_ID "TMPL37YjFuOSC"
#define BLYNK_TEMPLATE_NAME "ARDUINO LEDBLINK"
#define BLYNK_AUTH_TOKEN "-0jzmjz_pAaRNTZSczXd1I3y91hO7OxU"

#define BLYNK_PRINT Serial

#include <WiFiS3.h>
#include <BlynkSimpleWifi.h>

char ssid[] = "Thara";
char pass[] = "9566370385";

const int LED_PIN = LED_BUILTIN;

BLYNK_WRITE(V0)
{
  int value = param.asInt();

  if (value == 1)
  {
    digitalWrite(LED_PIN, HIGH);
    Serial.println("LED ON");
  }
  else
  {
    digitalWrite(LED_PIN, LOW);
    Serial.println("LED OFF");
  }
}

void setup()
{
  Serial.begin(115200);

  pinMode(LED_PIN, OUTPUT);
  digitalWrite(LED_PIN, LOW);

  Serial.println("Connecting to Blynk...");

  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);

  Serial.println("Connected to Blynk!");
}

void loop()
{
  Blynk.run();
}
```
# Observation
# LED ON
<img width="900" height="1600" alt="image" src="https://github.com/user-attachments/assets/d149b014-3d75-4ea8-a8c5-7a9022e70c73" />

# LED OFF
<img width="900" height="1600" alt="image" src="https://github.com/user-attachments/assets/cabd36ec-424d-4481-a1d3-99db940346af" />

# Result
The **cloud-based device control system was successfully implemented using MQTT and Wi-Fi communication**. The device was remotely controlled by sending ON/OFF commands through the MQTT communication channel. The experiment demonstrated the use of **IoT cloud connectivity, MQTT messaging, Wi-Fi communication, and remote device control**.
