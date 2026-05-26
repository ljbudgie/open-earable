You are working on OpenEarable: open-source Arduino firmware for an
ear-worn research platform with BLE connectivity, a 9-axis IMU, a pressure
sensor, one or two ultrasound microphones, a speaker, an RGB LED, a push
button, and an SD card.

Core rules:

- This repository is a fork of `OpenEarable/open-earable`. Do **not** modify
  `LICENSE` or add license addenda — the upstream copyright holders set the
  terms. Contribute changes under the existing license.
- Keep changes minimal and surgical. The firmware ships to physical hardware
  and is consumed by the Arduino Library Manager; structural churn breaks
  downstream users.
- Preserve compatibility with both supported hardware revisions, 1.3.0 and
  1.4.0, unless a change is explicitly hardware-gated.
- Treat audio output as safety-critical. Do not introduce code paths that
  can drive the speaker to unsafe sound pressure levels. Default-safe
  configurations only.
- Keep all sensor processing on-device. Do not add network/cloud
  dependencies to the firmware.
- Match the existing C++ / Arduino style. Run `clang-format` (see
  `.clang-format`) on files you touch under `src/`.
- Keep `library.properties` valid:
  - Bump `version=` for releases following SemVer.
  - Keep `architectures=` in sync with the boards actually supported.
  - Keep `depends=` accurate; do not add libraries that are not actually
    `#include`d.
- When you add or change a BLE service or characteristic, update the
  "BLE Specification" section in `README.md` so dashboard and edge-ml
  consumers stay in sync.
- When you add a new example, place it under `examples/<Name>/<Name>.ino`
  so the `arduino/compile-sketches` workflow picks it up automatically.

Tooling:

- Recommended build path: the
  [open-earable-PlatformIO wrapper](https://github.com/OpenEarable/open-earable-PlatformIO).
- CI builds examples with `arduino/compile-sketches` for the `mbed_nano`
  and `nrf52` architectures and runs `arduino-lint` against the library
  metadata.
- Local style: `pre-commit run --all-files` applies whitespace fixes and
  `clang-format` to `src/`.

When unsure, prefer changes that improve documentation, tests, or CI over
changes that alter firmware behaviour.
