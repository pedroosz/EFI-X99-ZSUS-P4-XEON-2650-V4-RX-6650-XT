# EFI ZSUS P4 X99 (C612) + XEON 2650 V4 + RX 6650 XT

## Hardware Specs

| Type | Name |
| --- | --- |
| CPU | Intel Xeon 2650 V4 |
| GPU | AMD Radeon RX 6650 XT |
| RAM | 16 GB (2 x 8 GB) |
| SSD | 512 GB |
| WiFi | Intel Wireless-AC 7260 |
| Motherboard | ZSUS P4 (Commonly sold as X99 but has a C612 chipset) |

## Kexts included

- [x] AppleALC
- [x] CpuTscSync
- [x] itlwm
- [x] Lilu
- [x] NVMeFix
- [x] RealtekRTL8111
- [x] RestrictEvents
- [x] SMCProcessor
- [x] SMCRadeonGPU
- [x] SMCSuperIO
- [x] USBToolBox
- [x] VirtualSMC
- [x] WhateverGreen
- [x] XHCI-unsupported

> **NOTE FOR INTEL WIFI USERS:** 
> You **MUST** add the AirportItlwm kext from Ventura and remove itlwm from this EFI to use WiFi in the installer.

## Quirks and what I've found

- I've not found a way to use 4 sticks of ram, I can use 4x8 (32GB) sticks on other OSes (Windows and Linux) but not on macOS, because of that I'm using 2x8. Maybe I'm missing something, but I don't know what and have not found a solution to the day of writing this.

- As I can't use the native WiFi interface due to AirportItlwm not having a release for Sequoia yet, I had to install Ventura first, and then update to Sequoia **AFTER** installing Heliport, adding the itlwm kext and removing the AirportItlwm kext from Ventura.

## Preparing the EFI

1. Download the EFI
2. Follow the steps from dorthania's guide [here](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
3. Once you have set up your Pendrive continue to Preparing your BIOS, and then proceed to boot into the recovery image.

## Preparing your BIOS:

| Path | Value |
| --- | --- |
Advanced -> Above 4G Decoding |  Enable
Advanced -> USB Configuration -> XHCI Hand-off | Enable
Advanced -> USB Configuration -> EHCI Hand-off | Enable
IntelRSCSetup -> Processor Configuration -> MSR Lock Control | Disable
IntelRSCSetup -> Processor Configuration -> PCH Sata Configuration -> Configure SATA as | AHCI
Security -> Secure Boot | Disabled
Boot -> Fast Boot | Disabled
