# Hardware

This firmware targets the OpenEarable ear-worn research platform. The
canonical hardware project and PCB sources live in the upstream
[OpenEarable](https://github.com/OpenEarable) organisation; this document
only summarises what the firmware in this repository expects, and points
to related downstream projects that build on top of OpenEarable hardware.

## Supported revisions

| Revision | Sensors / actuators                                                                                  |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `1.3.0`  | 9-axis IMU, ear-canal pressure & temperature sensor, in-ear ultrasound microphone, speaker, RGB LED, push button, microSD slot |
| `1.4.0`  | All of `1.3.0`, plus a second (out-of-ear) ultrasound microphone for dual-microphone capture          |

When both microphones on a `1.4.0` device are enabled simultaneously the
maximum per-channel sample rate of 62.5 kHz cannot be reached due to
bandwidth constraints — see the BLE specification in
[`README.md`](README.md) for the current limits.

## Storage

OpenEarable records audio to, and plays audio from, an on-board microSD
card. The firmware expects:

- A SanDisk Extreme Class 3 (or equivalent class 10 / A30) card, and
- The card formatted as **exFAT**.

Other classes are not supported and will produce audio dropouts.

## Build & flashing

The recommended way to build and flash the firmware is the
[open-earable-PlatformIO](https://github.com/OpenEarable/open-earable-PlatformIO)
wrapper, which pins the toolchain, libraries, and bootloader for you.
Building inside the Arduino IDE is also supported; the per-library setup
steps for `SdFat`, `Adafruit_BMP280`, the SPI/Wire configuration, and the
Nano 33 BLE Sense board variant are documented in detail in
[`README.md`](README.md).

## Related downstream projects

Other open projects consume OpenEarable hardware or are designed to be
worn alongside it. Notes here are informational; this repository does not
depend on them.

### OpenHear

[OpenHear](https://github.com/ljbudgie/openhear) is an independent,
sovereign-audio DSP and haptic-wristband project written in Python. It
treats the OpenEarable as one possible source of in-ear audio and IMU
signals for its pipeline. Useful entry points if you are combining the
two projects:

- **Clinician guide** —
  [`CLINICIAN_GUIDE.md`](https://github.com/ljbudgie/openhear/blob/main/CLINICIAN_GUIDE.md)
  documents sovereignty-first fitting workflows (audiograms, fitting
  receipts, no raw-audio leakage).
- **Wristband build guide** —
  [`HARDWARE.md`](https://github.com/ljbudgie/openhear/blob/main/HARDWARE.md)
  in the OpenHear repository describes the no-solder haptic wristband
  prototype that pairs with OpenEarable-style in-ear sensing.
- **Sovereign audio architecture** —
  [`SOVEREIGN_AUDIO.md`](https://github.com/ljbudgie/openhear/blob/main/SOVEREIGN_AUDIO.md)
  explains the data-handling model OpenHear applies on top of any
  hardware capture source.

The licensing and project goals of OpenHear and OpenEarable differ;
please read each project's `LICENSE` and `README.md` before combining
them in a deployment.
