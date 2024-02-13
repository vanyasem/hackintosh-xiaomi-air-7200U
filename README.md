# Xiaomi Mi Notebook Air 13.3 7200U (2017)

**Supported macOS version:** macOS 11 - Big Sur

**SMBIOS:** MacBookPro14,2

**OpenCore:** [0.7.3](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.7.3)

Partially based on [johnnynunez/Xiaomi-Mi-Air](https://github.com/johnnynunez/Xiaomi-Mi-Air)

## Hardware

- **CPU**: Intel Core i5-7200U - **Kaby Lake**

## Notes

While the config itself is ready to use, you still need to [generate your own serial numbers and tweak the config accordingly](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios) before installing the system.

Xiaomi does not allow to change CFG lock in UEFI settings, so you will have to manually patch your UEFI to remove CFG lock. I do not remember how I did it myself, but I'm sure it's nothing a DuckDuckGo search can't solve. You might want to take a look [here](https://github.com/johnnynunez/Xiaomi-Mi-Air/tree/master/BIOS).

After installing, you might be interested in [enabling secure boot](https://dortania.github.io/OpenCore-Post-Install/universal/security/applesecureboot.html#dmgloading).

You can also [disable on-screen logging](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/debug.html#config-changes) once you're sure that your system is stable.

Boot chime is enabled.

## Bundled

[Resources](https://github.com/acidanthera/OcBinaryData) included

### Drivers

1) `AudioDxe.efi` - [HDA audio support driver](https://dortania.github.io/docs/latest/Configuration.html#audiodxe) EFI firmware for most Intel and some other analog audio controllers
2) `HfsPlus.efi` - Proprietary EFI **HFS+** file system driver
3) `OpenCanopy.efi` - OpenCore plugin (Bootloader GUI)
4) `OpenRuntime.efi` - Mandatory OpenCore plugin with [special features](https://dortania.github.io/docs/latest/Configuration.html#openruntime)

### Kexts

1) [AirportItlwm](https://github.com/OpenIntelWireless/itlwm) (**2.0.0**) - Open Intel Wireless (Wi-Fi)
2) [AppleALC](https://github.com/acidanthera/AppleALC) (**1.6.4**) - Audio for not officially supported codecs
3) [CPUFriend](https://github.com/acidanthera/CPUFriend) (**1.2.4**) - CPU power management
4) [CPUFriendDataProvider](https://github.com/corpnewt/CPUFriendFriend) (**04-Sep-2021**) - Manually generated CPUFriend tuning
5) [HibernationFixup](https://github.com/acidanthera/HibernationFixup) (**1.4.3**) - Fixes hibernation
6) [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) (**2.0.0**) - Open Intel Wireless (Bluetooth)
7) [IntelBluetoothInjector](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) (**n/a**) - Part of IntelBluetoothFirmware
8) [Lilu](https://github.com/acidanthera/Lilu) (**1.5.6**) - Required for almost all other Kexts
9) [NoTouchID](https://github.com/al3xtjames/NoTouchID) (**1.0.4**) - Lilu plugin for disabling Touch ID support
10) [NullEthernet](https://bitbucket.org/RehabMan/os-x-null-ethernet) (**1.0.6**) - "Null" (Fake) Ethernet driver to be used when you have no working Ethernet
11) [NVMeFix](https://github.com/acidanthera/NVMeFix) (**1.0.9**) - Improve compatibility with non-Apple NVMe SSDs
12) [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for measuring battery readouts
13) [SMCLightSensor](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for the ambient light sensor
14) [SMCProcessor](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for monitoring Intel CPU temperature
15) [SMCSuperIO](https://github.com/acidanthera/VirtualSMC) (**n/a**) - Part of VirtualSMC. Used for monitoring fan speed
16) [USBInjectAll](https://github.com/Sniki/OS-X-USB-Inject-All) (**0.7.5**) - Inject all USB ports for the installed Intel EHCI/XHCI chipset automatically
17) [VirtualSMC](https://github.com/acidanthera/VirtualSMC) (**1.2.7**) - SMC emulator layer
18) [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) (**2.6.5**) - Intel I2C bus controller and slave device drivers
19) [VoodooI2CHID](https://github.com/VoodooI2C/VoodooI2C) (**n/a**) - Part of VoodooI2C. Add support for I2C-HID devices
20) [VoodooPS2Controller](https://github.com/acidanthera/VoodooPS2) (**2.2.5**) - VoodooInput's Magic Trackpad II emulation
21) [WhateverGreen](https://github.com/acidanthera/WhateverGreen) (**1.5.3**) - Patches for GPUs

### Tools

1) `OpenShell.efi` - EFI shell, useful for debugging