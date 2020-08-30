---
title:  "KB1LQD Optical Project Overview"
date:   2020-08-30 00:00:00
categories: [electronics]
tags: [engineering, electronics, communications, radio]
---

Optical communications is an area I've been curious about since my introduction into electronics, from simple AM voice transmissions to digital communications. I built a crude AM LASER TX/RX circuit in high school with my then vague electronics knowledge and circa 2005 online schematics I found online. I'd like to revisit this project with a renewed focus on building from fundamentals of a simple analog transmitter/receiver to a digital Frequency Shift Keying (FSK) design. I want this to be a fun project that I can achieve with an hour or two of spare time over the week as my main effort.

## Project References
The table below contains the project reference links.

| Reference Name | Description | Link |
|---|---|---|
| **GIT HW Repo** | Version controlled GIT repo of the project hardware files | [KB1LQD Optical Comm Project](https://github.com/kb1lqd/optical_comm_1)  |

## Project Milestone Path
This project is expected to achieve several intermediate milestones, each as a building block on the prior. For the first milestone a simplistic goal is expected.

* **Objective**
  * Create a simple AM modulated LED transmitter & receiver that can pass audio through the link

I expect this to encompass either a simple base-band AM or Pulse-Frequency Modulation implementation and allow simple analog audio or audio based digital signal to be passed through link. Brief research indicates directly modulating light via phase shifting offers greatly increased bandwidth but is much more complicated (using direct light modulating mediums such as liquid crystal). Keeping it simple will also allow basic infrastructure such as optical equipment and aiming devices to be created.

Future updates will be explored at a later time. Digital communications is likely easiest just by using audio modulations such as those typical in ham radio (PSK32, FT8, etc...) or more generic data modulations just as Audio Frequency Shift Keying (AFSK) using programs such as mini-modem.

##  Project Plan
I'm going to implement the following workflow within the project to ensure I create the intended hardware. This may be a little intense for a personal project but I intend to keep it light and simple.

1. Requirements Capture
  * Capture the intended project requirements at a high level. This should include interface requirements and functionality.
2. Architectural Design
  * High level block diagram and interface control documentation (ICD) that implements an architectural design that achieves the requirements captured.
  * Additional low-level requirements generated during this step should be captured
3. Detailed Design
  * Circuit designs are created that implement the architectural design
  * Circuit simulations to prove intended operation and requirements are met
  * PCBA designs are created
4. Implementation
  * PCBA's are assembled
  * PCBA checkout testing is performed
  * Functional test the PCBA's


## Requirements

The project requirements are listed below.

### Transmitter

| Req # | Requirement | Rational |
|---|---|---|
| 1 | The transmitter shall implement amplitude modulation at baseband. | Derived |
| 2 | The transmitter shall exhibit at least 4khz of bandwidth | To support voice operations |
| 3 | The transmitter shall accept an input signal from an audio headphone output interface | Use of a computer headphone jack to provide source signals into the transmitter|
| 4 | The transmitter shall accept an input signal from a microphone interface | Use of an external microphone to provide source signals into the transmitter|
| 5 | The transmitter shall be powered from a 5V +/-250mV source | USB power |

### Receiver

| Req # | Requirement | Rational |
|---|---|---|
| 1 | The receiver shall implement amplitude modulation at baseband. | Derived |
| 2 | The receiver shall exhibit at least 4khz of bandwidth | To support voice operations |
| 3 | The receiver shall output demodulated signals from an audio headphone output level interface | Monitor headphone output|
| 4 | The receiver shall output demodulated signals from a microphone output level interface | Output provided for computer microphone input interface|
| 5 | The receiver shall be powered from a 5V +/-250mV source | USB power |


## Architectural Design

I performed the architectural design implementing both the transmitter and receiver on a single assembly.

<img src="/images/kb1lqd_optical_comm_1/architecturaldesign.svg" alt="Block diagram architectural design of the optical transmitter/receiver."/>

The interfaces generated while implementing the architecture design are shown below. Note that I added an additional parallel receiver monitoring output to provide a means to both listen manually to a received signal and monitor into a computer (for processing/recording if desired.)

| Interface | Description |
|---|---|
| PWR.5V.IN | 5V +/-250mV power input for the assembly |
| AUDIO.MIC.IN | External audio microphone input source interface that can be selected as the transmitter input signal source.|
| AUDIO.SPK.IN | External speaker level input source interface that can be selected as the transmitter input signal source. This is intended to be directly connected to a headphone speaker output jack. |
| EXTDETECTOR.IN | External optical detector input interface. It is expected that the external detector contains local buffering/amplification.|
| LEDBIAS.OUT | External output interface used to connect an external LED to be driven as a transmitter.|
| RX.AUDIO.OUT0 | External headphone/line-in audio output 0.|
| RX.AUDIO.OUT1 | External headphone/line-in audio output 1.|
