---
title: ESP8266 Gateway mit WLAN auf 433MHz
categories: ['Digital']
tags: ['esp8266'] #always lower case
image:
    path: /blog_images/wlan-433mhz-gateway-mit-esp-12/012-00-Assembled1.png
    alt: ESP8266 Gateway mit WLAN auf 433MHz. Eine Anleitung um mit einem ESP8266 als Wlan Gateway Funktsteckdosen zu Steuern. Wir zeigen dir wie es geht.
date: 2018-05-20T05:41:13.377Z
author: julian
---

Hier unser Nachfolger Projekt zu [funksteckdose-über-netzwerk-steuern](/blog/funksteckdose-ueber-netzwerk-steuern/). Diesmal gibt es ein brandneues Gateway mit welchem sich ganz einfach verschiedenste Projekte umsetzten lassen. Nachfolgend die Technischen Details zu unserem ESP-12E Gateway.

* * *

## Technische Details

## Bauteile:

- ESP-12E (ESP8266) mit Arduino Bootloader WiFi Module + MCU
- [TLE42644](http://www.ti.com/lit/ds/symlink/pca9554.pdf) 5V Linear Regler (für 433MHz Module + Port expander)
- [MC34063](http://www.onsemi.com/pub/Collateral/MC34063A-D.PDF) 3.3V DCDC Haupt-Versorgung
- [PCA9554](http://www.ti.com/lit/ds/symlink/pca9554.pdf) / [PCF8574](http://www.ti.com/lit/ds/symlink/pcf8574.pdf) I2C Port Expander, 5V GPIOs (push-pull / open-drain)
- 433MHz Sender / Empfänger   [Modul 433Mhz TX/RX](https://www.amazon.de/Aukru-Superregeneration-433M-receiver-module/dp/B00R2U8OEU/ref=sr_1_3?ie=UTF8&qid=1511183759&sr=8-3&keywords=433+MHz)
- [DS18B20](https://datasheets.maximintegrated.com/en/ds/DS18B20.pdf) Digital temperature sensor, one-wire bus
- 3x open-drain MOSFET Treiber für 12V RGB LED strip

## Einsatzmöglichkeiten:

- Haus Automatisierung
- 433MHz Funksteckdosen ansteuern
- Funk Fernbedienungen auswerten
- Digitale Eingänge
    - Tasten / Signal Eingänge mit Interrupt Funktion
    - PIR Bewegungsmelder auswerten
    - Benutzer Taste auf PCB
- Digitale Ausgänge
    - Benutzer LED auf PCB
- Onewire Bus
    - Digitaler Temperatur Sensor auf PCB
    - Externe Sensoren anbinden (Feuchtigkeit, ...)
- I2C Bus
    - Steuerung des port-expander auf PCB
    - Externes Display
- Open-Drain Driver
    - 12V RGB LED Strip ansteuern
- ADC
    - Eingangsspannungs Messung (evtl. für Batterie Betrieb)

## Download

KiCAD Schematic als PDF: 

[ESP12-Evalboard-012-00.pdf](/blog_images/wlan-433mhz-gateway-mit-esp-12/ESP12-Evalboard-012-00.pdf)

µC pin-list as PDF: 

[µC-Pinning-012-00.pdf](/blog_images/wlan-433mhz-gateway-mit-esp-12/µC-Pinning-012-00.pdf)

## Bilder

![Bestückte Leiterplatte](/blog_images/wlan-433mhz-gateway-mit-esp-12/012-00-Assembled1.png)

![433 Mhz RX TX Modul](/blog_images/wlan-433mhz-gateway-mit-esp-12/433MHz-Rx-Tx.jpg)

![Redlabs Gateway Blockdiagramm](/blog_images/wlan-433mhz-gateway-mit-esp-12/ESP12-Blockdiagram.png)

![ESP-12E ESP8266](/blog_images/wlan-433mhz-gateway-mit-esp-12/esp12e-board.png)

![Redlabs PCB-012-00 PCB Layout](/blog_images/wlan-433mhz-gateway-mit-esp-12/PCB-012-00.png)

![Redlabs PCB-012-00 PCB Schaltplan](/blog_images/wlan-433mhz-gateway-mit-esp-12/schematic_esp-12e.png)
