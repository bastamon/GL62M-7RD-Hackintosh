MSI-GL62M 7RD Hackintosh
======
[![works badge](https://cdn.jsdelivr.net/gh/nikku/works-on-my-machine@v0.2.0/badge.svg)][project_link]

Hackintosh clover configuration for [**MSI GL62M 7RD**][msi_overview].

With a few modifications, can work for all GL62M 7RD version *theoretically*.
Tested platform: `GL62M 7RD-223cn`.

Most of functions are working, include built-in camera, audio, Touchkpad, sleep and HDMI.

## Specifications
| Basic | Spec Sheet |
|--|--|
| CPU | Intel i7-7700HQ |
| GPU | HD630 (eDP) |
| Chipset | Intel HM175 |
| Audio | Realtek ALC898 |
| Ethernet | Atheros AR8175 |
| WiFi | Broadcom BCM94350ZAE/DW1820A (M.2 2230) |
| Touchkpad | Synaptics (PS2) | 
| USB controller | 100/C230 Series xHCI |

## Before installation
Make sure at least upgrade your [BIOS][msi_bios] to `E16J9IMS.324` and [Firmware][msi_firmware] up to `16J9EMS1.112`.

## Known issues
* MiniDP
* SD card reader

## WiFi & Bluetooth
Replace built-in Intel card to Broadcom BCM94350ZAE/DW1820A.

How to tear down: [Youtube][tear_down] (This video is for `7REX 1252`, but the procedure is very similar.).
![tear down][tear_down_pic]

Download modified [BrcmPatchRAM kext][brcm] by [headkaze].

## UEFI drivers
``` c++
ApfsDriverLoader
AudioDxe
FSInject
OsxAptioFix3Drv
VirtualSmc
// HFSPlus if clover is going to boot from USB
```
> Note: SMCHelper.efi is not compatible with VirtualSMC.efi and must be removed

## Note 
More USB ports info can be found at [SSDT-UIAC.dsl][usb_map]

[brcm]: https://github.com/0ranko0P/GL62M-7RD-Hackintosh/tree/mojave_DW1820A/kexts#wifiac--bt4le
[headkaze]: https://github.com/headkaze
[tear_down]: https://www.youtube.com/watch?v=-WHgFWf_66A
[tear_down_pic]: https://raw.githubusercontent.com/0ranko0P/GL62M-7RD-Hackintosh/mojave_DW1820A/Tear_down.png
[wifi_guide]: https://www.tonymacx86.com/threads/broadcom-wifi-bluetooth-guide.242423
[msi_overview]: https://www.msi.com/Laptop/support/GL62M-7RD
[msi_bios]: https://www.msi.com/Laptop/support/GL62M-7RD#down-bios
[msi_firmware]: https://www.msi.com/Laptop/support/GL62M-7RD#down-firmware
[project_link]: https://github.com/0ranko0P/GL62M-7RD-Hackintosh
[usb_map]:  https://github.com/0ranko0P/GL62M-7RD-Hackintosh/blob/master/hotpatchs/deprecated/SSDT-UIAC.dsl
