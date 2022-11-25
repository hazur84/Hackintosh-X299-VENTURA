# Hackintosh-X299-VENTURA
X299 VENTURA OPENCORE 0.86

# Descargas principales

1. OpenCore https://github.com/acidanthera/OpenCorePkg/releases
1. ProperTree to edit .plist files 
1. GenSMBIOS For generating our SMBIOS data
2. Mount EFI


## Hardware

GPU Recomendados

1. AMD RX 5XX (550 A 590)
5. AMD RX 55XX (5500 A 5700)
8. AMD RX 6600 XT (Monterey 12.1 o superior)

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

1. Magic Trackpad
1. Logitech MX
1. Plantronics Diadema USB
1. WebCam Logitech Brio; C92 PRO
1. TV OLED EVO 42.

## CONFIGURACION DEL BIOS DE LA PLACA MADRE

## USB Instalacion

1. Descargar Sistema Operativo

Ejecutar en la terminal:

mkdir -p ~/macOS-installer && cd ~/macOS-installer && curl https://raw.githubusercontent.com/munki/macadmin-scripts/main/installinstallmacos.py > installinstallmacos.py && sudo python3 installinstallmacos.py

<img width="578" alt="image" src="https://user-images.githubusercontent.com/8379954/203933257-3ee20601-89da-47c8-aeab-846b2a820659.png">

Leer este tutorial para crear el disco usb de arranque e instalaciòn:
https://dortania.github.io/OpenCore-Install-Guide/installer-guide/mac-install.html#downloading-macos-modern-os

1. Monte la particion EFI de la USB y pegue las siguientes carpetas:

a. BOOT
b. OC
