---
layout: post
title: "Pocketboard: compact keyboard PCB design with real-world constraints"
date: 2026-01-10 10:00:00 +0100
categories: [hardware, pcb]
tags: [pcb-design, kicad, usb-c, mechanical-keyboard, embedded]
subtitle: "Design notes from developing a compact mechanical keyboard PCB, focusing on layout constraints, manufacturability, and reliability."
---

Pocketboard is a compact mechanical keyboard project where the goal was **not novelty**, but **engineering discipline**: a small form factor designed with realistic electrical and mechanical constraints in mind.

This project reflects how I approach hardware design when size, usability, and reliability all matter.

## Design constraints
From the start, the main constraints were:
- Pocket-friendly dimensions without sacrificing switch spacing
- Reliable USB-C connectivity (data + power)
- Clean matrix routing with minimal compromises
- PCB manufacturability using standard fabrication services

Every design decision was evaluated against these constraints rather than aesthetics alone.

## PCB layout strategy
The PCB was designed using a bottom-up approach:
- Mechanical constraints defined first (switch footprint, connector placement)
- Electrical constraints next (matrix routing, ground reference)
- Finally, manufacturability (trace widths, spacing, solderability)

Special care was taken to avoid routing shortcuts that would make debugging or future revisions harder.

## Lessons learned
- Compact boards amplify small mistakes — tolerances matter
- Mechanical anchoring of connectors is just as important as electrical correctness
- Designing for assembly saves more time than optimizing routing density

## What I would improve in the next revision
- Additional test pads for faster bring-up
- Improved strain relief for USB-C
- Slightly relaxed routing in non-critical areas for better yield
