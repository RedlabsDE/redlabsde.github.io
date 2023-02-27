---
title: ESP32 VL53L0X Arduino Füllstand Sensor
categories: ['Digital']
tags: ['arduino', 'esp32', 'vl53lxx', 'vl53l0x'] #always lower case
image:
    path: /blog_images/esp32-vl53lxx-sensor-arduino/sensor_vl53lxx_v2.jpg
    alt: Mit dem VL53L0X (VL53LXX-V2) Laser Abstandssensor den Füllstand von Wasser messen?
date: 2021-09-28T09:06:26.750Z
author: nico
---

## Einleitung

Es gibt viele Möglichkeiten den Füllstand eines Behälters digital zu messen. Einige Lösungen Messen beispielsweise den Druck des Wassers am Behälterboden und ermitteln mithilfe des vorherschenden Umgebungsdrucks die auf dem Sensor stehende Wassersäule. Der Nachteil der Sensor muss sich im zu messenden Medium befinden. Ob man einen solchen Sensor verwenden kann hängt damit auch von der Qualität des Sensors und der zu messenden Flüssigkeit ab.

Vom Messmedium getrennte Sensoren gibt es natürlich auch. Es gibt zum Beispiel kapazitive Sensoren durch welche man ein elektrisches Feld zwischen zwei Elektroden aufspannt. Verändert man das dielektrikum durch welches das elektrische Feld strömt, verändert man dadurch die Kapazität des aufgespannten Kondensators. Damit kann  z.B. die Füllhöhe einer Flüssigkeit kontaktlos ermittelt werden.

Es geht natürlich auch einfacher. Es gibt weit verbreitete günstige Ultraschallsensoren welche die Zeit zwischen aussenden des Ultraschall Signals und dem Empfangen des Ultraschall Signals messen. Die Wasseroberfläche dient hier als Reflektor. Verändert sich die Füllhöhe, verändert sich der Zeitabstand zwischen Senden und Empfangen.

## Problem Analyse

Für unser aktuelles Projekt möchten wir einen robusten, einfach zu verwendenden, kleinen und gleichzeitig günstigen Sensor zum Messen der Füllhöhe eines Wasserbehälters.

## Lösungen

Mit dem VL53LXX-V2 von STMicroelectronics sind wir fündig geworden, er benutzt einen optischen Laser als Sensor. Ähnlich wie bei einem Ultraschall Abstandssensor wird hier die Laufzeit zwischen Absenden und Empfangen gemessen. Kurz TOF (time of flight). Das technisch anspruchsvolle hier ist das der Laser sich mit Lichtgeschwindigkeit ausbreitet. Der Sensor muss extrem kurze Zeitabstände zwischen senden und Empfangen messen können. Der Sensor VL53LXX-V2 hat mit seiner "Single Photon Avalanche
Diode" einen Mindestabstand von nur 8ms und einen Maximalabstand von bis zu 200 cm abhängig von der Oberflächenfarbe. Ideal für unsere Anwendung. Wir konnten jedoch keine Information im Internet darüber finden ob der Sensor auch auf einer Oberfläche wie Wasser funktioniert. Nach einigen Test haben wir festgestellt das unsere Bedenken unberechtigt waren. Der VL53LXX-V2 ermittelt problemlos den Abstand zwischen Wasseroberfläche und Sensor. Durch seine I2C Schnittstelle ist der Sensor einfach anzusteuern.

![](/blog_images/esp32-vl53lxx-sensor-arduino/vl53l0x.png)

## VL53LXX-V2 Libraray

Wir verwenden die Adafruit VL53LXX-V2 Arduino Libraray auf einem Espressif ESP32. Das ESP32 Board arbeitet genau wie der Sensor mit einer Betriebsspannung von 3V3. Um den Anschluss an einen ESP zu erleichtern hier das Pinning:

| VL53LXX-V2 | ESP32 DEVKITV1 |
| ---------- | -------------- |
| VCC        | 3V3            |
| GND        | GND            |
| SCL        | D22            |
| SDA        | D21            |

![](/blog_images/esp32-vl53lxx-sensor-arduino/esp32_vl53lxx-v2.jpg)

## Arduino Code:

```c
// Initial code from Adafruit_VL53L0X arduino library
// https://www.redlabs.de 2020

#include "Adafruit_VL53L0X.h"

Adafruit_VL53L0X lox = Adafruit_VL53L0X();

void setup() {
  Serial.begin(115200);

  // wait until serial port opens for native USB devices
  while (! Serial) {
    delay(1);
  }

  Serial.println("Adafruit VL53L0X test");
  if (!lox.begin()) {
    Serial.println(F("Failed to boot VL53L0X"));
    while(1);
  }
  // power
  Serial.println(F("VL53L0X API Simple Ranging example\n\n"));
}


void loop() {
  VL53L0X_RangingMeasurementData_t measure;

  lox.rangingTest(&measure, false); // pass in 'true' to get debug data printout!

  if (measure.RangeStatus != 4) {  // phase failures have incorrect data
    Serial.print("Distance (mm): "); Serial.println(measure.RangeMilliMeter);
  } else {
    Serial.println(" out of range ");
  }

  delay(100);
}
```

Auf Github <https://github.com/adafruit/Adafruit_VL53L0X>

## Youtube Beispiel Video

{% include embed/youtube.html id='CJdzUrkWAAQ' %}

In dem Video verwenden wir den Arduino Serial Plot Monitor zur grafischen Ausgabe.

Um den Serial Plot Monitor in Arduino IDE zu öffnen einfach über den Menüpunkt "Werkzeuge" -> "Serieller Plotter öffnen".

![](/blog_images/esp32-vl53lxx-sensor-arduino/open_serial_plot.png)

## Zusammenfassung

Der Sensor war mit der Libraray von Adafruit in wenigen Minuten in Betrieb genommen. Damit konnten wir ohne viel Zeit zu verlieren unsere Tests erfolgreich durchführen. Ein großer Dank an das Entwicklerteam des VL53LXX und den entwicklern der Adafruit VL53LXX-V2 Libraray.

## Sicherheit

Der VL53L0X enthält eine Laserdiode. Die Laserleistung ist entwickelt für die Laserschutzklasse 1. Der Hersteller gibt an, dass die Standards nach IEC 60825-1:2014 erfüllt werden. Achte bitte dennoch darauf niemals direkt in den (nicht sichtbaren) Laserstrahl zu blicken.

![](/blog_images/esp32-vl53lxx-sensor-arduino/warning_laser_class1.png)

## Links

* [VL53L0X Datasheet](https://www.st.com/resource/en/datasheet/vl53l0x.pdf)
* [VL53L0X Breakout Board bestellen](https://amzn.to/2E92hGI)
* [ESP32 Devkit V1 bestellen](https://amzn.to/30ZUTXw)
* [Redlabs auf Youtube](https://www.youtube.com/channel/UClXk2zPHlwKuLrD-YCpEjmw)
