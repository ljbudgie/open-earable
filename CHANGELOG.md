# Changelog

All notable changes to this firmware are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project aims to follow [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

This is a fork of the upstream
[OpenEarable/open-earable](https://github.com/OpenEarable/open-earable)
firmware. Entries below summarise the upstream history that this fork is
based on; please refer to upstream tags for authoritative release notes.

## [Unreleased]

### Added
- Repository hygiene and contributor docs: `.editorconfig`,
  `CODE_OF_CONDUCT.md`, `SECURITY.md`, `CHANGELOG.md`, `COPILOT.md`.
- Continuous integration: `arduino/compile-sketches` workflow that builds
  the example sketches for the `mbed_nano` and `nrf52` board architectures
  declared in `library.properties`.
- `arduino-lint` workflow to validate Arduino library structure on every
  push and pull request.
- `clang-format` configuration and a `pre-commit` hook that applies it to
  sources under `src/`.
- `HARDWARE.md` documenting hardware revisions 1.3.0 and 1.4.0 and pointing
  to related downstream projects.

### Changed
- Extended `.gitignore` to cover Arduino CLI build output, PlatformIO
  artefacts, and common IDE folders.

### Notes
- License (`LICENSE`) is intentionally left untouched. This repository
  remains under the upstream OpenEarable license; downstream additions in
  this fork are contributed under the same terms.

## [1.4.0] — Unreleased upstream work

Tracks the upstream `v1.4.0` line described in `README.md`.

### Added
- Support for hardware revision 1.4.0, which adds dual ultrasound
  microphones: one in-ear and one out-of-ear.

### Changed
- When both microphones are enabled the maximum sampling rate of 62.5 kHz
  cannot be achieved because of bandwidth constraints. See the README for
  details.

## [1.3.0] — Upstream baseline

This is the upstream release that the fork is currently aligned with, as
reflected by `library.properties` (`version=1.3.0`).

### Included
- BLE API exposing the IMU, pressure sensor, microphone, RGB LED, and audio
  player.
- Notifications for button state and battery level changes.
- Compatibility with the OpenEarable dashboard and edge-ml.org.
- Support for hardware revision 1.3.0 (9-axis IMU, pressure sensor,
  speaker, in-ear ultrasound microphone).

[Unreleased]: https://github.com/ljbudgie/open-earable/compare/v1.3.0...HEAD
[1.4.0]: https://github.com/OpenEarable/open-earable/releases/tag/v1.4.0
[1.3.0]: https://github.com/OpenEarable/open-earable/releases/tag/v1.3.0
