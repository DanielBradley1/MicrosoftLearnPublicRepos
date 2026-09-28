<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/connecting-serial-devices -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Connecting Serial Microcontroller Devices

Data Streamer can connect to serial enabled devices such as:

- [Arduino Uno and related boards](https://www.arduino.cc/en/Main/Products)
- [micro:bit](https://microbit.org/)
- [Circuit Playground](https://learn.adafruit.com/introducing-circuit-playground)
- [MXChip Azure IoT DevKit](https://microsoft.github.io/azure-iot-developer-kit/v1/)
- any other serial enabled device

This makes it possible to use Microsoft Excel as a flexible and dynamic streaming data dashboard.

## Data Format

The data format for packaging streaming data is a comma Separated Values \(CSV\) string.

For Arduino UNO a serial message containing the value of analog input and the state of a digital input can be sent using the following code:

```c
int analogSensor1;
int digitalSensor1;

void setup() {
  Serial.begin(9600);
  pinMode(2, INPUT);  
}

void loop() {
  analogSensor1 = analogRead(A0);
  digitalSensor1 = digitalRead(2);

  Serial.print(analogSensor1);
  Serial.print(",");  
  Serial.print(digitalSensor1);
  Serial.println();
}
```

## Connecting to Data Streamer

1. Plug in your serial enabled microcontroller to your computer with a USB cable.
2. On the Data Streamer ribbon in Excel, select **Connect A Device**.
3. Select **Start Data**.

You should now see the values of your sensors streaming into your workbook.

## Advanced Window Device Settings

Data Streamer also has an Advanced Window to manage device settings, view the serial data console, or to change global user settings. For more information, see [Advanced settings for Excel's Data Streamer add-in](https://support.office.com/en-us/article/advanced-settings-for-excel-s-data-streamer-add-in-94cda451-880c-43c7-903c-0212ee188460).
