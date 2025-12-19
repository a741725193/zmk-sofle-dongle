# ZMK Studio (live keymap changes)

ZMK Studio lets you change key assignments at runtime, without rebuilding or flashing firmware (for supported capabilities).

Official docs: https://zmk.dev/docs/features/studio

## What you can (and can’t) do

ZMK Studio is great for:
- Editing key bindings while the keyboard is in use
- Renaming layers and enabling extra layers
- Assigning predefined behaviors to keys

ZMK Studio does **not**:
- Define brand new behaviors that are not already in the firmware/devicetree
- Define new physical layouts

If you need those, you must rebuild + flash firmware.

## Requirements (already mostly set up in this repo)

To use ZMK Studio over USB, the firmware needs:
- the `studio-rpc-usb-uart` snippet
- `CONFIG_ZMK_STUDIO=y`

This repo’s [build.yaml](../build.yaml) already enables those for the **dongle/central** build (recommended: only central should have Studio enabled).

Also, ZMK Studio requires a **`&studio_unlock`** binding in the keymap.

## Using Studio

1. Connect the **dongle/receiver** via USB.
2. Open ZMK Studio:
   - Web: https://zmk.studio/ (Chrome/Edge)
   - Native app downloads: https://zmk.studio/download
3. Select the keyboard/serial port that corresponds to the dongle.
   - If it fails to connect, close the page/app and try a different listed port.

Tip: If you are connected to the computer over both USB and BLE endpoints, set the keyboard output to match the endpoint used for Studio (e.g. use `&out OUT_USB` when using Studio over USB).

## Important: interaction with `.keymap` files

From the official ZMK docs:
- Once you start using ZMK Studio to manage your keymap, later edits to the `.keymap` file will **not** apply unless you perform **“Restore Stock Settings”** in ZMK Studio.

Practical guidance:
- If you intend to use ZMK Studio long-term, treat `.keymap` as the “baseline/stock” layout.
- Use `.keymap` edits mainly to:
  - add `&studio_unlock`
  - add extra empty `reserved` layers (so Studio can use more layers)
  - make changes that Studio cannot do
