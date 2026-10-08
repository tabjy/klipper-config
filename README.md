# Klipper Printer Configuration

Klipper configuration for my Voron 2.4 (350 mm build).

- **Controllers**: Bigtreetech Manta M8P + CB1 (host MCU)
- **Toolhead**: Stealthburner with SB2209 RP2040 over CAN on Voron TAP
- **Nevermore**: Nevermore Micro v6 activated carbon filters with extra bed fans

## Slicer setup

Start G-code:

```gcode
PRINT_START EXTRUDER=[nozzle_temperature_initial_layer] BED=[bed_temperature_initial_layer] PROBE=150
```

End G-code:

```gcode
PRINT_END
```

## License

[GPL-3.0](./LICENSE). Portions of this configuration are derived from:

- [FORMBOT/Voron-2.4](https://github.com/FORMBOT/Voron-2.4) — printer configuration (GPL-3.0)
- [Mainsail](https://github.com/mainsail-crew/mainsail) — `mainsail.cfg` client macros (GPL-3.0)
- Timelapse macro v1.15 by Christoph Frei and Alex Zellner (GNU GPLv3)
- Print area bed mesh macro by Steve Turgeon
