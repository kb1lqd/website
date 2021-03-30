
---
title:  "Building A Magnetic Loop Antenna"
date:   2021-03-29 00:00:00
categories: [amateur radio]
tags: [ham radio, antenna, homebrew, radio]
---
During the 2020 COVID-19 pandemic I decided to dive back into the world of amatuer radio, building a workbench/ham radio "shack", and building a few antennas to get on the air. I live in a fairly urban area of Mountain View, CA with limited antenna options at my apartment. Horizontal wire antennas perform poorly low to the ground and it'd be difficult to erect a vertical antenna without getting my landlords permission which landed me at ["Magnetic Loop" antennas](https://en.wikipedia.org/wiki/Loop_antenna). I've always wanted to build one! It was time to grab some tools and start cutting copper pipes. 

This antenna tunes between the 10m (10MHz) through 15m (21MHz) ham bands and can handle up to 20W of power. I used a stepper motor and gearing to allow remote tuning via a Raspberry Pi.

<img src="/images/2021-03-29-magnetic-loop-antenna/Loop-Photo-1.jpg" alt="KB1LQD's homebuilt 10 meter through 15 meter ham radio magnetic loop antenna."/>

This is not a detailed how-to article but I will provide helpful links and insight I discovered during this design/build.

## References

There are many resources online about magnetic loop, A.K.A Small Transmitting Loop (STL) antennas. Additionaly, there is a lot of misinformation including some in very popular resources listed below. Ultimately a mix-and-match will fill in most details and key tradeoffs. It's an antenna and there's no black-magic RF noise filtering involved.

* [www.66pacific.com Small Transmitting Loop Calculator](https://www.66pacific.com/calculators/small-transmitting-loop-antenna-calculator.aspx)
* [Non-Stop Systems Magnetic Loop](https://www.nonstopsystems.com/radio/frank_radio_antenna_magloop.htm)
* [W8JI Magnetic Loop Analysis](https://www.w8ji.com/magnetic_receiving_loops.htm)
  * This is a great in-depth technical resource & it's classic ham-radio web 1.0 HTML!


## Antenna Design

I set off to design this antenna by hand using online resources and the ARRL Antenna Handbook but life had other plans. Wanting use this project to learn FreeCAD designing the brackets and to get on the air I opted to just use the great [www.66pacific.com](https://www.66pacific.com/calculators/small-transmitting-loop-antenna-calculator.aspx) STL antenna calculator.

This online calculator is self-explainitory and informative, I got the information needed to support the frequencies I wanted and purchase a suitable capacitor that can handle the high voltage expected. STL's are a more exotic antenna from the common (electic) dipole antenna creating 1000's of volts and 10's of Amperes with just 20 Watts of RF power.

## 3D Printed Bracket Design

I used this project to learn the basic of [FreeCAD](https://www.freecadweb.org/) mechanical CAD software. 3D printing made attaching the copper piping, coupling loop, and capacitor tuning enclosure easy! I had not used mechanical CAD tools prior so after a bit of riding the struggle bus, working through tutorials, I wrapped my head around parametrically creating components. My design files improve incrementally with the latter (coupling loop bracket) employing FreeCAD spreadsheet relationship dimensions allowing easy changes to the features and dimensions of the part.

<img src="/images/2021-03-29-magnetic-loop-antenna/3D-CAD-Overview.png" alt="Overview 3D CAD model of the major copper tube mounting brackets"/>

<img src="/images/2021-03-29-magnetic-loop-antenna/3D-CAD-Bottom-Copper.png" alt="3D CAD model of the bottom copper pipe mounting bracket"/>

<img src="/images/2021-03-29-magnetic-loop-antenna/CAD-Spreadsheet.png" alt="Relationship parametric modeling in FreeCAD."/>

<img src="/images/2021-03-29-magnetic-loop-antenna/Coupling-Loop-Bracket.png" alt="3D model of the completed coupling loop bracket."/>


### Key Components

* 1/2" copper water pipe
* 15-120pf 2.8KV air variable butterfly capacitor (RFParts 73-175-17)
* 2 1/2" Schedule 40 PVC (Mast)
* 3D Printed PVC mounting brackets (designed using FreeCAD)
* Polycase WA-44 enclosure
* Raspberry Pi 3
* Adafruit DC and Stepper Motor HAT