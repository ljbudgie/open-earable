# Security Policy

This repository contains firmware for the OpenEarable hardware platform —
an Arduino-based earable with BLE connectivity, an IMU, a pressure sensor,
microphones, a speaker, and an RGB LED. Security and safety bugs in this
firmware can have real physical consequences (for example excessive sound
pressure produced by the on-board speaker, loss of BLE pairing controls, or
leaking of sensor data over the air). We take both classes of issue
seriously.

## Supported versions

This fork tracks the upstream OpenEarable firmware. Only the latest commit on
the `main` branch and the most recent tagged release receive security fixes.
There is no LTS branch.

| Version          | Supported |
| ---------------- | --------- |
| `main`           | ✅        |
| Latest release   | ✅        |
| Older releases   | ❌        |

## Reporting a vulnerability

**Please do not open a public GitHub issue for security problems.**

Use one of the following private channels instead:

1. **Preferred:** open a private vulnerability report through GitHub Security
   Advisories —
   <https://github.com/ljbudgie/open-earable/security/advisories/new>.
2. If you cannot use GitHub Security Advisories, contact the maintainer via
   their GitHub profile (<https://github.com/ljbudgie>) and request a private
   disclosure channel before sharing any details.

For issues that originate in the upstream OpenEarable codebase, please also
consider reporting them to the upstream project at
<https://github.com/OpenEarable/open-earable>.

When reporting, please include:

- A clear description of the issue and its impact (firmware vulnerability,
  hearing- or hardware-safety issue, BLE pairing or data-handling issue,
  supply-chain issue, etc.).
- Steps to reproduce, including:
  - Hardware revision (1.3.0 or 1.4.0).
  - Arduino IDE / PlatformIO version and toolchain.
  - Library versions listed in `library.properties`.
  - Any companion software (e.g. the OpenEarable dashboard, edge-ml).
- The commit SHA or release tag the report applies to.
- Any proposed mitigation, if you have one.

## What to expect

- We aim to acknowledge new reports within **5 working days**.
- We aim to provide a remediation plan or assessment within **30 days**.
- Coordinated disclosure is preferred. We will agree a disclosure date with
  the reporter and credit reporters who wish to be named.

## Scope

In scope:

- All firmware sources in `src/` (BLE services, sensor drivers, audio
  pipeline, SD logger, task manager, LED/button handling).
- Example sketches in `examples/`.
- Build resources in `resources/` that ship with the library
  (bootloaders, board variants, precompiled blobs, SPI/Wire config).
- `library.properties` and CI configuration that could be abused to ship
  altered firmware.

Out of scope:

- Vulnerabilities in third-party libraries listed under `depends=` in
  `library.properties`. Please report those upstream to the corresponding
  project.
- Vulnerabilities in the Arduino IDE, Arduino CLI, PlatformIO, or board
  packages themselves.
- Theoretical issues without a credible attack path against an OpenEarable
  device.

## Hearing-safety reports

OpenEarable is **not** a medical device. If you believe a configuration,
default, or code path in this firmware can produce sound pressure levels
through the on-board speaker that risk hearing damage, please report it
through the same private channel above and flag it as a **safety** issue.
We treat hearing-safety bugs with the same priority as security
vulnerabilities.
