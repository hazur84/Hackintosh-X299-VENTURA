# Hackintosh-X299-VENTURA
X299 VENTURA OPENCORE 0.86


## Hardware

Evitar estos discos duros:

1. Cualquier almacenamiento basado en eMMC.
1. Samsung PM981 y PM991 
1. Micron 2200S
1. SKHynix PC711
1. Samsung 970 Evo Plus
1. Intel 600p

Discos provados y recomendados:

1. SN730 Western Digital
1. SN750
1. SN750
1. Kioxa
1. Toshiba XG6
1. Corsair

Wifi unico recomendado (solo estas no incistas)

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

Una vez que esté creada la USB, didigirse a la carpeta EFI, descargar las carpetas y pegarlas en la memoria USB:

1. BOOT
2. OC