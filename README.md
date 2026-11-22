# SnapScreen

## A free touchscreen workstation for Snapmaker U1

SnapScreen brings configurable dashboards, printer controls, file browsing,
G-code previews, camera viewing, macros and diagnostics to a dedicated
ESP32-P4 touchscreen beside your printer. It runs on the panel itself; a
Raspberry Pi is not required to host the touchscreen application.

SnapScreen is independent software. “KlipperScreen on steroids” describes the
idea, not an official association with or a renamed copy of KlipperScreen.

**SnapScreen is free to use. No activation payment, order or personal ticket is
required.** Builders supply their own hardware. Free distribution does not imply
an open-source licence; no firmware source is published in this repository.

### SnapScreen and PrismFlow

This repository is dedicated to the **free printer panel**. Filament changer
integration belongs to [PrismFlow](https://github.com/AlphaStudioDE/PrismFlow),
which retains its existing activation system. Changer controls in SnapScreen
are grey and inactive; selecting them explains the PrismFlow requirement.
Normal printer-native tool selection remains available.

The panel-only build does not require CFS units, CAN modules, PTFE splitters,
rewinders, bearings or a 24 V changer power supply. It does not require flashing
a modified C6 CAN bridge.

### Hardware and installation

The current XL hardware is the supported GUITION JC1060P470 M3/ETH display and
carrier combination: 7-inch 1024 × 600 capacitive touch, ESP32-P4 with C6 companion,
16 MiB flash and 32 MiB PSRAM. Older P4 and P4 v3.2 require different images.
The dual-P4 USB helper detects CPU revision and chooses the matching firmware;
CPU detection does not identify every possible LCD panel variant.

Use the complete matching installer and its guide. Never bypass revision or
partition checks with `--force`, erase a board to bypass a refusal, or use another
board's backup. Keep the helper's private full backup locally.

### Public downloads and compatibility

[Browse public releases](https://github.com/AlphaStudioDE/SnapScreen/releases/latest).
Free firmware uses **`snapscreen-free.ssota`** for older P4 and
**`snapscreen-free-p4v3.ssota`** for the new P4 family. These files are signed
application packages, not raw USB boot images. Do not flash them at guessed offsets.

The existing public 1.0.6 / 1.0.7 packages remain available. The new panel-only
contest kit 1.0.8 has been prepared locally; it has not been published here yet.
Local validation is not a claim of physical acceptance of its exact binaries.

This repository name previously hosted the combined project, which is now
[PrismFlow](https://github.com/AlphaStudioDE/PrismFlow). Reusing the old name stops
GitHub's automatic redirect. To keep already-installed clients and existing
download links working, selected historical release assets are mirrored here
byte-for-byte. **Legacy `firmwarexl*.ssota` and tester-installer assets are retained
for compatibility only**; they still require the appropriate PrismFlow activation
and do not unlock changer features for free. Their presence does not change this
repository's panel-only product scope.

Both projects communicate with the printer over its local API. The contest
demonstration targets Snapmaker U1. Compatibility with other Klipper/Moonraker
printers requires separate verification. Do not expose printer control APIs to
the Internet for this setup.

### Community and feedback

Report the product version, P4 revision, board/panel model and the exact observed
behavior. Do not attach private full-flash backups, Wi-Fi credentials or personal
activation tickets to public issues.

Created by Damian Borkowski / PrismFlow.
