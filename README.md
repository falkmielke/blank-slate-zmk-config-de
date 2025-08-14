# Blank Slate ZMK Firmware

This repo contains the firmware for the Blank Slate PCB.

For full build guide for the Blank Slate, see https://docs.lpgala.xyz/docs/blank-slate-build-guide/overview/

# Soft Off Support

Blank Slate includes support for a ZMK feature this is still [in a PR](https://github.com/zmkfirmware/zmk/pull/1942). By default, this repository builds against that feature branch to ensure that works properly.

Should you desire to track ZMK `main` (or some other branch of ZMK), simply edit the `config/west.yml` file and replace the contents with:

```
manifest:
  remotes:
    - name: petejohanson
      url-base: https://github.com/petejohanson
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: blank-slate-zmk-module
      remote: petejohanson
      revision: main
  self:
    path: config
```

And then comment out the line in `config/lpgalaxy_blank_slate.conf`:

```
# CONFIG_ZMK_PM_SOFT_OFF=y
```


# About This Fork

Forked from https://github.com/petejohanson/blank-slate-zmk-config (20250814)
in an attempt to realize something close to German QWERTZ layout.
(Typing training for the children of a friend, who are usually bound to the limitations of their local schools' keyboards.)


# References

- basic layout: https://docs.lpgala.xyz/docs/blank-slate-build-guide/typing-test

- list of available codes: https://zmk.dev/docs/keymaps/list-of-keycodes and modifiers https://zmk.dev/docs/keymaps/modifiers

- translation german keys: https://github.com/qmk/qmk_firmware/blob/master/quantum/keymap_extras/keymap_german.h

- German keyboard layout: https://en.wikipedia.org/wiki/German_keyboard_layout, 
  https://en.wikipedia.org/wiki/German_keyboard_layout#/media/File:KB_Germany.svg


# procedure

- build and download the `*.uf2` firmware file (from `_studio` and `_zmk`, choose the latter)
- connect via usb
- double-press the reset button 
  - small hole/button on the back, between keys [w] and [e]
  - or: [&bootloader] key
  - -> blue LED behind [Esc] will flash
- this should mount the keyboard as a usb drive (otherwise/linux, mount manually)
- copy the firmware file to the keyboard (will restart and unmount)


# TODO's

- [x] Umlaute
- [x] arrange modifiers
- [x] more special keys
- [x] num row (shift up with left thumb nav)
- [x] F-keys (left block of NUM)
- [x] update keymap svg
