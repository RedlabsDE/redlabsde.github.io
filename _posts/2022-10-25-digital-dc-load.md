---
title: Digital Controllable DC Load
categories: ['Digital']
tags: ['i2c', 'controllable current sink', 'constant current sink', 'dc load', 'arduino', 'digital'] #always lower case
image:
    path: https://github.com/RedlabsDE/Digital-DC-Load/raw/main/documentation/PCB-raw.jpg
    alt: PCB assembled
date: 2022-10-25T13:50:56.855Z
author: julian
---

**Project key features:**
- linear constant curren sink
- galvanic isolated
- selectable operating range (high/low current/voltage)
- controlled via I2C
	- write & read load current
	- read load voltage
	- read additional external voltage
	- read temperature
- manual option: set current via external voltage (or potentiometer)

**Example application:**
- charge / discharge battery (control & measure current and voltage)
- measure & log current/voltage (use example setup to send data to PC)
- stess test of power supply

![Blockdiagram of example usecases](https://github.com/RedlabsDE/Digital-DC-Load/raw/main/documentation/CCS-Example-Usecases.png "Example Usecases")


[Open Github Repository](https://github.com/RedlabsDE/Digital-DC-Load)
