---
title:  "Amature Radio's Future: Delay Tolerant Network"
subtitle: "Technology In Ham Radio"
date:   2020-03-06 00:00:00
description: "I believe the future of ham radio involves delay tolerant networking driven by hobbiest and professional electronics experimenters."
categories: [amateur radio]
tags: [amateur radio, delay tolerant network]
---

The future of amatuer radio is not a new digital mode. The past century of ham radio has been rooted in two fundamental activities, to communicate and to innovate. However, in a world with smartphones, internet, and social media, communication no longer directly between two people or even in real-time! Traditional ham radio activities such as [rag chewing](https://en.wikipedia.org/wiki/Contact_(amateur_radio)), [contesting](https://en.wikipedia.org/wiki/Contesting), [public service events](http://www.arrl.org/public-service), and similar activities are akin to sailing in the 21st century: fun, but not practical. Commercial offerings such as the internet, cell phones, etc… have largely relegated amateur radio to a nostalgic hobby. The commercial industry will always beat amateur radio if there is a market and infrastructure for non-hams.

After 16 years in the hobby I’ve noticed that ham radio has a killer combo: community and [radio spectrum](https://en.wikipedia.org/wiki/Amateur_radio_frequency_allocations). 

* Everyone _wants_ to communicate openly and wants to _help others communicate_. 
* Groups coordinate together to implement a global network of hardware radios ([APRS](https://aprs.fi), [D-STAR](http://www.dstarinfo.com/home.aspx), [Echolink](http://www.echolink.org/)). 
* The hobby has built dozens of satellites orbiting above earth right now, free to use by anyone (with a callsign).
 * [AO-92](https://en.wikipedia.org/wiki/Fox-1D) using a [solar MPPT](https://github.com/FaradayRF/Fox-1-MPPT) designed and built by my brother (KB1LQC), myself (KB1LQD), and our [Rochester Institute of Technology senior design team](http://edge.rit.edu/edge/P13271/public/FinalDocuments/Build_Test_Document/P13271_AMSAT_MPPT_Technical_Report.pdf)

 We have people who coordinate, people that innovate, and we’re spread across the globe in sufficient numbers to create things larger than any single person can achieve. 

I believe the next true advancement within amateur radio will be new technologies that don’t quite fit the normal telecommunications functions but are well suited for the ham radio infrastructure and style of use. 

Consider [delay/disruption tolerant networks (DTN’s)](https://www.nasa.gov/content/dtn), they are primarily used by NASA or within other niche applications such as disaster relief teams to transfer data around a network that by definition is unreliable on the order of seconds to hours. Sending data between rovers, relay satellite(s), and Earth incurs hours of time when no link is possible between all three devices any one moment. DTNs maximize communication between any two devices, leapfrogging data over an impossible real-time network owing to their heritage in [store-and-forward protocols](https://en.wikipedia.org/wiki/Store_and_forward) of the past.

Amateur radio is the perfect medium for this technology. For example, consider a small data radio implementing a DTN being used by a person sending a message out of range of normal ham radio infrastructure (repeater towers). Their message is queued for transmissions but has nowhere to go until another amateur radio operator driving their car along the nearby highway  connects, downloads, and stores the message. When the car passes within range of another amateur radio operators home, which is connected to the internet, it forwards the message via the internet to its destination anywhere in the world. The messages recipient can reply via the same route in reverse.

All of this occurs without needing to build infrastructure removed from the internet but instead leverages the qualities of ham radio with the capabilities of the internet. Remote communication of any type (data is data) with minimum infrastructure. All that is needed is a critical mass of hams in an area using the system and unlike current networks (i.e. APRS) the mobile users actively improve the network for everyone else rather than just post a position or telemetry data themselves. Mobile users provided coverage in otherwise out of range areas.

There will be challenges implementing an open and widespread DTN using amateur radio but they are solvable. Radio hardware does not need to be complicated, implementations can utilize [ISM](https://en.wikipedia.org/wiki/ISM_band) band radio modems. The delay tolerant network’s job is to get the data to the internet where a massive bandwidth exists utilizing the last mile(s) of ham radio to achieve otherwise non-existent capability. This project provides a unique avenue for both operating and leading technological advancement not offered elsewhere. It is also well suited for the experimenters, makers, and those who just want to use a delay tolerant network in the field. 