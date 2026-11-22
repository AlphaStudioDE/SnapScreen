# SnapScreen — visual feature reference

One screenshot can document several related functions. The gallery therefore groups controls into workspaces instead of repeating an image for each button. Availability and permission to run commands depend on printer state and configuration. Capture automation did not operate the printer.

| Screenshot ID | Workspace | Functions documented |
|---|---|---|
| status | Home dashboard | Printer state, filename, four-hotend readings, bed/chamber temperatures, progress, elapsed/remaining time and connection widgets. |
| status-left | Readings and readiness | Four hotend columns, speed/flow/fan instruments, connection state and detected printer features. |
| status-right | Progress workspace | Circular progress, elapsed/remaining time, connectivity, speed/flow and cooling readouts. |
| temperatures | Temperature workspace | Hotend/bed/chamber readings, heater-target entry, heating cancellation and thermal history. |
| temperatures-left | Four-hotend workspace | Native tool selection, per-hotend history, heater readiness, cooling controls and speed/flow. |
| temperatures-right | Thermal presets | Material presets, bed/chamber detail, difference from target and fine target adjustment. |
| movement | Motion workspace | XYZ jog controls, selectable steps, live position and axis/all homing. |
| movement-left | Extrusion and Z | Extrude/retract entry, extrusion length, Z-offset controls, motors and feedrate selection. |
| movement-right | Position and quick moves | Larger coordinates, motor controls, quick-move shortcuts and motion feedrate. |
| macros | Macro workspace | Printer-provided macro library and an embedded G-code console. Macros come from printer configuration. |
| macros-left | Console widget | Full-width command input and response log inside a saved dashboard. |
| macros-right | Tramming and macros | Bed-screw tramming entry, configurable macro workspace and G-code console. No calibration was run. |
| files | File workspace | G-code browser, selected-file information, print/reload entry and storage summary. No print was started. |
| files-left | File information | Larger file list, selection information and file/storage figures. |
| files-right | File actions | File list, print/reload entry and storage figures in an alternate saved layout. |
| printing | Print monitor | Four native spools with materials/colors, active-filament paths, progress, elapsed/remaining time, layer, temperatures, speed/flow, embedded 3D preview and pause/cancel entry. |
| printing-2d | Embedded 2D preview | Alternative print-preview mode within the same print monitor. Reuse the main monitor image unless the mode difference matters. |
| filaments | Native filament management | Four printer-native tools, material/type, color/HEX, selected-tool console, temperature and staged load/unload workflow entry. This is separate from external CFS integration. |
| preview-load | G-code viewer | A file loaded and parsed on the panel; 3D toolpath, pan/rotate/zoom, orientation and lighting controls. |
| preview-details | Model details | Parsed file/model statistics beside the toolpath. One shot also documents the main viewer. |
| preview-filters | Toolpath filtering | Tool/feature visibility and filtering controls for the loaded G-code. Data depends on the file. |
| preview-files | Viewer file picker | Printer G-code selection, file information and thumbnail before loading the toolpath. |
| leveling | Bed-mesh inspection | Surface visualization, profile and height range where mesh data is provided. No probing, heating or bed calibration was performed. |
| leveling-toggle | Alternative mesh view | Another presentation of the same mesh. Include only when it adds useful information. |
| terminal | Printer terminal | History, search, message filters, follow/scroll, clear/export and G-code entry. No command was executed during capture. |
| camera | Camera workspace | Camera/source selection and view controls. No configured camera feed in this session; not a live-camera demonstration. |
| appearance | Appearance | Independent icon family, interface tone and dark/light selection. Current choice: Satin Ribbon / Blue / dark. |
| editor | Dashboard editor | Touch-and-hold editing, widget outlines and edit controls. No owner layout was changed or saved. |
| widget-library | Widget library | Widget categories, native previews, available sizes and presentations before placement. Changer-only controls are outside the free product scope. |

## Additional capabilities represented by the widget library

The panel includes printer status, temperatures, print progress, Smart ETA, quick actions, connection, fan speed/control, print preview, temperature targets and presets, native extruder selection, speed/flow overrides, thermal graphs, jog/step controls, homing, position, extrusion/retraction, Z offset, macro bindings, console, screw-tramming entry, files, bed/chamber detail, heater readiness, target nudging, thermal delta, per-hotend graphs, motion feedrate, quick moves, motors, file/storage statistics, capability detection, user notes/reminders and printer-light controls.

Some are alternative widget presentations or printer-dependent controls rather than separate full-screen applications. Listing a feature does not claim a completed physical actuation test. External changer, CFS and Rainbow control widgets belong to PrismFlow and must not be counted as free SnapScreen functions.

## Selection rules

Use the print monitor, native Filaments console, loaded G-code viewer, a thermal dashboard, a motion dashboard, widget editing/library, bed mesh and Appearance as the primary story. The extended gallery retains distinct workspace layouts. Exclude duplicate views, unconfigured camera imagery and owner-identifying Settings from the main presentation.

The image files have no added watermark. Their accompanying provenance states that the UI was captured on hardware with illustrative telemetry from an isolated source, rather than a real physical print or calibration test.
