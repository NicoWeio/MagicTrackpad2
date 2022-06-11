# Experimenting with the Magic Trackpad 2 on Linux

> This writeup ist just as WIP as my experiments.

## Intro
The haptic feedback of the Magic Trackpad 2 is configurable via three bytes.

In [iFixit's teardown](https://de.ifixit.com/Teardown/Magic+Trackpad+2+Teardown/51032),
we can see the that the haptic module of the Magic Trackpad 2 contains four coils.
How do they map to the three config bytes?

![](https://guide-images.cdn.ifixit.com/igi/Ak4m4Z2l5K2FqOwE.standard)
![](https://guide-images.cdn.ifixit.com/igi/2AFFx4RFJMvI2H4q.standard)


## Setup
While there is a [driver for the Magic Trackpad 2 in the Linux kernel](https://github.com/torvalds/linux/blob/master/drivers/hid/hid-magicmouse.c),
it does not allow to configure its force feedback.
That's why I installed an [alternative driver](https://github.com/nexustar/linux-hid-magicmouse).
There are other approaches, but this works well enough for me.


## Values on MacOS
According to [this issue comment](https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver/issues/28#issuecomment-451625504), these are the values that MacOS uses.
I've also included the pressure sensitivity from [here](https://github.com/nexustar/linux-hid-magicmouse/blob/main/README.md).

- strength: low
    - click: `0x15`, `0x04`, `0x04`
    - release: `0x10`, `0x00`, `0x00`
- strength: medium
    - click: `0x17`, `0x06`, `0x06`
        - pressure: `0x40`
    - release: `0x14`, `0x00`, `0x00`
        - pressure: `0x26`
- strength: high
    - click: `0x1E`, `0x08`, `0x08`
    - release: `0x18`, `0x02`, `0x02`


## Exploration of haptic feedback
- single nonzero
  - `0x00`, `0x00`, `0x00`
    - nothing
  - `0x20`, `0x00`, `0x00`
    - a dull, soft, “deep” click
    - low-pitched
  - `0x00`, `0x80`, `0x00`
    - a more audible, shallower “click”
    - high-pitched
  - `0x00`, `0x00`, `0x80`
    - a more audible, shallower “clack”
    - middle-pitched
- combined
  - …

→ It boils down to `0x{low}`, `0x{high}`, `0x{mid}`.
The higher the value, the stronger the feedback.


## Exploration of pressure sensitivity
Notation: `0x{click}`, `0x{release}`
- `0x10`, `0x00`
  - The release is not registered. Unusable.
- `0x10`, `0x01`
  - Very lightweight.
  - There is *some* pressure left when the release is registered, but really not a lot.
- `0x03`, `0x01`
    - One can move the cursor without clicking, somewhat.
- `0x30`, `0x01`
  - The click feels normal, but it feels like the touchpad “sticks” to ones finger.
- …


## Links

- https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver
- https://github.com/ponyfleisch/hid-magictrackpad2
- https://github.com/dos1/Linux-Magic-Trackpad-2-Driver
