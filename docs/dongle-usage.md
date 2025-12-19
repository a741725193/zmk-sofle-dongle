# Dongle usage (receiver mode)

This keyboard is configured to run in **dongle mode**:

- The **dongle/receiver** is the ZMK “central” device.
- The **left + right halves** are ZMK “peripherals”.
- Keystrokes are sent from the halves to the dongle first, then forwarded to your computer via **USB** or **Bluetooth**.

## What changes in dongle mode

- The halves do **not** directly connect to the computer; they connect to the dongle.
- After the dongle is configured, power usage on the left half is reduced (per the vendor documentation) and the dongle can operate at a higher report rate.

## Hardware controls on the dongle

- **Battery toggle switch (ON/OFF)**: disconnects the internal battery.
  - If you always use the dongle connected to USB, you can leave the battery switch **OFF** to reduce battery wear.
- **Reset button**:
  - With the dongle connected via USB, **double-press reset** to enter bootloader mode.
  - A USB drive will appear on your computer. Copy the new firmware file (`.uf2`) onto it.

## Suggested placement

- Use the included stand to angle the dongle on the desk.
- Optionally mount it on top of your monitor (the dongle includes a magnet; a metal patch can be attached to the monitor).

## First-time setup / re-pairing (recommended reset sequence)

If you purchased the keyboard earlier and added a dongle later (or if pairing is broken), do a full settings reset:

1. Flash the **`settings_reset`** firmware to:
   - dongle/receiver
   - left half
   - right half
2. Then flash the normal firmware to each device:
   - dongle: the **dongle firmware**
   - left: **left firmware**
   - right: **right firmware**

Notes:
- The `settings_reset` firmware does not distinguish left/right; it’s just to clear stored pairing/settings.
- After flashing, power both halves and the dongle; they should pair automatically.

## Using ZMK Studio (live keymap changes)

If you are using ZMK Studio for live keymap updates, connect the **dongle** via USB and follow the ZMK Studio guide in [ZMK Studio](zmk-studio.md).
