# Keymap changes

There are two main ways to change keys:

1) **ZMK Studio** (live changes; no re-flash for keymap updates)
- Recommended for most key changes.
- See: [ZMK Studio](zmk-studio.md)

2) **Rebuild + re-flash firmware** (for structural/advanced changes)
- Required when you change features/settings beyond what ZMK Studio can edit.
- Examples: enabling/disabling features, changing devicetree/overlays, changing what behaviors are available, changing sensors/encoders configuration, etc.

## Editing the keymap in this repo

- Primary keymap file used for customization: [config/eyelash_sofle.keymap](../config/eyelash_sofle.keymap)
- Configuration options live in: [config/eyelash_sofle.conf](../config/eyelash_sofle.conf)

Tip: some shield default keymaps also exist under `boards/shields/**`, but for this repo you should typically edit the files under `config/`.

## Build with GitHub Actions (recommended)

1. Fork this repository on GitHub.
2. In your fork, go to **Actions** and enable workflows if GitHub prompts you.
3. Modify the keymap:
   - Edit the keymap file directly in GitHub, or
   - Use the Keymap Editor: https://nickcoutsos.github.io/keymap-editor/
4. Commit your changes.
5. GitHub Actions will run automatically (or use **Run workflow**).
6. Download the build artifact from the Actions run.

## Flashing the firmware (`.uf2`)

1. Connect the target device (dongle, left, or right) via USB.
2. Double-press the reset button to enter bootloader mode.
3. A USB drive will appear.
4. Copy the correct `.uf2` file to the root of that drive.

Important:
- Don’t delete files from the bootloader drive.
- For split keyboards, flashing the keymap often only requires the “central” device. In **dongle mode**, the “central” device is the **dongle/receiver**, not the left half.

## If a build fails

- Undo the last keymap change and try again.
- If needed, re-fork the repo to return to a known-good state, then re-apply your changes with the Keymap Editor to reduce syntax errors.
