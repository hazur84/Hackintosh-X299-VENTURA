# HACKINTOSH X299 MAC OS VENTURA 13.1 - OPENCORE 0.86 (26/dic/2022)

## Setup

1. Placa Madre [ROG RAMPAGE VI APEX](https://rog.asus.com/motherboards/rog-rampage/rog-rampage-vi-apex-model/) - [BIOS 3701](https://rog.asus.com/motherboards/rog-rampage/rog-rampage-vi-apex-model/helpdesk_bios/)
1. GPU GygaByte RX590 8Gb
1. SSD M2 1TB WD730SN WESTERN DIGITAL (HACKINTOSH)
1. SSD M2 1TB WD730SN WESTERN DIGITAL (WINDOWS 11)
1. CPU Core I9-9920X (3.5GHz @ 165W, Cache L3:19.25M, 12 Cores)
1. RAM 64Gb 16Gbx4 @ 3,000 Mhz XPG DDR4
1. Case Cooler Master [MASTERBOX Q500L](https://www.coolermaster.com/la/es-la/catalog/cases/mid-tower/masterbox-q500l/)
1. WiFi card BCM943602 con adaptaor pcie

<img width="392" alt="MacOsVentura" src="https://user-images.githubusercontent.com/8379954/209585330-9cca7e25-83f8-49d4-83cf-e5242acfb1ef.png">

# HARDWARE

[Guía de GPU Recomendados](
https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/amd-gpu.html#native-amd-gpus) con MacOS Ventura

1. AMD WX 5100; 7100; 9100
1. AMD RX VEGA 56; 64 
1. AMD RX 5XX (560; 570; 580; 590) 
1. AMD RX 5X00 XT (5500; 5600; 5700) 
1. AMD RX 6600; 6600XT 
1. AMD RX 6800 XT y 6900 XT

Evitar estos discos duros:

1. Cualquier almacenamiento basado en eMMC.
1. Samsung PM981 y PM991 
1. Micron 2200S
1. SKHynix PC711
1. Samsung 970 Evo Plus
1. Intel 600p

Discos provados y recomendados:

1. SN730 Western Digital (R: 3,400 MB/S; W: 2,700 MB/s)
1. SN750 Western Digital
1. Kioxa / Toshiba KXG6AZNV (R: 3,100 MB/S; W: 2,800 MB/s)
1. Patriot

Modelos de tarjetas WiFi ecomendados (evitar todas las demás):

1. BCM943602
1. BCM94360
1. BCM94352
1. BCM94350

## Perifericos

1. Magic Trackpad ($100 USD)
1. Logitech Keyboard MX ($100 USD)
1. Plantronics Diadema USB
1. WebCam Logitech Brio; C92 PRO ($50 USD)
1. TV LG OLED EVO 42 ($1000 USD)

# CONFIGURACION DEL BIOS DE LA PLACA MADRE

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

# USB Instalacion

1. Revise este [tutorial](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#downloading-macos-modern-os) para crear el disco usb de arranque e instalaciòn.

1. Monte la particion EFI de la USB con [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) 

2. Descargue el archivo EFI.zip de este proyecto Github 

3. Descomprima en la particion EFI de la USB.

# Configuracion del archivo config.plist

You will need to create your own Serial Number and SMUUID. Instructions can be found [here](https://dortania.github.io/OpenCore-Install-Guide/config-HEDT/skylake-x.html#platforminfo). Remember to adjust the SMBIOS a iMacPro1,1
<img width="682" alt="Screenshot 2022-12-26 at 17 16 27" src="https://user-images.githubusercontent.com/8379954/209587973-53dde243-87b7-43ab-aec8-29a67f152e95.png">
Reinicie y acceda al bios, coloque la memoria usb como primer boot y el disco duro de instalacion como el segundo boot.

# Prerequisitos y actualizaciones
https://dortania.github.io/OpenCore-Install-Guide/extras/monterey.html

# Descargas principales

1. [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases)
1. ProperTree to edit .plist files 
1. [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generating our SMBIOS data
2. [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/) Mount EFI to mount EFI partitions 
3. [Kext Updater](https://www.sl-soft.de/en/kext-updater/) to update kext files 

# CREDITS

SHINOKI77
https://github.com/shinoki77/ASUS-X299-Hackintosh/tree/main/BASE-EFI
