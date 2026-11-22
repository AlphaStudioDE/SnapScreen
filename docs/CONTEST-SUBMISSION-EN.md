# SnapScreen — a dedicated touchscreen workspace for Snapmaker U1

SnapScreen brings printer controls, monitoring, files, G-code previews and configurable dashboards to a dedicated ESP32-P4 touchscreen. The panel runs its own application; it does not need a Raspberry Pi to host the touchscreen interface. It communicates through the printer's local API without replacing the printer firmware.

The screen should adapt to the person using the printer. Users can combine readings, controls, charts and shortcuts into their own layouts, keep different workspaces for different tasks, and still reach a complete print monitor or G-code viewer when needed.

## What the gallery demonstrates

- Configurable dashboards with touch-and-hold editing, a widget library, selectable sizes and alternative widget presentations.
- Four-hotend monitoring, bed/chamber readings, thermal history, targets, presets, cooling controls and speed/flow overrides.
- XYZ movement, step sizes, homing, position, motors, extrusion and Z-offset controls, subject to printer state and support.
- Printer file browsing, selected-file information and storage figures.
- A G-code viewer with 3D toolpaths, model details, tool/feature filtering, rotation, pan, zoom and lighting.
- Print monitoring with elapsed/remaining time, progress, layers and an embedded 2D/3D preview.
- Native four-tool filament management: materials, colors, active tool and load/unload workflow controls.
- Printer macros, a G-code console/terminal, camera viewing and bed-mesh inspection where provided by the printer.
- Four icon families, independent interface tones and dark/light mode. The images use Satin Ribbon / Blue / dark.

## Why this is useful

A dedicated panel keeps the printer workflow beside the machine. The same device can show an overview, provide a focused thermal or motion workspace, inspect a file before printing, or display a larger 3D toolpath. Users can arrange widgets around their own work instead of adapting every task to one fixed dashboard.

## Hardware and product scope

The XL build targets the supported JC1060P470 carrier/display combination: 1024 × 600 capacitive touch, ESP32-P4, 16 MiB flash and 32 MiB PSRAM. Older P4 and new P4 v3.x use family-specific firmware. The dual-P4 installer detects the silicon revision and selects the matching supported image. This is still a DIY/beta project requiring the documented board/panel combination and assembly steps.

SnapScreen is free and has no activation payment. It is the printer-panel product. External filament-changer integration belongs to PrismFlow and retains its activation; those changer functions are not free SnapScreen features. Native printer tool/filament functions remain available in SnapScreen.

## Image and test provenance

These are actual 1024 × 600 LVGL snapshots taken on the owner ESP32-P4 panel, not artist renders or desktop mockups. Capture uses a temporary private transport that is excluded from distributed firmware. The interface comes from the local 1.0.10 candidate with square bottom navigation tiles and the larger four-spool/four-LED Filaments icon.

Telemetry, the 40-percent print and sample G-code/mesh values come from an isolated presentation source. Images demonstrate the real interface, not completion of a physical print, heating cycle, motion, filament load/unload or calibration test. Capture automation invokes no printer commands. Camera and other printer-specific features require the corresponding printer/API configuration.

Read the public download version from the repository release: these 1.0.10 images do not silently replace an older published kit.

Creator: Damian Borkowski / PrismFlow.

Project: https://github.com/AlphaStudioDE/SnapScreen
