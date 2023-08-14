> #### Legend
> - ✨ = feature that other drivers don't have
> - 🛑 = missing feature that other drivers have


- [torvalds/linux → /drivers/hid/hid-magicmouse.c](https://github.com/torvalds/linux/blob/master/drivers/hid/hid-magicmouse.c)
  - the mainline driver you're probably using right now
  <!-- - supports USB and Bluetooth -->
  - ✨ supports battery level reporting
  <!-- - does not support host click / … -->
<!---->
- [mwyborski/Linux-Magic-Trackpad-2-Driver](https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver)
  - aka [robotrovsky/Linux-Magic-Trackpad-2-Driver](https://github.com/robotrovsky/Linux-Magic-Trackpad-2-Driver)
  - was [mainlined](https://github.com/torvalds/linux/commit/9d7b18668956c411a422d04c712994c5fdb23a4b) in 2018 (see above)
  - untouched since 5 years, so outdated compared to mainline
<!---->
- [dos1/Linux-Magic-Trackpad-2-Driver](https://github.com/dos1/Linux-Magic-Trackpad-2-Driver)
  - fork of [mwyborski/Linux-Magic-Trackpad-2-Driver](https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver) (see above)
  - ✨ adds configuration options for haptic feedback
  <!-- - supports USB and Bluetooth -->
<!---->
- [nexustar/linux-hid-magicmouse](https://github.com/nexustar/linux-hid-magicmouse)
  - fork of [torvalds/linux → /drivers/hid/hid-magicmouse.c](https://github.com/torvalds/linux/blob/master/drivers/hid/hid-magicmouse.c) (see above)
  - ✨ adds support for host click and click sensitivity
<!---->
- [ponyfleisch/hid-magictrackpad2](https://github.com/ponyfleisch/hid-magictrackpad2)
  <!-- - completely different code -->
  - ✨ supports host click and click sensitivity
  - ✨ supports “force clicks”
    - haptic feedback as expected
    - supposed to emulate a middle click, but doesn't work as-is
  - 🛑 does not support USB
  - compilation requires a small change as of Linux 5.15
    - from: `hid_register_report(hdev, HID_INPUT_REPORT, 0x31);`
    - to: `hid_register_report(hdev, HID_INPUT_REPORT, 0x31, 0);`
  <!-- - code looks clean -->
  - claims to be based heavily on [mwyborski/Linux-Magic-Trackpad-2-Driver](https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver) (see above) and [robbi5/magictrackpad2-dkms](https://github.com/robbi5/magictrackpad2-dkms) (see below)
  - author considers [mwyborski/Linux-Magic-Trackpad-2-Driver](https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver) (see above) superior [¹](https://github.com/ponyfleisch/hid-magictrackpad2/issues/4#issuecomment-394312796)
  <!-- - supports USB and Bluetooth -->
<!---->
- [robbi5/magictrackpad2-dkms](https://github.com/robbi5/magictrackpad2-dkms)
  - probably outdated
<!---->
- [adam-h/Linux-Magic-Trackpad-2-Driver](https://github.com/adam-h/Linux-Magic-Trackpad-2-Driver)
  - fork without any changes
<!---->
- [bobbysue/Linux-Magic-Trackpad-2-Driver](https://github.com/bobbysue/Linux-Magic-Trackpad-2-Driver)
  - fork without any changes
