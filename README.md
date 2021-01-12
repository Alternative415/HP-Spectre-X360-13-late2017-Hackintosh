# HP-Spectre-X360-13-late2017-Hackintosh
Custom macOS installation for HP Spectre x360 13" late 2017 (13t-ae000)

## Introduction
It is possible to install a semi-working build of macOS Big Sur (11.1) to Spectre late 2017 via Opencore(0.6.5) or Clover(r5128).

I will provide information about how I made my EFI(& CLOVER) and about what working/not working.

Hope this will help other Spectre users get engaged into the Hackintosh scene.

## Machine information
|Parts|Details
|:---:|:---:|
Model | HP Spectre x360 13-inch Late 2017 (13t-ae000)
CPU | Intel i5-8250U (Coffee Lake)
RAM | 8GB RAM
Graphics | UHD 620 Graphics
Display | 13-inch FHD Touch display
Wifi&Bluetooth | Intel Dual Band Wireless AC8265 (Wifi: 0x8086 0x24FD, Bluetooth: 0x8087 0x0AB)
Audio | Realtek ALC295
SSD | Samsung 970 EVO Plus 1TB (Originally was Intel Series 600p SSD)

## macOS information
macOS 11 Big Sur

11.1

## Bootloader information
OpenCore: 0.6.5

Clover: r5128

## What's Working
* CPU(with proper power management/HWP)
* Basic Display function
* Wifi(with native UI): https://github.com/OpenIntelWireless/itlwm
* Trackpad(multitouch and gesture support): VoodooInput, VoodooPS2Controller, VoodooRMI
* Keyboard
* USB
* SD Card Reader: Might be unstable. Expect side effects when sleep/wake up.
* Webcam
* Sleep
* Type c to HDMI external display support
* Side volume keys

## What's partially working
* Audio: Works fine with alcid=13. However, sound is small and only the upper speakers are working. Other ids made the sound larger, but had some problems like only right side speaker working. I haven't tested all ids, so feel free to try out other numbers.
* Bluetooth: Support for Intel Bluetooth is still in early stage. Only some devices pairs, connects and works well. https://github.com/OpenIntelWireless/IntelBluetoothFirmware
* Display brightness: Highest brighness isn't that high, and lowest brightness makes the backlight go off. Brightness changes in only first few steps.
* Keyboard hotkeys: Sound change, Screen Brightness change and keyboard backlight toggle works fine, media buttons don't work.

## What's not working
* Thunderbolt 3: Causes kernel panic while waking up from sleep. Disabled until further investigation.
* USB C ports' USB 3.0 support: Related to Thunderbolt controllers.
* Touch Screen: Heard that it is easy to enable. I have no intention of using it in macOS, so kept it disabled.

## Notes
* I highly recommend building your own files by following Dortania's excellent guide. it will help you understand the big picture and how to use my files correctly. After you went through all the guide, you can use my files as an referance. 
* The config.plists in each folder doesn't have any SMBIOS data to avoid any mixups. Please add your own. I used MacBookPro15,2. MacBookPro15,4 looks fine too.
* If it somehow failes to boot with all my files, the problem is likely to be the DSDT.aml. DSDT is known to be unique to each devices. You will have to make your own DSDT and fix it with patches.

## Changelog
### 2021.01.10
- Initial Release
### 2021.01.12
- SDCard Reader now supported.(Only Clover: I will focus more on clover for now. OC and their kext handing is too messed up right now.)
- Keyboard Brightness Hotkeys now work. DSDT patches: https://www.tonymacx86.com/threads/guide-high-sierra-on-hp-spectre-x360-8th-gen-coffee-lake.251330/

## Credits
* Dortania
* acidanthera
* Corpnewt
* WoadZS: https://github.com/WoadZS
* Rehabman
* x86.co.kr

and many others that I have forgotten to include, sorry.
