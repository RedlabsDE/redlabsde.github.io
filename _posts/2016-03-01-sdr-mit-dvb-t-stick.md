---
title: SDR mit DVB-T Stick
categories: ['Digital']
tags: ['music', 'battery charger'] #always lower case
image:
    path: /blog_images/sdr-mit-dvb-t-stick/stick-dvb-t-sdr.png
    alt: Unter Software Defined Radio (SDR) fasst man Konzepte für Hochfrequenz-Sender und -Empfänger zusammen, bei denen kleinere oder größere Anteile der Signalverarbeitung mit Software verwirklicht werden. Wir verwenden einen RTL2832U...
date: 2016-03-01T00:00:00.000Z
author: nico
---

Unter Software Defined Radio (SDR) fasst man Konzepte für Hochfrequenz-Sender und -Empfänger zusammen, bei denen kleinere oder größere Anteile der Signalverarbeitung mit Software verwirklicht werden. Als günstiger Einstieg in die Welt von SDR kann man einen einfachen DVB-T Dongle verwenden. Ich habe [diesen günstigen DVB-T Stick](http://amzn.to/1WT1VSH) in verwendung. Er besitzt einen RTL2832U Demodulator von der Firma Realtek. Ich habe mir ein bisschen damit rum gespielt und ein paar interessante Software Programme und Anwendungsmöglichkeiten herausgesucht die ich euch hier kurz näherbringen möchte.

[![USB Stick SDR RTL2832U Chip](/blog_images/sdr-mit-dvb-t-stick/stick-dvb-t-sdr-e1456822179998-300x117.jpg)](http://amzn.to/1WT1VSH)

## Flight Radar 24 (ADS-B Signal)

![GlobeSScreenShot](/blog_images/sdr-mit-dvb-t-stick/GlobeSScreenShot-220x220.png)
Viele von euch kennen sicherlich https://www.flightradar24.com/, hier wird der Live Air Traffic als Website dargestellt. Ein großteil der Daten werden von sogenannten [ADS-B](https://en.wikipedia.org/wiki/Automatic_dependent_surveillance_%E2%80%93_broadcast) empfängern am Boden empfangen und an den Server von FR24 weitergeleitet. Jedes Verkehrsflugzeug sendet ein ADS-B Signal unverschlüsselt aus dieses enthält unter anderem Informationen über Position, Flughöhe, Geschwindigkeit, Flugnr, Squawk und vielen mehr. Das Signal wird auf einer Frequenz von 1090 Mhz gesendet welches unser SDR empfangen und auswerten kann. Wenn ihr FR24 dabei helft noch mehr informationen zu sammeln bekommt ihr als belohnung (schon nach wenigen stunden) einen kostenlosen Premium Account. Hier bekommt ihr die Software und weitere Informationen zum Angebot von FR24 ([https://www.flightradar24.com/share-your-data](https://www.flightradar24.com/share-your-data)). Wenn ihr das ganze mal lokal bei euch ausprobieren wollt ohne die Daten der allgemeinheit zur Verfügung zu stellen kann ich euch die Software "[RTL1090](http://rtl1090.web99.de/)"  zum empfangen und "[Globae-S RTL1090](http://rtl1090.web99.de/homepage/index.php?way=1&site=READOUT&DERNAME=Globe-S%20RTL1090&dm=rtl1090&USER=rtl1090&goto=1&XURL=&WB=1&EXTRAX=X&PIDX=104245)" zur Visualisierung ans Herz legen.

## Satelliten "abhören"

![radio-control](/blog_images/sdr-mit-dvb-t-stick/radio-control.png)Es gibt Amateur Satelliten deren Signal Protokolle öffentlich dokumentiert sind. Wenn man diese auswertet erhält man Informationen über z.b. aktuelle Telemetriewerte wie Lage, Temperatur, Solarenergie usw. Dar diese Signale sehr schwach sind benötigt man eine bessere Antenne als die mitgelieferte. Empfohlen wird eine Yagi Antenne. Diese Besitzen wir leider noch nicht und konnten das Projekt daher noch nicht umsetzen. Vielleicht zu einem späteren Zeitpunkt. Um die genaue Position eines solchen Sateliten zu bestimmen benötigt man die Satellitenbahnelemente dieser werden meist als Two Line Elements (TLE) veröffentlicht. Mit der kostenlosen Software [Orbitron](http://www.stoff.pl/) von Sebastian Stoff kann man die Position sehr einfach ermitteln. Falls du die Position selber mit Hilfe einer Library berechnen möchtest um z.B. eine Antenne automatisch nach zu führen empfehle ich dir [SGP4](https://www.danrw.com/sgp4/) diese ist gut dokumentiert und erhält gute beispiele im Netz.

## Radio Hören (AM/FM - Demodulation)

![old-radio](/blog_images/sdr-mit-dvb-t-stick/old-radio.png)

Mit der kostenlosen Software SDR# von http://airspy.com/ könnt ihr frei alle Frequenzen mithören. Wenn man nun das Programm auf Modulation FM und die Frequenz auf einen Lokalen Radio Sender einstellt hat man ein günstiges Computer/Laptop AM/FM Radio.

**WICHTIG:** 

Der Erwerb, Besitz und die Benutzung von Funkscannern in Deutschland ist grundsätzlich legal. Allerdings dürfen Sie damit nicht die Frequenzbereiche des BOS-Funks abhören oder gehörte Informationen weitergeben, da dies eine Straftat darstellt.
