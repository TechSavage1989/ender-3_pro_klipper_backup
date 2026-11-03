<h1 align="center">Ender-3 Pro Klipper Backup</h1>
<p align="center">Backup of the Klipper, Moonraker, KlipperScreen and Crowsnest configuration for a Creality Ender-3 Pro.</p>

<p align="center">
  <a href="#whats-inside">What's inside</a> ·
  <a href="#restoring">Restoring</a>
</p>

Klipper backup script for manual or automated GitHub backups. This backup is provided by [Klipper-Backup](https://github.com/Staubgeborener/klipper-backup).

## What's inside

Everything lives under `printer_data/config/`, mirroring the printer host's `~/printer_data/config` folder.

| File | What it holds |
| --- | --- |
| [`printer.cfg`](printer_data/config/printer.cfg) | Main Klipper config: MCU, steppers, extruder, heated bed, BLTouch, safe Z home, screws tilt adjust, bed mesh, display, plus the saved bed mesh, PID and Z-offset values |
| [`macros.cfg`](printer_data/config/macros.cfg) | G-code macros: `PRINT_START` / `PRINT_END`, pause/resume/cancel, filament load/unload, adaptive bed mesh and purge, parking, and the `update_git` backup macro |
| [`shell_command.cfg`](printer_data/config/shell_command.cfg) | Shell-command macros for camera logs and finding the MCU serial port |
| [`moonraker.conf`](printer_data/config/moonraker.conf) | Moonraker server, authorization, history and update manager (Fluidd, Klipper-Backup, Crowsnest) |
| [`moonraker.conf.backup`](printer_data/config/moonraker.conf.backup) | Earlier copy of `moonraker.conf`, before the Crowsnest update manager entry was added |
| [`crowsnest.conf`](printer_data/config/crowsnest.conf) | Crowsnest webcam streamer settings |
| [`KlipperScreen.conf`](printer_data/config/KlipperScreen.conf) | KlipperScreen UI settings |

Files such as `.env`, `secrets.conf`, CSVs and timestamped `printer-*.cfg` backups are excluded by [`.gitignore`](.gitignore).

## Restoring

Copy the contents of `printer_data/config/` back into `~/printer_data/config/` on the printer host, then restart Klipper and Moonraker. Device paths in `printer.cfg` (such as the `[mcu]` serial port) and the `virtual_sdcard` path are specific to the original host and may need updating.
