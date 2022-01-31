# arduino-humidistat

Humidistat using an Arduino Uno, DHT11 Sensor, and DIY Mains Power Relay

## Variables

* `swing`: The size of the relative Humidity (RH) range to target. A larger swing allows for more variation in the RH, while reducing the amount of switching. A small swing maintains the RH more precisely/consistently, while increasing the amount of switching. Example, a `targetHumidityPct` of 50 and a swing of 4 would maintain RH between 48 and 52%.
* `targetHumidityPct`: Target humidity percentage.
* `slope`: The slope of the line as calculated from two-point salt calibration.
* `yIntercept`: The y-intercept as calculated from two-point salt calibration.

## Sensor Assembly & Test

### Wiring

Wiring Diagram

* https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239

Note: My DHT11 has a PCB with an onboard resistor, so I wired its leads directly to the Arduino; otherwise, I used the same wiring diagram as above.

### Test

Install required Arduino libraries into Arduino IDE and upload the sketch via USB.

Monitor serial output over USB and look for lines like the following:

`Sensor-Claimed Humidity: 25.20% Humidity: 32.92%  Temperature: 22.30°C 72.14°F  Heat index: 21.44°C 70.60°F`

It doesn't matter what the values are, and your sensor will not be calibrated yet, so both "Humidity" values are likely to be off a bit.

For future reference, the first humidity value, "Sensor-Claimed Humidity" is the one claimed by the sensor. The second, corrected value will reflect the actual humidity once the sensor is calibrated.

## Calibration

The sensor can be calibrated with moistened CaCl (ice melt pellets) and NaCl (kosher salt).

For each salt, in turn, the following procedure was followed:

* In a plastic bottle cap (from a soda bottle or similar) cover its bottom with water (~1ml; tap water is fine). Add enough salt until it is heaped above the lip's level but is not apt to spill.
* In an airtight container (plastic bag, tupperware, or glass casserole dish covered with plastic wrap--my choice, etc.) add:
  * Prepared bottle cap
  * Sensor with its leads protruding from the container
* Wait for equilibrium to be reached. The longer the wait (up to a point) the more accurate the measurement will be. Note:
  * CaCl seems to stabilize more quickly: 4-6 hours.
  * NaCl seems to stabilize more slowly: 12-24 hours.
