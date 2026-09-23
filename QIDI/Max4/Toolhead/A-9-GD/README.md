# QIDI Max4 toolhead board: A-9(GD)

> **Disclaimer.** Unofficial. Compiled from a QIDI pinout sheet for an older
> revision, a vendor product photo, and one owner's live Klipper config. Any of
> it can be wrong for your board. Continuity-test before you connect anything.

## What it is

The toolhead MCU board: Klipper's `[mcu THR]`. QIDI sells it as the
**"Max4 Adapter Plate"**, SKU MAX4017
(<https://au.qidi3d.com/products/max4-adapter-plate>). The product page does
not name the board; the silkscreen in its photo reads **A-9(GD) V1.5**.

| | |
|---|---|
| MCU | GigaDevice GD32 (the "(GD)" in the name). Klipper reports it as `stm32f103xe` **[verified]** |
| Host link | UART to the Max4's **X-12-1 AP board** ("Toolhead Adapter Port"), `/dev/ttyS4` at 500000 baud **[verified]** |
| Extruder driver | TMC2209 (U5, under the heatsink) **[vendor]** |
| On board | CS1237 load-cell ADC, LIS2DW12 accelerometer, and on V1.5 a MAX6675 thermocouple amplifier |

## Not the Q2 board

The Q2 toolhead ("Q2 Adapter Plate") is a different board, the **A-10**, with a
different layout. A QIDI Discord post shared `A-9(GD) V1.2_002 PIN.pdf`
alongside the Q2's **X-9-1 / X-9-3** mainboard sheets, which makes it look like
a Q2 document. The Max4's own mainboards are **X-12-1 / X-12-3**.

## Revisions

| Rev | What we have | Notes |
|---|---|---|
| [V1.2](V1.2/) | QIDI pin-assignment sheet (image) | Vendor document. **Differs from V1.5 in at least two places** |
| [V1.5](V1.5/) | QIDI product photo, live-config pin map | The revision on the documented machine |

## Sources

- QIDI pin sheet `A-9(GD) V1.2_002 PIN`, shared on the QIDI Discord
  (referenced in <https://github.com/QIDITECH/QIDI_Q2/issues/2>)
- QIDI product page, Max4 Adapter Plate, SKU MAX4017
- Live `printer.cfg` and includes, QIDI Max4 firmware 02.02.01.08, read 2026-09-23
- Max4 board photos: <https://github.com/thelegendtubaguy/QidiMax4CommunityWiki>
