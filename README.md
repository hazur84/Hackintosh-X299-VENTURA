# HACKINTOSH X299 MAC OS VENTURA 13.1 - OPENCORE 0.86

## Setup

1. Placa Madre [ROG RAMPAGE VI APEX](https://rog.asus.com/motherboards/rog-rampage/rog-rampage-vi-apex-model/) [BIOS 3701](https://rog.asus.com/motherboards/rog-rampage/rog-rampage-vi-apex-model/helpdesk_bios/)
2. CPU Core I9-9920X (3.5GHz @ 165W, Cache L3:19.25M, 12 Cores)
3. RAM 64Gb 30000 Mhz XPG DDR4
4. Case Cooler Master
5. WiFi card BCM943602

# Hardware

GPU Recomendados
https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/amd-gpu.html#native-amd-gpus

1. AMD WX 5100; 7100; 9100 (Mojave o Superior)
1. AMD RX VEGA 56; 64 (Mojave o Superior)
1. AMD RX 5XX (560; 570; 580; 590) (Mojave o Superior)
5. AMD RX 5X00 XT (5500; 5600; 5700) (Catalina o superior)
8. AMD RX 6600 XT (Monterey 12.1 o superior)
9. AMD RX 6800 y 6900 XT (Big Sur o superior)

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

# Descargas principales

1. OpenCore https://github.com/acidanthera/OpenCorePkg/releases
1. ProperTree to edit .plist files 
1. GenSMBIOS to generating our SMBIOS data
2. Mount EFI to mount EFI partitions 
3. Kext Updater to update kext files https://www.sl-soft.de/en/kext-updater/

# USB Instalacion

1. Descargar Sistema Operativo

Ejecutar en la terminal:

mkdir -p ~/macOS-installer && cd ~/macOS-installer && curl https://raw.githubusercontent.com/munki/macadmin-scripts/main/installinstallmacos.py > installinstallmacos.py && sudo python3 installinstallmacos.py

<img width="571" alt="DownloadVentura" src="https://user-images.githubusercontent.com/8379954/209476932-c78883e3-38d5-483e-9ee1-42f173c74372.png">

Leer este tutorial para crear el disco usb de arranque e instalaciòn:
https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#downloading-macos-modern-os

1. Monte la particion EFI de la USB y pegue las siguientes carpetas:

- BOOT
- OC

# Prerequisitos y actualizaciones
https://dortania.github.io/OpenCore-Install-Guide/extras/monterey.html

