# CR1FN200338 C15: config-level pin map

> **Disclaimer.** No photo or pinout sheet exists here for C15 specifically;
> see [C16](../C16/) for photos. This map is built from Creality's Klipper
> configs, which name the board as C15. It shows which MCU pins the firmware
> uses, **not** which connector each pin reaches. Continuity-test before you
> rely on it.

**[vendor-config]** unless tagged otherwise. Pins are `nozzle_mcu` pins.

## Pin map

| Function | Pin | Klipper section | Notes |
|---|---|---|---|
| Extruder STEP | PB5 | `[extruder]` | Goes to the extruder motor board, which carries the servo driver |
| Extruder DIR | !PB4 | `[extruder]` | |
| Extruder ENABLE | !PB2 | `[extruder]` | |
| **Extruder stall** | **PB12** | `[motor_control] motor_e_stall` | Active in the repo configs for the K2 and K2 Pro; **commented out** in the live V1.1.260206 config. **[inferred]** A stall/fault line back from the extruder servo |
| Heater | PB8 | `[extruder]` | |
| Hotend thermistor | PA0 | `[extruder]` | |
| Hotend fan | PB7 | `[multi_pin heater_fans]` | The oldest K2 Plus config also lists **PB2**, the extruder enable pin. Later configs drop it |
| Extruder motor fan | PB1 | `[output_pin extruder_fan]` | Newer configs and the live config only |
| Part-cooling fan | PWM !PB15, enable PB6 | `fan0`, `fan0_en` | |
| Filament sensor | !PA11 | `[filament_switch_sensor]` | Newer configs add a pull-up (`^!PA11`) |
| Accelerometer (lis2dw) | CS PA4, SCK PA5, MOSI PA7, MISO PA6 | `[lis2dw]` | Software SPI |
| Nozzle pressure sensor | swap PA15; CS PB13, PB14 | `[prtouch_v3]` | Strain-gauge Z probe. The driver is closed (`prtouch_v3` ships compiled) |
| Host UART | not in config | `[mcu nozzle_mcu]` | 230400 baud |

## Differences between the configs

| | Oldest K2 Plus (`F008`, v1.0.15) | K2 / K2 Pro (`F012`, `F021`) and live V1.1.260206 |
|---|---|---|
| Hotend fan pins | PB7 **and PB2** | PB7 only |
| Extruder motor fan | absent | PB1 |
| Extruder stall | absent | PB12 (commented out in the live config) |
| Filament sensor pull-up | no | yes |

**[inferred]** The oldest config looks written before the closed-loop extruder
existed: no stall line and no motor fan, with the hotend fan tied to the
extruder enable. Treat the newer column as correct for current boards.

## Not visible in any config

- **The RS-485 pass-through to the extruder servo (address 0x85).** The toolhead
  MCU relays these frames in firmware, over pins the configs never name.
- **Free pins.** No spare-pin list is possible without a pinout sheet or a board
  trace.
