---
title: NMOS Nano Board
categories: ['Analog']
tags: ['amplifier'] #always lower case
image:
    path: /blog_images/nano-3ch-n-mos-board/20180712_183157.jpg
date: 2018-07-16T00:00:00.000Z
author: julian
---

Mit dem super kleinen 3-Kanal _NMOS Nano Board (016/00)_ lassen sich einfach und Platz sparend kleinere DC Lasten schalten. Angesteuert wird das Board via µController (Arduino, ...) GPIO bzw. PWM.

* * *

## Beschreibung & Spezifikation

Auf dem Board befinden sich 3 Open-Drain Schaltungen um den N-MOSFET [IRLML6244.](https://www.infineon.com/dgdl/irlml6244pbf.pdf?fileId=5546d462533600a4015356686fed261f)

- Maximale Betriebs-Spannung **V\_DS\_max: 20V DC**
- Kleiner Drain-Source Widerstand **R\_DS\_on: 21 mΩ**
- Kompatibel zu 3.3V & 5V Systemen **V\_GS\_th <2.5V**
- Ansteuerung via **GPIO / PWM**
- PCB Maße **15mm x 20mm**

[Schaltplan als PDF](/blog_images/nano-3ch-n-mos-board/016-00-NMOS-nano-Board-Schematic.pdf)

* * *

## Beispiel #1:  12V-RGB Strip dimmen mit Arduino

1. _NMOS Nano Board_
2. LED Strip
3. Arduino Board (nano/mini)
4. 12V Netzteil
5. Kabel

Es werden nur die aufgeführten Komponenten benötigt, keine weiteren Bauteile. Der 12V (RGB) LED Strip kann direkt auf die _NMOS Nano Board_ PCB gelötet werden. Die Pins "Gate1, Gate2, Gate3" werden mit beliebigen Pins des Arduinos verbunden, wenn gedimmt werden soll müssen die Arduino Pins mit "PWM pin" gekennzeichnet sein. Mit den 12V wird das Arduino Board (Pin "VIN") und das _NMOS Nano Board_ versorg (Pin "V+").

Fertig. Jetzt können über 3 Arduino Pins die Farben Rot/Grün/Blau gesteuert werden.

 

## Bilder

![](/blog_images/nano-3ch-n-mos-board/016-00-application1.png)
![](/blog_images/nano-3ch-n-mos-board/016-00-Dimensions.jpg)
![](/blog_images/nano-3ch-n-mos-board/20180712_183157.jpg)
