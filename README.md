# ThinkPad T430 Ultrabay Companion Core

A modular co-processor module designed to slot directly into the Ultrabay of a ThinkPad T430. It leverages the bay’s SATA power line to run a Raspberry Pi Zero (or similar compute module), enabling the laptop to offload auxiliary tasks to a dedicated embedded system.

## 🔧 What It Does

The **Ultrabay Companion Core** adds an embedded secondary system to your T430 by re-purposing the Ultrabay as a power and communication interface. This allows your laptop to interact with a Pi-based co-processor for automation, networking, data logging, or experimentation — all from a hot-swappable module that fits flush with the chassis.

### Example Use Cases
- Running `cron` jobs or Linux daemons independently of the host OS
- Serving a web dashboard for local scripts or temperature monitors
- Setting up a portable Pi-hole or DNS tunneler
- SSH-accessible embedded system for parallel tasks
- Local AI inference module (e.g., whisper.cpp, llama.cpp)

## 🔌 Power & Communication

| Feature              | Detail                                             |
|----------------------|----------------------------------------------------|
| **Power Source**     | 5V SATA line from the T430 Ultrabay (Pin 7)        |
| **Power Regulation** | Optional onboard LDO/SMPS to ensure stable 5V 2A   |
| **Data Link**        | USB passthrough (via SATA to USB board or cable)   |
| **Alt Interfaces**   | UART / I²C breakout for GPIO-level communication   |

The ThinkPad Ultrabay includes a **5V SATA power line**, originally intended for optical drives. We'll tap into that line to power the Pi Zero or similar SBC. Power draw will be limited (~1–1.5A max) to ensure it doesn't overload the bus.

If USB communication is desired, an internal USB connection (either through a USB header or USB-SATA bridge) will allow the laptop OS to interface directly with the Companion Core. Alternately, a UART line can be used for serial communication.

## 🧱 Physical Design

- Form factor matches the 12.7mm ThinkPad Ultrabay optical drive dimensions
- 3D-printed enclosure to secure board and connectors
- Cutouts for:
  - USB debugging access
  - Cooling if needed (vent holes, passive airflow)
- Optional LED indicators for power/activity

## 🔩 Internals

| Component         | Purpose                                      |
|-------------------|----------------------------------------------|
| Raspberry Pi Zero | Primary compute (or equivalent microcontroller) |
| Custom PCB        | Power distribution, optional USB/serial bridge |
| Connectors        | SATA power tap, GPIO breakout                |
| Case              | 3D-printed shell in Ultrabay dimensions      |

## 🛠️ Build Goals

- [ ] Custom PCB design for clean SATA 5V input + USB hub or GPIO mux
- [ ] 3D-printed Ultrabay-compatible case
- [ ] Optional: Add status LEDs and switch to enable/disable core
- [ ] Software daemon to handle communications, logging, etc.
- [ ] Proper journaling and documentation for reproducibility

## 📷 Preview (Coming Soon)

Renderings of the enclosure, PCB schematics, and wiring diagrams will be added as the project progresses.

## 📜 License

This project is open-source under the MIT license. Use it, remix it, build on it — just don't sell it as-is without adding your own improvements.

---

> Part of the [Hack Club's Highway to Undercity](https://hackclub.com/highway) custom project series
