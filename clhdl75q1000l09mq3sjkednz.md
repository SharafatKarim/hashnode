---
title: "Disable Bluetooth at startup in TLP"
datePublished: Sun May 07 2023 15:46:51 GMT+0000 (Coordinated Universal Time)
cuid: clhdl75q1000l09mq3sjkednz
slug: tlp-bluetooth
tags: linux, bluetooth, utility

---

## TLP

From the project page:

> TLP is a feature-rich command line utility for Linux, saving laptop battery power without the need to delve deeper into technical details. TLP’s default settings are already optimized for battery life and implement Powertop’s recommendations out of the box. So you may just install it and forget it. Nevertheless TLP is highly customizable to fulfil your specific requirements.

Read more from,

* [Tlp official website](https://linrunner.de/tlp/)
    
* [Arch wiki](https://wiki.archlinux.org/title/TLP)
    

# Steps

To disable Bluetooth at startup, open the following file in your preferred text editor (root privilege will be required),

```plaintext
/etc/tlp.conf
```

> For example to use `nano` text editor, your command will be, `sudo nanao /etc/tlp.conf`.

Then change,

```plaintext
RESTORE_DEVICE_STATE_ON_STARTUP=0
```

to

```plaintext
RESTORE_DEVICE_STATE_ON_STARTUP=1
```

And, also use the following line,

```plaintext
DEVICES_TO_DISABLE_ON_STARTUP="bluetooth"
```

> Don't forget to remove the '#' from the beginning of a line (removing comments).

## Example layout

Here is a basic example of my config,

```plaintext
# Restore radio device state (Bluetooth, WiFi, WWAN) from previous shutdown
# on system startup: 0=disable, 1=enable.
# Note: the parameters DEVICES_TO_DISABLE/ENABLE_ON_STARTUP/SHUTDOWN below
# are ignored when this is enabled.
# Default: 0

RESTORE_DEVICE_STATE_ON_STARTUP=1

# Radio devices to disable on startup: bluetooth, nfc, wifi, wwan.
# Separate multiple devices with spaces.
# Default: <none>

#DEVICES_TO_DISABLE_ON_STARTUP="bluetooth nfc wifi wwan"
DEVICES_TO_DISABLE_ON_STARTUP="bluetooth nfc wwan"
```

Here besides `bluetooth`, I've also disabled `nfc` and `wwan`.

## References

* [Manjaro forum - Bluetooth Turns On Automatically After Reboot!](https://forum.manjaro.org/t/bluetooth-turns-on-automatically-after-reboot/101073)