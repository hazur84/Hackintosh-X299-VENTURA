# Hackintosh X299 MacOS Sequoia 15.3 - RX6600XT - OC 1.0.3 (29/jan/2025)

![Screenshot 2024-08-20 at 17 55 58](https://github.com/user-attachments/assets/b92cc91a-a0cc-41c9-979a-32befd6cb0ba)

# UPDATES or UPGRADES:
1. Change SecureBootModel to Disaable value. 
1. Change csr-active-config to 03080000 to  disable System Integrity Protection (SIP) before install updates or apply root patches with OCLP.

After successfull update or upgrade you can revert values.
1. Change SecureBootModel to Default value.
2. Change csr-active-config to 00000000 to enable System Integrity Protection (SIP).

# CHANGELOG:
1. OpenCore 1.0.3 (29/jan/2025)
   - MacOs Sequoia test 15.3 OK
   - MacOs Sonoma 14.7.3 OK
1. OpenCore 1.0.1 (20/ago/2024)
   - MacOs Sonoma test 14.6.1 OK
1. OpenCore 1.0 (28/may/2024)
   - MacOs Sonoma test 14.5 OK
   - Add CPUINFO Model in About This Mac, thanks, [frontgear](https://www.tonymacx86.com/threads/solved-processor-name-missing-from-about-this-mac-screen.327255/)
1. OperCore 0.9.9 (21/april/2024)
   - MacOs Sonoma test 14.4.1 OK
1. OpenCore 0.9.7 (30/Dec/2023)
   - MacOS Ventura 13.6.1 test OK
   - MacOs Sonoma test 14.2.1 OK
   - Upgrade OpenCore, thanks, [Ani JD, Youtbe Channel](https://www.youtube.com/watch?v=RZF75faxqTQ)
[OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools)
1. OpenCore 0.8.6 (07/jan/2023)
   - MacOS Ventura test OK
   - Upgrade OpenCore, thanks, [SHINOKI77](https://github.com/shinoki77/ASUS-X299-Hackintosh/tree/main/BASE-EFI)

# MAC OS SONOMA INSTALATION

## What's not working?
Fenvi T919 Wi-Fi: macOS Sonoma has dropped support for all Broadcom Wi-Fi present on Macs before 2017. Fenvi T919 and HB1200 have BCM4360 chipsets (not supported) so Wi-Fi does not work in Sonoma. Bluetooth works fine. This is a serious inconvenience because functions related to the Apple ecosystem (Airdrop, Continuity Camera, etc.) are also lost. The only option to fix is using OCLP patch.

## Installing macOS Sonoma

1. Upgrade from macOS Ventura 13.4 or later:
   - System Settings >> Software Update >> Beta Updates >> click on the info icon >> Disabled
   - Choose macOS Sonoma 14.0
   - Or get the app from App Store.

2. Install from scratch:
   - Creating USB boot media to install from scratch ( [USB pendrive instalation](#usb-pendrive-instalation) section ).
   - Reboot from the USB device and begin Sonoma installation.

## OpenCore and EFI folder
Update OpenCore and kexts to Sonoma compatible versions. OpenCore, at least version 1.0.1 Settings used with macOS Ventura may work with macOS Sonoma. Updating OpenCore and kexts, there are no significant changes to the config.plist file, which may be the same for both systems.

For the update to be successful, 2 parameters in config.plist related to security must be adjusted:

 - SecureBootModel=Default or x86legacy (Apple Secure Boot as Default sets the same model as in SMBIOS and x86legacy is designed for SMBIOS that lack T2 chip and virtual machines)
 - SIP enabled (csr-active-config=00000000.

It is advisable to have Gatekeeper enabled (sudo spctl –master-enable in Terminal). Note: in last versions of Ventura, sudo spctl –master-enable (or disable) has been replaced by sudo spctl –global-enable (or disable). For now, both commands work fine.

These security options can be changed after installation as they are not required out of updating macOS.

## Notes about software updates

1. Getting Update notification
   - iMacPro1,1 (iMac Pro 27″, late 2017) models do have a T2 chip and, when using these SMBIOS models, you do not receive update notifications
   - iMacPro1,1 models receive update notifications if configured as vmm (virtual machine): revpatch=sbvmm in boot-args along with RestrictEvents.kext.

2. Size of the update (full or incremental)
   - Systems where the OCLP root patch has not been applied or has been reverted:
   - iMacPro1,1 require revpatch=sbvmm in boot-args along with RestrictEvents.kext to get incremental updates, without this setting you get full-size updates
   - All systems that have the OCLP root patch applied receive full-size updates.

After the system is updated, RestrictEvents.kext and the boot argument can be disabled because they are not required for normal Sonoma operation.

CREDITS: 
1. [PEREZ987](https://perez987.es/macos-14-sonoma-en-z390-aorus-elite/)
2. [PEREZ987 GITHUB](https://github.com/perez987/macOS-14-Sonoma-on-z390-with-OpenCore)
4. [Hackintosh v3](https://github.com/shiruken/hackintosh?tab=readme-ov-file)
5. [CPU INFO MODEL](https://github.com/acidanthera/RestrictEvents)
6. [Learn OCAuxiliaryTools](https://github.com/5T33Z0/OC-Little-Translated)
7. [Fixing audio with AppleALC](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html)


## SETUP

1. Motherboard [ROG RAMPAGE VI APEX](https://rog.asus.com/motherboards/rog-rampage/rog-rampage-vi-apex-model/) - [BIOS 3801] (https://rog.asus.com/motherboards/rog-rampage/rog-rampage-vi-apex-model/helpdesk_bios/)
1. CPU [Intel® Core™ i9-9920X](https://www.intel.com/content/www/us/en/products/sku/189127/intel-core-i99920x-xseries-processor-19-25m-cache-up-to-4-50-ghz/specifications.html) (3.5GHz @ 165W, Cache L3:19.25M, 12 Cores)
1. RAM 64Gb 16Gb x4 @ 3,600 Mhz [XPG D60G](https://www.xpg.com/us/xpg/843) DDR4 Quad Channel
1. GPU [NITRO+ AMD Radeon™ RX 6600 XT](https://www.sapphiretech.com.cn/en/consumer/nitro-radeon-rx-6600-xt-8g-gddr6) 8Gb
1. PSU [CORSAIR HX650](https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/hx-series-config/p/CP-9020030-NA) 650 Watt 80 PLUS® Gold Certified, (change fan Noctua NF-P14s)
1. SSD M2 2TB [SN350](https://www.westerndigital.com/es-la/products/internal-drives/wd-green-sn350-nvme-ssd?sku=WDS200T3G0C) WESTERN DIGITAL (Mac OS 14) Read: 3200MB/s ; Write: 3000MB/s
1. SSD M2 1TB [KXG60ZNV1T02](https://americas.kioxia.com/es-lar/business/ssd/client-ssd/xg6.html) KIOXA (WINDOWS 11) Read: 3,180 MB/s ; Write: 2,960 MB/s
1. Case Cooler Master [MASTERBOX Q500L](https://www.coolermaster.com/la/es-la/catalog/cases/mid-tower/masterbox-q500l/)
1. Cooler Master MasterLiquid [ML280](https://www.amazon.com.mx/gp/product/B08BV2RHZW/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) (change fan Noctua NF-P14s) for CPU
2. Cooler Master MaserLiquid [ML240](https://www.amazon.com.mx/ENFRIAMIENTO-LIQUEDO-COOLER-MASTER-MLW-D24M-A18PZ-R1/dp/B0C4BZQG8P/ref=sr_1_3?__mk_es_MX=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=8QXZSPDZ6T0Z&keywords=ML240&sprefix=ml240%2Caps%2C138&sr=8-3&ufe=app_do%3Aamzn1.fos.4e545b5e-1d45-498b-8193-a253464ffa47&th=1) for GPU
3. NZXT KRAKEN G12 [NZXT KRAKEN G12](https://www.amazon.com.mx/NZXT-Kraken-G12-GPU-Enfriamiento-rl-krg12-b1/dp/B06ZYHRMYP/ref=sr_1_1?crid=17O3EKOW5JNCO&keywords=nzxt%2Bkraken%2Bg12&sprefix=NZXT%2BG12%2Caps%2C3835&sr=8-1&ufe=app_do%3Aamzn1.fos.4e545b5e-1d45-498b-8193-a253464ffa47&th=1)
4. Fans Noctua 1400mm x3 [NF-P14s](https://www.amazon.com.mx/gp/product/B00KF7O58G/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
5. Fans Noctua 120mm x3 [NF-P12](https://www.amazon.com.mx/gp/product/B07CG2PGY6/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
6. Fans Noctua 60mm x2 [NF-A6x25](https://www.amazon.com.mx/gp/product/B00VXTANZ4/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
7. Fans Noctua 92mm x1 [NF-B9](https://www.amazon.com.mx/Noctua-NF-B9-redux-1600-PWM-Ventilador/dp/B00KF7S9F6/ref=sr_1_3?__mk_es_MX=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=3158ITVJGOVPM&keywords=noctua+92mm&sprefix=noctua+92mm%2Caps%2C163&sr=8-3&ufe=app_do%3Aamzn1.fos.4e545b5e-1d45-498b-8193-a253464ffa47) 
8. WiFi card [BCM943602](https://www.amazon.com.mx/Willhom-BCM94360CS2-Bluetooth-Wireless-661-7465/dp/B07BQ976CR/ref=sr_1_5?keywords=BCM943602&qid=1673330954&sr=8-5) with [pcie bracket](https://www.amazon.com.mx/BCM943224PCIEBT2-bcm94360CS2-BCM943602CS-Bluetooth-Hackintosh/dp/B07CZFVWSZ/ref=sr_1_3?__mk_es_MX=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=37UM2475ZG6IB&keywords=bcm94360CS2&qid=1673331306&sprefix=bcm94360cs2%2Caps%2C95&sr=8-3)

## PHERIPHERALS

1. Magic Trackpad
1. Logitech Keyboard MX
1. Plantronics Diadema USB
1. WebCam Logitech Brio; C92 PRO
1. TV LG OLED EVO 42 [OLED42C2PSA](https://www.lg.com/mx/televisores/lg-oled42c2psa) HDMI 2.1 4K@120HZ

![About This Mac](https://github.com/user-attachments/assets/929d85a5-209b-4dc8-a91a-18c7e3232760)


![WhatsApp Image 2024-01-02 at 12 48 59](https://github.com/hazur84/Hackintosh-X299-VENTURA/assets/8379954/2e72378f-933a-4944-9ba3-fcf33e039ca6)

# HARDWARE FOR OTHERS SIMILAR SETUP X299

Please check [GPU Buyer's Guide](
https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/amd-gpu.html#native-amd-gpus) compatible with MacOS Ventura

1. AMD WX X100 (4100; 5100; 7100; 9100)
1. AMD RX VEGA (56; 64) 
1. AMD RX 5XX (560; 570; 580; 590) 
1. AMD RX 5X00 XT (5500; 5600; 5700) 
1. AMD RX 6X00 XT (6600; 6800; 6900) this series only support hdmi 2.1 4k@120hz
1. AMD RX 6X00 XT (6400; 6500; 6650, 6700) this series avoid, not working in macos

Avoid this hard drives, please review this [link](https://elitemacx86.com/threads/storage-compatibility-for-macos.875/):

1. Anything HDSSD eMMC.
1. Samsung PM981 y PM991 
1. Micron 2200S
1. SKHynix PC711
1. Samsung 970 Evo Plus
1. Intel 600p

Hard drives verified:

1. Western Digital [SNXXX](https://www.westerndigital.com/products/internal-drives/pc-sn730-ssd#specifications) 
1. Kioxa / Toshiba [KXG60ZNVXXXX](https://americas.kioxia.com/es-lar/business/ssd/client-ssd/xg6.html)
4. Patriot

WiFi cards supported (avoid all others):

BCM943XXX (BCM94350, BCM94352; BCM94360; BCM943602)

# SETUP BIOS MOTHERBOARD

Reset to Default Settings before adjusting to these settings. It is recommended to use one of the more recent BIOS revisions.

- AI Tweaker
  - AI Overclock Tuner - XMP
  - CPU SVID Support - Enabled

- Advanced
  - CPU Configuration
    - MSR Lock Control - Disabled
  - CPU Power Management Configuration
      - Enhanced Intel SpeedStep Technology - Enabled
      - Turbo Mode - Enabled
      - Autonomous Core C-State - Enabled
      - Enhanced Halt State (C1E) - Enabled
      - CPU C6 Report - Enabled
      - Package C State - C6(non Retention) state
      - Intel(R) Speed Shift Technology - Enabled
      - MFC Mode Override - OS Native Support

  - System Agent (SA) Configuration
    - Intel VT for Directed I/O (VT-d) - Enabled

  - PCI Subsystem Settings
    - Above 4G Decoding - Enabled
    - Re-Size BAR Support - Auto

  - PCH Storage Configuration
    - SATA Mode Selection - AHCI

- Boot
  - CSM (Compatability Support Module)
    - Launch CSM - Disabled

- Secure Boot
    - OS Type / Other OS


# USB pendrive instalation

1. Check this [tutorial](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#downloading-macos-modern-os) for create usb boot of instalation.

1. Mount the partition USB EFI with [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) or [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools)

2. Download the file EFI.zip on this Github project.

3. Unzip the file EFI.zip into USB EFI partition.

4. Setup the file config.plist 

# Setup file config.plist

You will need to create your own Serial Number and SMUUID. Instructions can be found [here](https://dortania.github.io/OpenCore-Install-Guide/config-HEDT/skylake-x.html#platforminfo). Remember to adjust the SMBIOS a iMacPro1,1

<img width="682" alt="Screenshot 2022-12-26 at 17 16 27" src="https://user-images.githubusercontent.com/8379954/209587973-53dde243-87b7-43ab-aec8-29a67f152e95.png">

Reboot and accesss to BIOS, insert usb pendrive and setup first boot then, setup hard drive instalation second boot.

# RX5X00 (5500; 5600; 5700) and RX6X00 (6600; 6800; 6900)

AMD RX 6600 on Ventura with MacPro or iMacPro SMBIOS
AMD Navi cards run fine on Ventura when using iMac SMBIOS with **agdpmod=pikera** in boot args as the only needed setting. But when using MacPro or iMacPro SMBIOS a lot of users have reported black screen. The simplest way to fix this is to add in DeviceProperties of config.plist properties that set Henbury framebuffer for each of the 4 ports of this GPU.

<img width="956" alt="Screenshot 2023-01-06 at 11 57 31" src="https://user-images.githubusercontent.com/8379954/211070820-06f5ce09-feb8-4646-b36f-c474d2e2ec1c.png">

By default, Radeon framebuffer (ATY,Radeon) is loaded. But, in AMDRadeonX6000Framebuffer.kext >> Contents >> Info.plist we can see that AMDRadeonNavi23Controller has ATY,Henbury and 6600 series are Navi 23. This is why this framebuffer is selected.

The patch is added in this way:

<img width="961" alt="Screenshot 2023-01-06 at 11 44 37" src="https://user-images.githubusercontent.com/8379954/211068826-b8cc5216-a3d7-4de2-9ffe-ce89935ac110.png">

```js
<key>DeviceProperties</key>
    <dict>
        <key>Add</key>
        <dict>
            <key>PciRoot(0x1)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x0,0x0)/Pci(0x0,0x0)</key>
            <dict>
                <key>@0,name</key>
                <string>ATY,Henbury</string>
                <key>@1,name</key>
                <string>ATY,Henbury</string>
                <key>@2,name</key>
                <string>ATY,Henbury</string>
                <key>@3,name</key>
                <string>ATY,Henbury</string>
            </dict>
        </dict>
        <key>Delete</key>
        <dict/>
    </dict>
```

Notes:

PCI path to the GPU may be the same on your system but it is convenient to check it with [Hackintool](https://github.com/benbaker76/Hackintool)

<img width="1821" alt="Screenshot 2023-01-06 at 11 08 05" src="https://user-images.githubusercontent.com/8379954/211068020-e24e546e-e7f7-48bb-a236-47b55334f85b.png">

If needed for other Navi cards, the framebuffers to be loaded are different for each family:

|GPU  |value       |
|-----|------------|   
|5500	|ATY,Python  |
|5600 |ATY,Sunbeam |
|5700	|ATY,Adder   |  
|6600	|ATY,Henbury |
|6800	|ATY,Belknap |
|6900	|ATY,Carswell|


# Problems with USB ports
Please use [this](https://dortania.github.io/OpenCore-Post-Install/usb/intel-mapping/intel.html) as a proper guide to map your USB ports.

# Prerequisites and Open Core upgrades
https://dortania.github.io/OpenCore-Install-Guide/extras/monterey.html

# Tools Downloads

1. [OpenCore 1.0](https://github.com/acidanthera/OpenCorePkg/releases/download/1.0.1/OpenCore-1.0.1-RELEASE.zip) (inside find Referece Manual in /Docs/Configuration.pdf)
1. [OpenCore Reference Manual 1.0](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Configuration.pdf)
1. [ProperTree](https://github.com/corpnewt/ProperTree) to edit .plist files 
1. [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generating our SMBIOS data
1. [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) Mount EFI to mount EFI partitions and edit config.plist
1. [Mount EFI](https://github.com/corpnewt/MountEFI) Mount EFI terminal
2. [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools) Mount EFI terminal
1. [Kext Updater](https://www.sl-soft.de/en/kext-updater/) to update kext files
1. [HackinTool](https://github.com/benbaker76/Hackintool) to know PCI Path

# OTHERS

Disable Gatekeeper With Terminal
1. Launch Terminal from Applications > Utilities.
2. Enter the following command: sudo spctl --master-disable

# CREDITS

1. [SHINOKI77](https://github.com/shinoki77/ASUS-X299-Hackintosh/tree/main/BASE-EFI)
1. [Setup RX6600XT in Ventura](https://github.com/perez987/macOS-12-13-on-Z390-with-OpenCore)
1. [PEREZ987](https://github.com/perez987/6600XT-on-macOS-12-13-with-PowerPlayTable) framebuffer navicards

# TO DO
Upgrade code to OPENCORE (someone wants to help?)

Review this link [Updating OpenCore and macOS](https://dortania.github.io/OpenCore-Post-Install/universal/update.html#updating-opencore)
