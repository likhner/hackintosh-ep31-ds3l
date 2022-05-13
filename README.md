# Hackintosh GA-EP31-DS3L

## Hardware

| Type         | Model                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Motherboard  | [Gigabyte GA-EP31-DS3L (rev 2.1)](https://www.gigabyte.com/Motherboard/GA-EP31-DS3L-rev-21/sp#sp)                                                                   |
| CPU          | [Intel Core 2 Duo E8500](https://ark.intel.com/content/www/us/en/ark/products/33911/intel-core2-duo-processor-e8500-6m-cache-3-16-ghz-1333-mhz-fsb.html) (Wolfdale) |
| Video card   | NVIDIA GeForce GTX 960                                                                                                                                              |
| Network card | Realtek 8139D                                                                                                                                                       |
| Sound card   | Realtek ALC888                                                                                                                                                      |

## Issues

| Issue                                             | Fixable? | Reason                                                                                  | Fix |
|---------------------------------------------------|----------|-----------------------------------------------------------------------------------------|-----|
| No sound adjustment of the video card             | ❌        | Not supported by macOS                                                                  | ❌   |
| The latest supported version is macOS High Sierra | ❌        | NVIDIA graphics cards and this generation of processor are no longer supported by macOS | ❌   |
| Unstable Internet connection                      | ❌        | Kext to the network card is taken from an older version of macOS                        | ❌   |
| Unable to fix all SSDT files                      | ❌        | Old generation processor                                                                | ❌   |
| The universal CLOVER config is used               | ❌        | Old generation processor                                                                | ❌   |
| Unable to create USB port map                     | ❌        | Unable to fix required SSDTs                                                            | ❌   |
| Bad sound quality                                 | 🤷‍♂️       | Using VoodooHDA                                                                         | 🤷‍♂️  |

## CLOVER

### Drivers

| Name                                                                                                         | Description                      |
|--------------------------------------------------------------------------------------------------------------|----------------------------------|
| [ApfsDriverLoader](https://github.com/CloverHackyColor/CloverBootloader/releases/latest)                     | Required to display APFS volumes |
| [AppleImageCodec](https://github.com/CloverHackyColor/CloverBootloader/releases/latest)                      | Required to support FileVault 2  |
| [AppleKeyAggregator](https://github.com/CloverHackyColor/CloverBootloader/releases/latest)                   | Required to support FileVault 2  |
| [AptioInputFix](https://github.com/CloverHackyColor/CloverBootloader/releases/latest)                        | Required to support FileVault 2  |
| [FirmwareVolume](https://github.com/CloverHackyColor/CloverBootloader/releases/latest)                       | Required to support FileVault 2  |
| [FSInject](https://github.com/CloverHackyColor/CloverBootloader/releases/latest)                             | Required for kexts injection     |
| [HfsPlus](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)                       | Required to display HFS volumes  |
| [OcQuirks](https://github.com/ReddestDream/OcQuirks/releases/latest)                                         | Required for NVRAM support       |
| [OpenRuntime](https://github.com/ReddestDream/OcQuirks/releases/latest)                                      | Required for NVRAM support       |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases/download/1.0.9/VirtualSMC-1.0.9-RELEASE.zip) | Apple SMC Emulator               |

### Kexts

| Name                                                                                                 | Description             |
|------------------------------------------------------------------------------------------------------|-------------------------|
| [AppleRTL8139Ethernet](CLOVER/EFI/CLOVER/kexts/Other)                                                | Kext for network card   |
| [Lilu](https://github.com/acidanthera/Lilu/releases)                                                 | Universal patcher       |
| [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)                        | USB port map            |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases/latest) (_SMCProcessor, SMCSuperIO_) | Apple SMC Emulator      |
| [VoodooHDA](https://sourceforge.net/projects/voodoohda/files/latest/download)                        | Kext for sound card     |
| [WhateverGreen](https://github.com/acidanthera/whatevergreen/releases/latest)                        | Video card patcher      |
| [VoodooPS2Controller](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/)*         | Kext for PS/2           |
| [NVIDIA Web](https://gfe.nvidia.com/mac-update)                                                      | Kext for the video card |
| [NVIDIA CUDA](https://www.nvidia.com/en-us/drivers/cuda/mac-driver-archive/)                         | Kext for CUDA           |

*Cannot be used together with `USBInjectAll`
