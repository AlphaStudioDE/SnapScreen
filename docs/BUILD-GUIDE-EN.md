# SNAPSCREEN XL 1.0.8
Free contest edition / Panel build and installation
22 November 2026 - public 1.0.8 release / network or SD installation

## 1 / What you are building

A standalone 7-inch ESP32-P4 touchscreen for controlling and monitoring a compatible printer over its local API. No Raspberry Pi is required to run the panel. SnapScreen is independent software; 'KlipperScreen on steroids' describes the concept, not a fork or an official KlipperScreen product. The contest demonstration targets Snapmaker U1. Other printers need compatible, reachable Klipper/Moonraker services and separate verification.

SnapScreen is free to use: no activation payment, order or personal ticket is required. Hardware is purchased by the builder. Free distribution does not imply an open-source licence. The same maintained application also supports the separately activated PrismFlow product. In SnapScreen, changer controls are grey and blocked; tapping them explains that PrismFlow is required. Printer-native tool selection remains available.

This package contains only the parts list and software needed for the panel. It does not require filament changers, CAN transceivers, PTFE tubes, splitters, rewinders, bearings, external changer cables or a 24 V changer supply. Do not install a modified C6 bridge for this build. Keep the working factory C6 networking firmware.

## 2 / Panel-only bill of materials

Required: 1 GUITION JC1060P470C_I_W_Y / JC1060P470 XL M3/ETH display-controller assembly, 7-inch 1024 x 600 capacitive touch, ESP32-P4 with companion C6, 16 MiB flash and 32 MiB PSRAM. Use the supported carrier and panel combination, not merely any ESP32-P4 board. Both the older P4 family and P4 v3.2 are supplied. The installer selects firmware by CPU revision; this does not identify arbitrary LCD panel variants. Photograph the PCB model/revision and verify the original demo display/touch before installation.

Required: 1 USB DATA cable matching the board's P4 programming connector. Charge-only cables cannot program it. A Windows x64 computer is needed for the first USB install; it does not need to remain connected afterwards. The portable Python/esptool runtime is included.

Required: stable regulated 5 V power through the board's documented power input. The supplied manufacturer specification states 5 V and approximately 600 mA for the module; allow supply/cable headroom and follow the exact carrier manual. A suitable USB supply may already be available. Never connect 24 V to a USB or 5 V input, backfeed two supplies, or connect mains to the board. No buck converter or panel DC socket is required when using the documented USB power path.

Required for offline installation; optional for network installation: 1 microSD card, 512 MB-4 GB, readable FAT/FAT32, plus a compatible card reader if the computer lacks one. Back up existing card data. The kit does not format the card. Larger capacities/filesystems have not been qualified for this guide.

Required for printer control: a compatible printer and local network. Start with panel and printer on the same 2.4 GHz-capable Wi-Fi/LAN, without client isolation. The panel does not change the printer firmware. Internet access is not needed for the included SD installation.

Optional: printed enclosure/stand, insulated mounting surface, suitable standoffs, screws and inserts. The final project enclosure STL and exact fastener specification are separate mechanical deliverables; this ZIP does not contain a completed printable enclosure. Choose fasteners after checking the PCB holes and enclosure; do not force screws into the screen or PCB. Use existing workshop stock where suitable. Soldering is not required for the basic USB-powered panel.

Optional: Ethernet cable for the XL carrier's RJ45 connection to a router. A printer-side USB-Ethernet adapter/hub is only relevant to a separately tested wired printer arrangement; it is not needed for ordinary Wi-Fi use. Direct Ethernet interoperability depends on the printer/adapter and is not promised by this package.

The original manufacturer specification was checked locally: JC1060P470C_I_W_Y Specifications-EN.pdf, product parameters. No live purchase prices or full PrismFlow build costs are quoted here.

## 3 / Assemble the panel

Work with power disconnected. Check the display/ribbon and carrier for damage; retain the factory-connected display and touch cables in their original connectors. Place the board on a nonconductive surface or install it in a correctly fitting enclosure with clearance under the PCB. Route the USB and optional Ethernet cables without straining their connectors. Do not add connections to GPIO, CAN, printer toolheads or filament hardware. The basic electrical connections are: regulated 5 V -> documented panel power input; PC -> P4 USB programming connector for installation; panel -> local network -> printer for operation. These are logical connections, not permission to join power sources.

Power the unmodified board and check its original demo first. If it is already running working SnapScreen, keep its identity and use the normal update path. Disconnect the printer/changer hardware from any DIY wiring; keep the printer idle. Identify the P4 programming USB connector from the carrier markings/manual, not the companion C6 connector. Close serial monitors and remove the SD card before USB flashing.

## 4 / Check and flash the P4

Extract the complete ZIP to a local folder. Run 00-CHECK-FILES.cmd. It checks all distributed file hashes, both USB variants and the two signed SD packages without accessing a device. Stop if it reports damaged files. The kit includes portable esptool 4.14.0; do not substitute a GUI with guessed offsets.

For an existing compatible SnapScreen layout: run 01-FLASH-P4.cmd, enter the verified P4 COM port and type FLASH when requested. The helper reads chip revision/security/flash layout, selects p4-v1 for v0.1-v1.99 or p4-v3 for v3.1-v3.99, and refuses unknown revisions. It saves a full 16 MiB backup and independently verifies it before writing four images. It separately verifies the write and NVS preservation before reset. Existing compatible SnapScreen identity/tickets are retained. An existing activation does not make free SnapScreen control changers.

For a fresh board still running the reviewed manufacturer demo: use 01b-MIGRATE-FACTORY-P4.cmd. It requires FLASH and MIGRATE FACTORY. Only exact reviewed factory layouts are accepted, including the occupied V3.8 boot prefix. A blank destination NVS is mandatory. The factory NVS remains in your private full backup; this route creates a new SnapScreen identity. An unknown-layout refusal is a request for review, not an instruction to erase the board. Never use factory migration to bypass a damaged/activated installation.

Logs and backups are stored under %LOCALAPPDATA%/SnapScreen/backups/tester-installer/. Keep the original full dump privately: it may contain device identity and network information. Send flash.log and observations for support, not an entire private dump. If the port is unavailable, check the P4 connector, USB data cable and board-specific BOOT/RESET procedure in the carrier manual. Do not guess pins or force a write. The helper does not erase flash, change eFuses, enable hardware security, or program C6.

## 5 / Install FREE SnapScreen - network or SD

For offline installation, copy BOTH unchanged files from 03-Installer/SD-OPTIONAL into the root of your FAT/FAT32 card: snapscreen-free.ssota and snapscreen-free-p4v3.ssota. Do not copy a ZIP, raw USB BINs, installer.ssota or a ticket. Safely eject the card and insert it into the panel.

On the panel choose 'Install SnapScreen - Free', then 'Continue' to open the embedded installer. Do not create an order or buy activation. In the installer choose Network and connect to Wi-Fi or Ethernet to download the signed free firmware, or choose 'Install from SD' with the prepared card. It automatically selects the file for the current P4 family and free product; no manual CPU selection is needed. The signature, target, chip revision and image are checked before selecting the new boot slot. Keep power connected until completion. On boot, verify the product is SnapScreen and the application version is 1.0.8.

The public SnapScreen 1.0.8 release provides both free network images and family-specific version metadata. The installer picks the correct filename automatically. Network installation needs Internet access and valid network time; the included SD packages provide an offline alternative. The embedded installer itself opens offline. No order, payment or ticket is required for either free route.

## 6 / First setup and everyday use

Choose your language/network in the first-run wizard. Join the printer's local network. Use Auto-Detect or enter the printer IP manually. Verify the printer identity/status before sending any commands. If not found, check address, Wi-Fi isolation and printer API availability. The panel is not a cloud tunnel and should not require exposing the printer API to the Internet.

Start with read-only checks: stable display and aligned touch; Wi-Fi/Ethernet connection; correct temperatures/status; files and preview; camera if available. On an empty dashboard, the centered hint reads 'Touch and hold to add widgets'. Hold a free area to enter edit mode, add a widget and save the layout. Existing widgets and print previews keep their normal behavior.

Changer controls remain grey and explain the PrismFlow requirement. Do not connect CAN modules or attempt changer calibration. Printer movement, heating, macros and file printing still operate real hardware: only test those deliberately with the printer in a safe idle state. Check the printer's own screen and emergency stop access first.

## 7 / Recovery and reporting

A missing network installation file, connection failure, server error or rejected package shows a modal explanation. Retry later or use SD. A failed download does not itself select a new boot image or perform activation. The device restarts only after OK; the current slot is retained. Capture the exact message before acknowledging it. Never use --force, erase_flash, another board's dump or a C6 update to solve a P4 black screen.

If boot/display fails, retain the helper log, exact kit/version/hash, PCB and LCD photos, observed backlight behavior and whether the P4 port appears. Stop speculative flashing. A previously verified full backup can be restored only with a reviewed board-specific procedure. This kit intentionally does not provide a one-click destructive restore button.

## 8 / Qualification and limits

Both P4 families were rebuilt as 1.0.8 with their own SDK/panel configuration. Older P4 uses ESP-IDF 5.3.5; new P4 uses ESP-IDF 6.1 with the corrected revision-specific DSI clock. Earlier released ZIPs remain unchanged. This release includes the network failure popup and empty-dashboard hint. The previous 1.0.7 new-P4 trial has owner-reported working display, touch and network installation. The exact 1.0.8 free binaries require a physical smoke test; local build, signature and simulated-flash checks are not hardware acceptance. Record boot, touch, SD, networking and the no-ticket free path on both families before claiming full contest-demo qualification.
