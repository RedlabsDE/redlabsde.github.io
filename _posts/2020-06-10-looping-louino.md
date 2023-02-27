---
title: Looping Louino
categories: ['Digital']
tags: ['arduino', 'atmega328', 'looping loui'] #always lower case
image:
    path: /blog_images/looping-louino/PCB-013-00-1-1024x592.png
date: 2020-06-10T16:55:33.615Z
author: julian
---

Unsere Looping Loui Erweiterung. Der ATMega328P-AU übernimmt alle wichtigen Aufgaben vom User Input über die Motor Steuerung bis zur LED Ansteuerung.

## Features

* Programme: Normal / SpeedUp / Random / Remote/ MaxSpeed
* Programm und Richtungsanzeige mit RGB LEDs
* Vorwärts & Rückwärts in variabler Geschwindigkeit
* 5-Spieler Modus: Loui selbst steuern
* Firmware via Arduino Bootloader updaten und anpassen

## Hardware Funktionen

Der **ATMega328P-AU** übernimmt alle wichtigen Aufgaben vom User Input über die Motor Steuerung bis zur LED Ansteuerung. Der µC kann per Atmel ISP programmiert werden und/oder mit Hilfe des Arduino Bootloaders. Die UART Schnittstelle ist über die Klinkenbuchse auch im verbauten Zustand bequem zu benutzen.

Als Motor Treiber wird die voll integrierte MOSFET H-Bridge **ZXMHC6A07T8-2** eingesetzt. Durch Messung der Motor Spannung und des Motor Stroms, kann auf die "I/O"-Schalter Stellung geschlossen werden. Der Schalter ist wie im Orginal LoopingLoui in Reihe mit dem Motor geschalten.

Für die Beleuchtung bzw. Programm- und Richtungsanzeige sorgt ein Stück eines **WS2811 LED Strip** mit 11 LEDs. Die Programm Auswahl erfolgt über einen **Pushbutton**.

Um die Richtung und Geschwindigkeit selbst zu steuern, kann an der **Klinkenbuchse** ein externes Poti angeschlossen werden. (Hier zum Beispiel ein **Joystick** aus einer alten Flieger Fernsteuerung)

Die Versorgungsspannung (7.5VDC über einen **Hohlstecker**) wird vom DC/DC Step-Down Wandler **MP1584** auf 5V geregelt um den µC sowie die LEDs zu versorgen.

## Technische Infos

[Schaltplan 013/00-02 (.PDF)](/blog_images/looping-louino/loopinglouino-schematic-013-00-02.pdf)

[Fertigungszeichnung 013-00-FFAB (.PDF)](/blog_images/looping-louino/013-00-ffab.pdf)

Das Layout ist offen und die PCB kann hier bei [Aisler (externer Link)](https://aisler.net/p/MKIYMUSK) bestellt werden.

## Bilder

![Motor + Schalter Verkabelung](/blog_images/looping-louino/20181001_194858-1024x614.jpg)

![PCB im Batteriefach](/blog_images/looping-louino/20191121_122007-1-1024x614.jpg)

![von unten](/blog_images/looping-louino/20191204_103417-1-1024x614.jpg)

![Fertiges Looping Loui mit Netzteil und Fernsteuerung](/blog_images/looping-louino/20191204_103528-1-1024x614.jpg)

![PCB 013/00 vor dem verlöten](/blog_images/looping-louino/PCB-013-00-1-1024x592.png)

## DIY - Looping Loui Upgrade

#### 1. PCB und alle benötigten Bauteile beschaffen

* Redlabs PCB
* Bauteile (siehe Schaltplan / BOM folgt...)
* WS2811 LED Strip mit 11 LEDs
* Steckernetzteil mit 7.5V DC
* ein paar Kabel, Heißkleber, Bohrer und Geduld
* Optional: Externes Poti zur Fernsteuerung + Klinkenkabel

#### 2. PCB auflöten

Die richtigen Bauteile für die PCB findet ihr in der BOM. Auf der 013-00-FFAB Zeichnung finden sich die Position und Orientierung der Bauteile.

#### 3. Firmware programmieren und testen

Entweder mit dem Atmel ISP Programmieren oder mit dem Arduino Bootloader.

#### 4. Looping Loui bearbeiten

Das Unterteil wird aufgeschraubt und die beiden Motor&Schalter Anschlusskabel so verlängert, dass sie später bequem an die PCB gesteckt werden können.

Im Batteriefach wird Platz für die PCB gemacht: Boden des Fachs entfernen und Löcher für den Hohlstecker, den Pushbutton und die Klinkenbuchse bohren.

Der WS2811 LED Strip wird so in das Unterteil verklebt, dass die LEDs nach außen zeigen und je 3 LEDs pro Seite sichtbar sind.

#### Optional: Fernsteuerung

Um Loui selbst steuern zu können muss über die Klinkenbuchse ein externes Poti angeschlossen werden. Am besten eignen sich hier Teile einer alten RC-Fernbedienung.

#### 5. Anschließen, Testen, Los fliegen ...
