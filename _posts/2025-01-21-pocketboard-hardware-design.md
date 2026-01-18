---
layout: post
title: "Pocketboard: Compact Keyboard PCB Design"
date: 2025-01-21
tags: [pcb-design, kicad, usb-c, keyboard, rp2040, qmk]
subtitle: "Design notes from developing a compact keyboard PCB, focusing on layout constraints, manufacturability, and reliability."
---

Pocketboard is a compact, standalone keyboard designed for portable, on-the-go use. The project is inspired by the **HandiPi** keyboard by BrickBots, but redesigned from the ground up with a focus on **modern components, surface-mount assembly, and real-world usability**.

The keyboard uses a **36-key Miryoku-inspired layout** and provides full keyboard functionality in a form factor small enough to be carried in a pocket, tool bag, or car. Despite its size, Pocketboard is designed to behave like a fully featured USB keyboard suitable for terminal access, configuration tasks, and general input when working away from a standard workstation.

<!-- IMAGE 1: Assembled Pocketboard (hero image) -->
![Pocketboard assembled keyboard]({{ site.baseurl }}/assets/pocketboard_assets/pocketboard_1.jpg)

---

## Inspiration and Goals

The original motivation behind Pocketboard was the need for a **reliable, always-available input device**. While full-size or split keyboards offer excellent ergonomics, they are often forgotten or impractical to carry at all times.

The design goals were therefore:
- Minimize size while retaining practical usability
- Use **only SMD components** to simplify assembly and reduce board thickness
- Select a **modern MCU with strong ecosystem support**
- Add optional **LCD support** for feedback and diagnostics
- Use **USB Type-C** for power and data to ensure cable availability

The result is a small but capable device that can be kept close at hand and used whenever a keyboard is needed, without relying on built-in laptop keyboards or external peripherals.

---

## Hardware Design Choices

The board is built around the **RP2040**, selected for its performance, availability, and strong open-source ecosystem. It is paired with **128 Mbit of external flash**, allowing room for advanced firmware features, graphics for the LCD, and experimental functionality.

A **1.96” LCD** is included to provide visual feedback such as pressed keys, status information, or simple animations. The display can be hidden behind a custom 3D-printed enclosure for a more discreet appearance if desired.

For connectivity, **USB Type-C** was chosen for long-term compatibility and ease of use. The design includes **ESD protection** on the USB interface to improve robustness and protect sensitive components during handling and everyday use.

For the keys, **1.8 N tactile push buttons** were selected to provide clear feedback while maintaining a compact footprint.

<!-- IMAGE 2: PCB top view or KiCad render -->
![Pocketboard PCB layout]({{ site.baseurl }}/assets/pocketboard_assets/pocketboard_2.jpg)

---

## Firmware Integration

Pocketboard ships with firmware based on **QMK**, providing a stable and well-understood foundation for keyboard functionality.  
QMK enables features such as:
- Layers and custom key mappings
- Home-row modifiers
- LED control
- Integration with the LCD for user feedback

The RP2040 also allows experimentation with alternative firmware solutions if desired, making the platform flexible for further development or customization.

---

## Manufacturing Considerations

The PCB was designed with **manufacturability in mind**. Trace widths, via sizes, and component placement were kept within comfortable margins to avoid unnecessary manufacturing complexity.

While the RP2040 package introduces a relatively fine pitch, this was considered an acceptable trade-off given current industry trends, where many modern MCUs use similar or smaller footprints.

The first production run consisted of **100 units**, intended both for real-world use and to allow others to study, modify, and experiment with the design.

<!-- IMAGE 3: Partially assembled board or close-up -->
![Pocketboard assembly detail]({{ site.baseurl }}/assets/pocketboard_assets/pocketboard_3.jpg)

---

## Open-Source Approach

Pocketboard is fully **open source**, with both hardware design files and firmware available on GitHub. The project is intended not only as a usable product, but also as a learning platform for others interested in compact embedded hardware design, USB devices, and keyboard firmware.

Users are free to modify the hardware, port alternative firmware, or develop their own software from scratch.

---

## Conclusion

Pocketboard was a rewarding project that combined **embedded hardware design, PCB layout, firmware integration, and manufacturability considerations** into a single compact product.

Special thanks to **BrickBots** for the original HandiPi project, which served as the foundation and inspiration for this design.  

Contributions, feedback, and experimentation are always welcome.
