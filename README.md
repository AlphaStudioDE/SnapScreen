# SnapScreen

## Your printer. Your workspace. One dedicated touchscreen.

**A free ESP32-P4 touchscreen workstation for Snapmaker U1.**

[**Download the complete 1.0.8 kit — both P4 families**](https://github.com/AlphaStudioDE/SnapScreen/releases/latest/download/SnapScreen-XL-Free-Contest-Kit-1.0.8-Dual-P4.zip)
 · [English build guide](https://github.com/AlphaStudioDE/SnapScreen/releases/latest/download/Panel-Guide-EN.pdf)
 · [Instrukcja po polsku](https://github.com/AlphaStudioDE/SnapScreen/releases/latest/download/Panel-Guide-PL.pdf)
 · [Release notes](https://github.com/AlphaStudioDE/SnapScreen/releases/tag/SnapScreen_1.0.8_firmware)

SnapScreen brings configurable dashboards, printer controls, file browsing,
G-code previews, camera viewing, macros and diagnostics to a dedicated
ESP32-P4 touchscreen beside your printer. It runs on the panel itself; a
Raspberry Pi is not required to host the touchscreen application.

SnapScreen is independent software. “KlipperScreen on steroids” describes the
idea, not an official association with or a renamed copy of KlipperScreen.

**SnapScreen is free to use. No activation payment, order or personal ticket is
required.** Builders supply their own hardware. Free distribution does not imply
an open-source licence; no firmware source is published in this repository.

### More of your workflow, right beside the printer

| Feature | What it brings to your workspace |
|---|---|
| Configurable dashboards | Arrange temperature, status and print-progress widgets around your workflow. |
| Printer controls and macros | Reach normal printer actions, native tool selection and workshop shortcuts from the touchscreen. |
| Files and previews | Browse jobs and inspect supported 2D/3D G-code previews. |
| Camera and monitoring | Follow the printer view and live information when provided by the printer. |
| Workshop tools | Access the terminal, bed-mesh view and diagnostics. |
| Themes and layout editing | Shape the screen around your setup; touch and hold to add widgets. |

Feature availability depends on the printer API and configuration.

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

**The panel-only 1.0.8 kit is now available for both P4 families.** Download the
complete ZIP above and extract it. It contains the portable Windows x64 tools,
both signed offline free packages, English/Polish panel guides and BOM, a logical
connection diagram and guidance for an AI assistant helping with the build.

1. Read the guide and run `00-CHECK-FILES.cmd` without accessing a device.
2. Follow the guide's normal USB or exact reviewed factory-migration route.
   The helper makes and separately verifies a full backup before writing.
3. Choose **Install SnapScreen - Free → Continue → Network** on the panel.
   The signed free 1.0.8 image is selected automatically for the detected P4 family.
4. For offline installation, copy both free files from `03-Installer/SD-OPTIONAL`
   to the card root and choose SD instead. Neither route requires a ticket.
5. Connect to the printer on your local network, verify its identity/status and
   touch and hold a free dashboard area to add widgets.

The free application filenames remain `snapscreen-free.ssota` (older P4) and
`snapscreen-free-p4v3.ssota` (new P4). Both are version 1.0.8. Network installation
needs Internet access; the included SD files provide an offline alternative.

### What is new in 1.0.8?

- Both P4 families rebuilt as 1.0.8 with their own SDK/display configuration;
  new P4 retains the corrected DSI reference clock.
- A missing installation file, connection/server failure or rejected network
  package shows a message and waits for **OK** before restarting. Retry later
  or use SD; failure does not itself select a new boot image or perform activation.
- Empty dashboards display **Touch and hold to add widgets**.
- A panel-only build guide: no CAN, CFS, PTFE splitters, rewinders, bearings or
  24 V changer power supply. No modified C6 bridge needs to be flashed.

The basic USB-powered panel requires no soldering. A suitable regulated 5 V
supply and USB data cable are needed; use the exact carrier manual for connectors.
The final enclosure STL and exact fastener specification are separate mechanical
deliverables and are not included. Builders purchase their own hardware.

**DIY beta / contest release.** Both families build and pass local installation,
signature, routing and fault-injection checks. Display, touch and network install
were reported working on the preceding 1.0.7 new-P4 tester build. The exact free
1.0.8 binaries still require physical smoke testing on both families. Publishing
a download is not a claim that every function is qualified on every printer.

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
