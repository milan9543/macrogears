# MacroGears — ZMK 2-Button Macro Pad

## Wiring

Connect two momentary switches between **GND** and:

- **D0** (P0.02) → sends `I`
- **D1** (P0.03) → sends `K`

> If you use different pins, edit `macrogears.overlay` and update the gpio numbers.

## Build locally

```bash
west init -l config
west update
west build -s zmk/app -b nice_nano_v2 -- \
  -DSHIELD=macrogears \
  -DZMK_CONFIG="$(pwd)/config"
```

## Build via GitHub Actions

1. Fork [zmkfirmware/unified-zmk-config-template](https://github.com/zmkfirmware/unified-zmk-config-template)
2. Drop the `config/` folder and `build.yaml` into the repo root
3. Push — Actions will produce a `firmware.zip` artifact with the `.uf2` file

## Flash

1. Double-tap the reset button on the board — it mounts as a USB drive
2. Copy the `.uf2` file onto that drive
3. Board reboots automatically

## Pairing

Hold **both buttons for 5 seconds** to clear Bluetooth bonds and enter pairing mode.

## Sleep

Board sleeps after **10 minutes** of inactivity. Press any button to wake.
