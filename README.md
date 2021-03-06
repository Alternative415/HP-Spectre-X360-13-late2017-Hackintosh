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
CPU | Intel i5-8250U (Kaby-Lake R)
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
* Display functions(Color, Brightness, etc)
* Wifi(with native UI): https://github.com/OpenIntelWireless/itlwm Still work in progress, but the latest alpha(1.2.0 by now) works without any hiccups for me.
* Trackpad(multitouch and gesture support): VoodooInput, VoodooPS2Controller, VoodooRMI
* Keyboard
* USB
* SD Card Reader: Might be unstable. Expect side effects when sleep/wake up.
* Webcam
* Type C to HDMI external display support
* Side volume keys
* Sidecar(Wired)

## What's partially working
* Audio: Works fine with alcid=13. However, sound is small and only the upper speakers are working. Other ids made the sound larger, but had some problems like only right side speaker working. I haven't tested all ids, so feel free to try out other numbers.
* Bluetooth: Support for Intel Bluetooth is still in early stage. Only some devices pairs, connects and works well. https://github.com/OpenIntelWireless/IntelBluetoothFirmware
* Keyboard hotkeys: Sound change, Screen Brightness change and keyboard backlight toggle works fine, media buttons don't work.
* Sleep: If you try sleeping with power supplied, it wakes up automatically. Solution is to unplug power, go to sleep and plug in. Sleep without power supply works fine with minimum battery drainage. This strange behavior is suspected to be related to Thunderbolt 3 controllers not working.

## What's not working
* Thunderbolt 3: Causes kernel panic while waking up from sleep. Disabled until further investigation.
* USB C ports' USB 3.0 support: These ports' USB 3.0 is controlled by TB3 controllers. They show up in Opencore builds and works fine, but doesn't work after sleep/waking up. Cold boot makes it work again. They don't show up in Clover builds, so never working.
* Touch Screen: Heard that it is easy to enable. I have no intention of using it in macOS, so kept it disabled.

## Notes
* I highly recommend building your own files by following Dortania's excellent guide. it will help you understand the big picture and how to use my files correctly. After you went through all the guide, you can use my files as an referance. 
* EFI is OpenCore files, CLOVER is Clover files(duh).
* The config.plists in each folder doesn't have any SMBIOS data to avoid any mixups. Please add your own. I used MacBookPro15,2. MacBookPro15,4 looks fine too.
* If it somehow failes to boot with all my files, the problem is likely to be the DSDT.aml. DSDT is known to be unique to each devices. You will have to make your own DSDT and fix it with patches. Major patches are Battery and brightness. Take a look at my DSDT to see how I patched them. You can look for tutorials by rehabman in Tonymac.

## Changelog
### 2021.01.10
- Initial Release
### 2021.01.12
- SDCard Reader now supported.(Only Clover)
- Screen Brightness Hotkeys now work. DSDT patches: https://www.tonymacx86.com/threads/guide-high-sierra-on-hp-spectre-x360-8th-gen-coffee-lake.251330/
- Fixed screen brightness only having 4 levels.
- USB Port fixup. Unused ports cleaned.
- Tweaked Clover config.plist to be more clean.

## Credits
* Dortania
* acidanthera
* Corpnewt
* WoadZS: https://github.com/WoadZS
* Rehabman
* x86.co.kr
* Tonymacx86

and many others that I have forgotten to include, sorry.
