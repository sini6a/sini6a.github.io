---
layout: post
title: "Internet Radio Speaker: ESP32-C3"
date: 2025-05-07
subtitle: "Design and implementation of a compact ESP32-C3-based internet radio speaker, focusing on embedded constraints, audio streaming limitations, and manufacturable hardware design."
tags: [pcb-design, esp32, audio, i2s, wifi, hardware-design, usb-c, kicad]
---

This project is a compact **internet radio speaker** built around the ESP32-C3. It was designed to solve a very specific problem: reliable, always-available playback of a single radio station without depending on a phone or computer.

The result is a small, purpose-built device that boots directly into playback and is optimized for simplicity, manufacturability, and predictable behavior.

![Internet Radio fully assembled]({{ site.baseurl }}/assets/internet-radio-assets/internet-radio-2.jpg)

## Background and motivation
I have been a long-time listener of a specific radio station from my home country. After moving to Sweden, the only way to listen to it was through a computer or phone, which was inconvenient and easy to forget during work.

Rather than treating this as a software problem, I approached it as an **embedded hardware project**: a dedicated device that performs one task well and requires no user interaction beyond power and volume control.

## Design goals and constraints
From the start, the design was guided by a few non-negotiable constraints:

- Wi-Fi connectivity for internet radio streaming  
- Minimal user interface (power + volume only)  
- Small PCB footprint  
- Good audio quality for near-field listening  
- Fully manufacturable using standard PCB assembly services  

These constraints informed both the hardware and firmware decisions.

## Hardware architecture
The core of the design is the **ESP32-C3**, chosen specifically for its **single-core architecture** and low power consumption. While more powerful ESP32 variants exist, they would have been unnecessary for this use case and would have increased complexity and cost.

Key hardware choices:
- ESP32-C3 module with 32 Mbit flash to reduce external components
- Two MAX98357 I²S class-D audio amplifiers (one per channel)
- Stereo speaker output with sufficient volume for a desktop environment
- Potentiometer with integrated power switch for simple user interaction
- On-board PCB antenna with careful ground and keep-out considerations

Using off-the-shelf I²S amplifiers avoided the need to design a discrete class-D stage, reducing both risk and board size.


![Internet Radio PCB]({{ site.baseurl }}/assets/internet-radio-assets/internet-radio-1.jpg)


## Firmware considerations
The firmware was written specifically for this device and is available on GitHub.

Key points:
- Uses the `arduino-audio-tools` library by Phil Schatzmann for audio handling
- Directly streams internet radio over Wi-Fi
- Optimized for deterministic startup and minimal runtime configuration

A known limitation of the ESP32-C3 is **AAC playback performance**. Due to the single-core MCU and limited processing headroom, some AAC streams cannot be decoded reliably. This limitation was identified during testing and accepted as a design trade-off.

MP3 streams, however, play reliably and without dropouts.


<video controls muted loop playsinline style="width:100%">
  <source src="{{ site.baseurl }}/assets/internet-radio-assets/internet-radio-video-720p.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>



## Manufacturing and cost
The board was designed with manufacturability in mind:
- Highly integrated audio amplifier ICs
- Standard footprints and assembly-friendly layouts
- Impedance-controlled routing for high-speed signals and the on-board Wi-Fi PCB antenna

The most significant cost drivers are the two audio amplifiers, but their use significantly reduces development time and PCB complexity compared to a custom amplifier design.

## Open-source approach
Both the **hardware design files and firmware** are open source and available on GitHub. The project is structured to be easy to modify, extend, or adapt to other radio streams or use cases.

## Key takeaways
This project reinforced several practical lessons:
- Wireless performance is highly sensitive to PCB layout and antenna placement
- Simpler architectures often lead to more reliable products
- Purpose-built devices outperform general-purpose solutions for focused tasks

Overall, this was a valuable exercise in designing a constrained, real-world embedded system from concept to functional hardware.
