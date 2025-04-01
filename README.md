# Xiaomi Mi Notebook Air 13.3 7200U (2017)

**Supported macOS version:** macOS 12 - Monterey, macOS 13 - Ventura, macOS 14 - Sonoma (including 14.4+)

**SMBIOS:** MacBookPro15,4

**OpenCore:** [1.0.4](https://github.com/acidanthera/OpenCorePkg/releases/tag/1.0.4)

Partially based on [johnnynunez/Xiaomi-Mi-Air](https://github.com/johnnynunez/Xiaomi-Mi-Air)

## Updating

If you are updating from macOS 13 (Ventura), pay attention to the fact that the SMBIOS has changed in order to receive the Sonoma update.

Before updating the EFI, log out of iCloud. You can also delete iCloud leftovers by following [this guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#clean-out-old-attempts) for extra safety. Afterward, regenerate the serial number with `GenSMBIOS` (as described in the Notes section below).

After updating the EFI, reset NVRAM on first boot (press spacebar on the boot picker, and select `Reset NVRAM`).

Proceed with the update as you normally would on a Mac. Open System Settings, check for updates, and install Sonoma. Then log back into iCloud. Your PC will be detected as an entirely new device. Make sure to delete stale login entries from your device list.

## Status

Mostly perfect. Apart from the fact that the hardware itself is old and slow.

### Working

- Wi-Fi
- Bluetooth _(except for AirDrop, Handoff, Continuity)_
- TouchPad _(including gestures)_
- iGPU
- Keyboard _(including special keys)_
- Screen _(including brightness & Night Shift)_
- HDMI/AUX outputs _(with resolution up to 1440p)_
- USB ports _(including USB Type-C hubs)_
- Sleep
- Built-in camera, microphone, speakers
- Battery management
- FileVault

### Not working

- TouchID _(see <https://github.com/johnnync13/Xiaomi-Mi-Air/issues/94>)_
- dGPU _(will never work)_

## Hardware

- **CPU**: Intel Core i5-7200U - **Kaby Lake**

## Notes

While the config itself is ready to use, you still need to [generate your own serial numbers and tweak the configuration accordingly](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios) before installing the system.

Xiaomi does not allow changing CFG lock in UEFI settings, so you must manually patch your UEFI to remove CFG lock. I don't remember how I did it myself, but I'm sure it's nothing a DuckDuckGo search can't solve. You might want to take a look [here](https://github.com/johnnynunez/Xiaomi-Mi-Air/tree/master/BIOS).

After installation, consider [enabling secure boot](https://dortania.github.io/OpenCore-Post-Install/universal/security/applesecureboot.html#dmgloading).

You can also [disable on-screen logging](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html#config-changes) once you’re sure your system is stable.

Boot chime is enabled.

## Bundled

[Resources](https://github.com/acidanthera/OcBinaryData) included _(except for voiceovers)_

### Drivers

1) `AudioDxe.efi` - [HDA audio support driver](https://dortania.github.io/docs/latest/Configuration.html#audiodxe) EFI firmware for most Intel and some other analog audio controllers
2) `HfsPlus.efi` - Proprietary EFI **HFS+** file system driver
3) `OpenCanopy.efi` - OpenCore plugin (Bootloader GUI)
4) `OpenRuntime.efi` - Mandatory OpenCore plugin with [special features](https://dortania.github.io/docs/latest/Configuration.html#openruntime)
5) `ResetNvramEntry.efi` - OpenCore plugin, adds [ResetNvram](https://dortania.github.io/docs/latest/Configuration.html#resetnvramentry) entry to the boot menu
6) `ToggleSipEntry.efi` - OpenCore plugin, adds [ToggleSip](https://dortania.github.io/docs/latest/Configuration.html#togglesipentry) entry to the boot menu

### Kexts

1) [AirportItlwm](https://github.com/OpenIntelWireless/itlwm) (**2.3.0**) - Open Intel Wireless (Wi-Fi)
2) [AppleALC](https://github.com/acidanthera/AppleALC) (**1.9.4**) - Audio for codecs that are not officially supported
3) [CPUFriend](https://github.com/acidanthera/CPUFriend) (**1.2.9**) - CPU power management
4) [CPUFriendDataProvider](https://github.com/corpnewt/CPUFriendFriend) (**04-Sep-2021**) - Manually generated CPUFriend tuning
5) [HibernationFixup](https://github.com/acidanthera/HibernationFixup) (**1.5.2**) - Fixes hibernation
6) [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) (**2.4.0**) - Open Intel Wireless (Bluetooth)
7) [IntelBTPatcher](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) (**n/a**) - Part of IntelBluetoothFirmware. Required for Monterey and later
8) [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM) (**2.6.9**) - Required for Monterey and later
9) [Lilu](https://github.com/acidanthera/Lilu) (**1.7.0**) - Required for almost all other Kexts
10) [NullEthernet](https://bitbucket.org/RehabMan/os-x-null-ethernet) (**1.0.6**) - "Null" (Fake) Ethernet driver to be used when you have no working Ethernet
11) [NVMeFix](https://github.com/acidanthera/NVMeFix) (**1.1.2**) - Improve compatibility with non-Apple NVMe SSDs
12) [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for measuring battery readouts
13) [SMCLightSensor](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for the ambient light sensor
14) [SMCProcessor](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for monitoring Intel CPU temperature
15) [SMCSuperIO](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for monitoring fan speed
16) [USBInjectAll](https://github.com/Sniki/OS-X-USB-Inject-All) (**0.7.6**) - Inject all USB ports for the installed Intel EHCI/XHCI chipset automatically
17) [VirtualSMC](https://github.com/acidanthera/VirtualSMC) (**1.3.5**) - SMC emulator layer
18) [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) (**2.9.1**) - Intel I2C bus controller and slave device drivers
19) [VoodooI2CHID](https://github.com/VoodooI2C/VoodooI2C) (**n/a**) - Part of VoodooI2C. Add support for I2C-HID devices
20) [VoodooPS2Controller](https://github.com/acidanthera/VoodooPS2) (**2.3.7**) - VoodooInput's Magic Trackpad II emulation
21) [WhateverGreen](https://github.com/acidanthera/WhateverGreen) (**1.6.9**) - Patches for GPUs

### Tools

1) `OpenShell.efi` - EFI shell, useful for debugging
2) `CleanNvram.efi` - completely clears NVRAM, useful when NVRAM got corrupted
