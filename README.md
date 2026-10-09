# Klipper Printer Configuration

Klipper configuration for my Voron 2.4 (350 mm build).

- **Controllers**: Bigtreetech Manta M8P + CB1 (host MCU)
- **Toolhead**: Stealthburner with SB2209 RP2040 over CAN on Voron TAP
- **Nevermore**: Nevermore Micro v6 activated carbon filters with extra bed fans

## Installation

1. On the Klipper host:
    ```sh
    $ cd ~/printer_data
    $ rm -rf config
    $ git clone https://github.com/tabjy/klipper-config.git config
    $ cp config/printer.cfg.example config/printer.cfg
    ```

2. In the Klipper console:
    ```gcode
    G28
    G0  X175 Y175 Z75 F7200

    PID_CALIBRATE HEATER=heater_bed TARGET=100
    PID_CALIBRATE HEATER=extruder   TARGET=245

    PROBE_CALIBRATE

    SHAPER_CALIBRATE AXIS=X
    SHAPER_CALIBRATE AXIS=Y

    QUAD_GANTRY_LEVEL
    BED_MESH_CALIBRATE

    SAVE_CONFIG
    ```

    Note result from `SAVE_CONFIG` is written to `printer.cfg` and is ephemeral. It's not tracked by this repo and is gitignored. Backup `printer.cfg` by other means if needed.

## Slicer setup

- Start G-code:
    ```gcode
    PRINT_START EXTRUDER=[nozzle_temperature_initial_layer] BED=[bed_temperature_initial_layer]
    ```

- End G-code:
    ```gcode
    PRINT_END
    ```

## License

[GPL-3.0](./LICENSE). Portions of this configuration are derived from:

- [FORMBOT/Voron-2.4](https://github.com/FORMBOT/Voron-2.4) — printer configuration (GPL-3.0)
- [Mainsail](https://github.com/mainsail-crew/mainsail) — `mainsail.cfg` client macros (GPL-3.0)
- Timelapse macro v1.15 by Christoph Frei and Alex Zellner (GNU GPLv3)
- Print area bed mesh macro by Steve Turgeon
