<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48"/>

MSI-GL62M 7RD Hackintosh
======
[![works badge](https://cdn.jsdelivr.net/gh/nikku/works-on-my-machine@v0.2.0/badge.svg)][project_link]

Hackintosh OpenCore configuration for [**MSI GL62M 7RD**][msi_overview].

With a few modifications, can work for all GL62M 7RD version *theoretically*.
Tested platform: `GL62M 7RD-223cn`.

Most of functions are working, include WIFI, Bluetooth, audio, Touchkpad, TypeC, USB, sleep and HDMI.

## Screenshots
![about][about_pic]

## Specifications
| Basic | Spec Sheet |
|--|--|
| CPU | Intel i7-7300HQ |
| GPU | HD630 (eDP) |
| Chipset | Intel HM175 |
| Audio | Realtek ALC898 |
| Ethernet | Atheros AR8175 |
| WiFi | Intel Wireless-AC3168 with Bluetooth|
| Touchkpad | Synaptics (PS2) | 
| USB controller | 100/C230 Series xHCI |

## BIOS Configuration
Make sure at least upgrade your [BIOS][msi_bios] to `E16J9IMS.324` and [Firmware][msi_firmware] up to `16J9EMS1.112`.

| Settings |  |
|--|--|
| `CFG Lock` | Disable |
| `CSM` | Disable |
| Fast Boot | Disable |
| `Intel Speed Shift`(aka. HWP) | Enable |
| Secure Boot | Disable |

**Some options only available in advanced mode:**\
In BIOS, holding **ALT + RIGHT-CTRL + SHIFT** together then press **F2**

<pre>
[Advanced] tab
├─ Power & Performance
│  └─ CPU-Power Management Control
│     ├─ <b>Intel(R) Speed Shift Technology</b>
│     └─ CPU Lock Configuration
│        └─ <b>CFG Lock</b>
└─ CSM Configuration
   └─ <b>CSM Support</b>
</pre>

## Known issues
* MiniDP
* SD card reader

## Getting Started
[OpenCore Laptop Guide][dortania_link].

## WiFi & Bluetooth
I prefer the built-in Intel card, refer [OpenIntelWireless][intel_link] and remove DW1820A related config.

If you prefer to replacing the built-in Intel card with Broadcom BCM94350ZAE/DW1820A.

Install essential [Kext][brcm].

For more details refer [osxlatitude][wlan_ts_link] and [Bluetooth Troubleshooting][bt_ts_link]

## UEFI drivers
``` c++
AudioDxe
OpenRuntime
Ps2KeyboardDxe
// HFSPlus to boot installer
```

## Post Install
[Follow Dortania guide][dortania_link_post].
And skip these parts:
``` c++
Fixing Audio // fixed
Fixing CFG Lock // unlocked in BIOS
Fixing USB // fixed
Emulated NVRAM // natively supported in GL62M 
Fixing Power Management // fixed
Fixing Battery Status // fixed
```
* Hide Picker Screen

    Disable ```Misc/Boot/ShowPicker```

* PlayChime

    Download file from [OcBinaryData][oc_boot_mp3], and place it under ```OC/Resources/Audio```.

    Enable ```UEFI/Audio/PlayChime```

## Note 
More USB ports info can be found at [SSDT-UIAC.dsl][usb_map]

[about_pic]: screenshots/About.png
[brcm]: https://github.com/0ranko0P/GL62M-7RD-Hackintosh/tree/OC_Bigsur_DW1820A/kexts#wifiac--bt4le-dw1820a
[bt_ts_link]: https://osxlatitude.com/forums/topic/11540-dw1820a-the-general-troubleshooting-thread
[dortania_link]: https://dortania.github.io/OpenCore-Install-Guide
[dortania_link_post]: https://dortania.github.io/OpenCore-Post-Install
[intel_link]: https://github.com/OpenIntelWireless
[msi_overview]: https://www.msi.com/Laptop/support/GL62M-7RD
[msi_bios]: https://www.msi.com/Laptop/support/GL62M-7RD#down-bios
[msi_firmware]: https://www.msi.com/Laptop/support/GL62M-7RD#down-firmware
[oc_boot_mp3]: https://github.com/acidanthera/OcBinaryData/blob/master/Resources/Audio/OCEFIAudio_VoiceOver_Boot.mp3
[project_link]: https://github.com/0ranko0P/GL62M-7RD-Hackintosh
[usb_map]:  https://github.com/0ranko0P/GL62M-7RD-Hackintosh/blob/OC_Bigsur_DW1820A/SSDT/deprecated/SSDT-UIAC.dsl
[wlan_ts_link]: https://osxlatitude.com/forums/topic/11322-broadcom-bcm4350-cards-under-high-sierramojavecatalina
