# Firmware — Anki Macropad

QMK firmware for the Anki Macropad. Built using [QMK MSYS](https://msys.qmk.fm/) on Windows.

## Files

- `anki_macropad/` — keyboard definition (place in `qmk_firmware/keyboards/`)
- `anki_macropad_default.uf2` — compiled firmware ready to flash

---

## Flashing Pre-built Firmware

If you just want to flash the macropad without recompiling:

1. Hold the **BOOTSEL button** (SW1) while plugging in USB
2. The board appears as a USB drive called **RPI-RP2** in File Explorer
3. Drag and drop `anki_macropad_default.uf2` onto the drive
4. The drive disappears and the board reboots — done

---

## Building from Source

### 1. Install QMK MSYS

Download and install from [msys.qmk.fm](https://msys.qmk.fm/). Open **QMK MSYS** from the Start menu when done.

### 2. Set Up QMK

```bash
qmk setup
```

Say yes when prompted to clone the QMK repository.

### 3. Copy the Keyboard Definition

Copy the `anki_macropad/` folder into your QMK firmware keyboards directory:

```
qmk_firmware/keyboards/anki_macropad/
```

### 4. Compile

```bash
qmk compile -kb anki_macropad -km default
```

The compiled `.uf2` file will appear in the root of the `qmk_firmware/` folder as `anki_macropad_default.uf2`.

### 5. Flash

Follow the flashing steps above.

---

## Keymap

| Key | Keycode | Anki Function |
|---|---|---|
| Again | `1` | Rate card: Again |
| Hard | `2` | Rate card: Hard |
| Good | `3` | Rate card: Good |
| Easy | `4` | Rate card: Easy |
| Edit | `E` | Edit current card |
| Show Answer | `Space` | Flip card / show answer |

To change keycodes, edit `anki_macropad/keymaps/default/keymap.c` and recompile.

---

## Hardware

- **MCU:** RP2040
- **Rows:** GP0, GP1, GP2
- **Columns:** GP24, GP25, GP6, GP7
- **Diode direction:** COL2ROW
- **Bootloader:** rp2040 (UF2 drag-and-drop)
