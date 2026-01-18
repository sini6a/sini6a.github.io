---
layout: post
title: "PHNX Keyboard: ergonomic split keyboard"
date: 2024-04-28
subtitle: "Technical design notes from developing PHNX, a 54-key ergonomic split mechanical keyboard, focusing on matrix design, USB reliability, firmware constraints, and manufacturable PCB layout."
tags: [hardware-design, pcb-design, keyboard, qmk, atmega32u4, usb-c, ergonomics, kicad]
---

PHNX is a custom **ergonomic split mechanical keyboard** featuring **54 MX-compatible switches** with **per-key addressable RGB LEDs**. The design is based on the **ATmega32U4**, a widely used and well-supported MCU in the custom keyboard community, and uses **USB Type-C** for modern and reliable connectivity across devices.

![PHNX assembled keyboard]({{ site.baseurl }}/assets/phnx_assets/phnx_3.jpg)

---

## Inspiration
The keyboard layout is inspired by **Miryoku**, which differs significantly from traditional staggered layouts originating from typewriter-era mechanical constraints.

Unlike legacy layouts, Miryoku emphasizes:
- Symmetry
- Reduced finger travel
- Active thumb usage

On standard keyboards, thumbs are largely underutilized. Miryoku addresses this by assigning important functions to thumb keys, improving efficiency and reducing finger strain. This project was an opportunity to explore how such a layout behaves when paired with custom hardware and firmware.

---

## Hardware design choices
The keyboard uses an **ATmega32U4 MCU**, which operates directly from **5V USB power**, eliminating the need for an additional voltage regulator. This simplifies the power design and integrates well with **addressable RGB LEDs**.

Key hardware considerations:
- **SK6812 Mini-E RGB LEDs** for per-key lighting
- MX-compatible switch footprints for maximum switch and keycap compatibility
- Exposed **ISP header** for bootloader recovery and low-level debugging
- Careful routing to avoid interference between the matrix, RGB data, and USB signals

![PHNX PCB]({{ site.baseurl }}/assets/phnx_assets/phnx_2.jpg)

---

## Firmware integration
PHNX runs **QMK firmware**, which is the de-facto standard for custom mechanical keyboards.

Firmware features include:
- Fully programmable layers and macros
- RGB control and layer indication
- Support for **VIA**, enabling live key remapping without reflashing

The keyboard supports entering the bootloader using a **QMK Magic Key**, allowing firmware flashing without opening the case. This greatly improves usability during development and iteration.

---

## Manufacturing considerations
The PCBs were manufactured and sponsored by PCBWay.

Manufacturing-related decisions:
- The main cost driver is **PCB size**, as each half is implemented as a single board
- USB-C footprint tolerances required careful attention during layout
- All passive components are **0603 or larger**, making the board suitable for hand soldering

The design balances manufacturability with flexibility for prototyping and small-batch production.

---

## Open-source approach
As with all my hardware projects, **both hardware and firmware are open source**.

The repository includes:
- KiCad schematics and PCB files
- Manufacturing outputs
- QMK firmware configuration

Contributions, modifications, and improvements are welcome via GitHub.

---

## Conclusion
Working with the **ATmega32U4** was a valuable experience due to its mature tooling, predictable USB behavior, and strong firmware ecosystem.

This project provided hands-on experience with:
- USB power and signaling considerations
- Addressable RGB LED integration
- Manual assembly and rework of densely populated PCBs

PHNX represents a complete custom keyboard project where **electrical design, firmware integration, and mechanical considerations were treated as a unified system**.


![PHNX assembled keyboard]({{ site.baseurl }}/assets/phnx_assets/phnx_1.jpg)

