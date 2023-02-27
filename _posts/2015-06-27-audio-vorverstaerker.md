---
title: Audio Vorverstärker + Klangregelung
categories: ['Analog']
tags: ['amplifier'] #always lower case
image:
    path: /blog_images/audio-vorverstaerker/PreAmp-Schematic.png
    alt: Als Erweiterung zur Musik-Kiste wurde ein Stereo Vorverstärker mit Klangregelung auf Basis des Applikationsbeispiels des Operationsverstärkers TL082 entworfen.
date: 2015-06-27T00:00:00.000Z
author: julian
---


Als Erweiterung zur [Musik-Kiste](/blog/musik-kiste/) wurde ein Stereo Vorverstärker mit Klangregelung auf Basis des Applikationsbeispiels des Operationsverstärkers [TL082](http://www.ti.com/lit/ds/snosbw5c/snosbw5c.pdf) entworfen.

Modifiziert und neu dimensioniert stellt die Schaltung eine Vorverstärkung (+8dB) und eine aktive Klangregelung (±4dB) bereit.

- - -

## Dimensionierung der Schaltung

Um den Vorverstärker sinnvoll zu dimensionieren wurde zunächst die maximale Amplitude gängiger Audio-Quellen gemessen. Angegeben wird die Spitze-Spitze Spannung Vpp.

* iPhone: ca. 1.2Vpp
* Laptop: ca. 2.0Vpp (Ue_max)

Die maximale Ausgangsspannung(Ua_max) des verwendeten Operationsverstärker liegt bei ca. 9.6Vpp. Bei einer Verstärkung über diese Spannung übersteuert der OPV und das Signal wird verzerrt! Mit den beiden Spannungen Ue_max=2.0V und Ua_max=9.6V ergibt sich eine absolute maximale Verstärkung von:

**Gain_abs = Ua/Ue = 4.8 ⇒ +13.6dB**

Um den OPV nicht an der Grenze des verzerrungsfreien Bereichs zu betreiben wird mit einer sicheren maximalen Verstärkung von **Gain_max = +12dB** weiter geplant.

Die maximale Verstärkung teilt sich auf in eine konstante Vorverstärkung und die maximale Verstärkung der aktiven Klangregelung. Für die **Vorverstärkung** werden **ca. +8dB** geplant. (Bild: "Bass & Treble normal")

Somit ergibt sich eine **maximale Anhebung der Tiefen/Höhen** um **+4dB**. (Bild: "Bass & Treble maximal angehoben")

Die Schaltung wurde in LTspice aufgebaut und simuliert. Die wichtigsten Frequenzgänge sind als Bilder angehängt, die Bezeichnung Bass&Treble angehoben/abgesenkt beziehen sich auf die Stellungen der Potentiometer aus R3/R6 (Bass) und R14/R15 (Treble).

**Das LTspice Modell:**

[Download PreAmpV2.asc](/blog_images/audio-vorverstaerker/preampv2.asc)

- - -

## Schaltungsbeschreibung

Da die Schaltung für ein Stereo-Audiosignal ausgelegt ist und somit aus zwei identischen Teilen besteht, beziehen sich die folgenden Bauteilbezeichnungen nur  auf den oberen Teil des Schaltplans. Alle Bezeichnungen beziehen sich auf den KiCAD Schaltplan (als PDF und Bild angehängt).

**Der KiCAD Schaltplan als PDF:** 

[Download StereoPreAmp.pdf](/blog_images/audio-vorverstaerker/stereo_pre_amp.pdf)

### Spannungsversorgung

Die Schaltung wird mit 12VDC aus einem Blei-Akku versorgt. Um Störungen durch den internen Laderegler der [Musik-Kiste](/blog/musik-kiste/) zu unterdrücken ist die Spannungsversorgung mit einem RLC Tiefpass versehen.

### Gleichspannungsentkopplung / Hochpass

Da die Schaltung asymmetrisch (+12V) versorgt wird, muss für die Operationsverstärker eine virtuelle Masse erzeugt werden. Diese wird mit dem Spannungsteiler R9/R10 auf 6V festgelegt und mit C6 gestützt.

Das Eingangssignal (an K1) wird zunächst mit C2 Gleichspannungs-entkoppelt und über R6 der virtuellen Masse (V/2) überlagert. Die Eingangsbeschaltung (C2/R6) stellt zudem einen RC-Tiefpass dar.

### Vorverstärker

Mit U1A findet eine Wechselspannungs-Verstärkung von Gain = 1+(R12/R8) = 2.47 **⇒** **+7.9dB** statt. Durch den Kondensator C10 wird die Gleichspannungsverstärkung unterdrückt. Die Unterdrückung von Gleichspannung ist notwendig, da sich der Ruhepegel des Eingangssignal auf 6V (virtuelle Masse) befindet. Eine Gleichspannungsverstärkung würden beuten, dass bereits in Ruhe eine Übersteuerung des Operationsverstärkers stattfindet (6V*2.4 = 14,4V ). Verstärkt werden darf also nur die Auslenkung aus dem Ruhepegel.

Verhalten Gleichspannung:

* C10 stellt einen Leerlauf dar
* R8 ist wirkungslos
* OP wird zum Impedanzwandler
* Gain = +1

###  Aktive Klangregelung

Die Klangregelung wurde in LTspice simuliert und auf den gewünschten Wert von ca. ±4dB gebracht. Mit den Potenziometern RV2 und RV3 erfolgt die Einstellung der Tiefen/Höhen Regelung. Dabei entspricht ein Anschlag der Potentiometer an Pin 3 einer maximalen Verstärkung und ein Anschlag an Pin 1 einer maximalen Dämpfung.

### Lautstärke Regler

Die Lautstärker Regelung übernimmt ein logarithmisches 10k Stereo-Potentiometer am Ausgang der Schaltung.

- - -

## Layout und Aufbau

Das einseitige Platinen Layout wurde mit KiCAD erstellt. Die äußeren Abmessung sowie die Befestigungsbohrungen sind an den Class-D Verstärker der [Musik-Kiste](/blog/musik-kiste/) angepasst. Der Vorverstärker kann so platzsparend auf dem Class-D Verstärker montiert werden und an die doppelt ausgeführten Schraubklemmen der Spannungsversorgung des Vorverstärkers mit angeschlossen werden.

- - -

## Erfahrungen / Erweiterungen

Die Schaltung ist aufgebaut (Bilder folgen) und läuft seit Mitte Juni '15 zufriedenstellend in der [Musik-Kiste](/blog/musik-kiste/).

Zum Test des Vorverstärkers sowie der Gesamten [Musik-Kiste](/blog/musik-kiste/) wurde u.a. der [Online-Tonegenerator](http://onlinetonegenerator.com/) benutzt.

![Output-Bh-Th](/blog_images/audio-vorverstaerker/Output-Bh-Th.png "Output-Bh-Th")

![Output-Bl-Tl](/blog_images/audio-vorverstaerker/Output-Bl-Tl.png "Output-Bl-Tl")

![Output-Bm-Tm](/blog_images/audio-vorverstaerker/Output-Bm-Tm.png "Output-Bm-Tm")

![Output-Bm-Tm](/blog_images/audio-vorverstaerker/Output-Bm-Tm.png "Output-Bm-Tm")
