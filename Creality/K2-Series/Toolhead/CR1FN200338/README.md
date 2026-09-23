# Creality K2 series toolhead board: CR1FN200338

> **Disclaimer.** Unofficial. There is no public schematic or pinout for this
> board. Everything here comes from Creality's GPL Klipper configs and product
> photos. A config shows which MCU pins the firmware *uses*, not which
> connector each pin reaches. Continuity-test before you connect anything.

## What it is

The toolhead ("nozzle") MCU board: Klipper's `[mcu nozzle_mcu]`. Creality sells
it as the **"K2/K2 Pro/K2 Plus Toolhead Board"**, and the same part fits all
three models.

| | |
|---|---|
| Board ID | **CR1FN200338** **[vendor-config]**: the header of every K2 `printer.cfg` reads `Nozzle_mcu ... version: CR1FN200338C15`; the product photo's silkscreen reads `CR1FN200338C16` |
| MCU | GigaDevice **GD32F303CBT6** (LQFP48) **[vendor-config]** |
| Host link | Serial, `/dev/ttyS1` at 230400 baud (K2 Plus); `/dev/ttyS3` on the K2 and K2 Pro **[vendor-config]** |
| Lineage | The oldest K2 Plus config names the toolhead `K1-NOZZLE-M_V12`, so the design probably descends from the K1 nozzle board **[inferred]** |

## Not on this board: the extruder driver

The K2 extruder is closed loop, but the servo driver and encoder are on a
separate **extruder motor board** mounted behind the motor, connected by two
ribbon cables (Creality's replacement guide). The motor itself is a plain
4-wire stepper. This board only sends it step/dir/enable, and passes RS-485
frames through to the servo at address 0x85.

## Revisions

| Rev | What we have |
|---|---|
| [C15](C15/) | Config-level pin map. The revision named in all published K2 configs |
| [C16](C16/) | Product photos, front and back. No pin data specific to C16 |

The trailing `Cnn` is treated as the revision because Creality's other board
IDs follow the same pattern (the K2 mainboard is `CR4FN200338C15`). **[inferred]**

## Sources

- Creality K2 Klipper source, `config/F008/`, `config/F012_CR0CN200400C10/`,
  `config/F021_CR0CN200400C10/` (<https://github.com/CrealityOfficial/K2_Series_Klipper>)
- Live stock config from a base K2, firmware V1.1.260206, captured in
  <https://github.com/night-gnida/k2-vanilla-public> (`docs/stock-live-printer.cfg`)
- Creality store, K2/K2 Pro/K2 Plus Toolhead Board (photos)
- Creality Wiki, K2 Plus "Replace Extrusion Motor Assembly"
