Manjaro HardWare Detection
==========================


**Manjaro HardWare Detection** ou plutôt **mhwd** comme on va l’appeler dorénavant est un outil propre à **Manjaro**. Sous cette appellation se cache en fait deux outils assez sympas en CLI mais aussi de manière graphique.

- **mhwd** : est la commande de base, active dés le début qui permet la détection et la configuration du hardware qu'il soit pci ou usb.

..Warning:: Noter que cet outil est encore en développement et n'est capable pour l'instant que d'installer les drivers graphiques des GPU.

- **mhwd-kernel** : est la commande pour gérer son ou plutôt ses kernels. C'est une des grandes possibilités que permet **Manjaro** c'est d'avoir des Kernels aux pluriels. Des LTS en général et parfois aussi, des kernels intermédiaires afin de bénéficier soit de nouvelles fonctionnalités non incluses dans les LTS soit des corrections de bogues ou les deux.



# MHWD
Mhwd est le nouvel outil que se dote Manjaro pour gérer les pilotes usb et pci dont installation et /ou la suppression de la carte graphique toujours complexe pour le débutant et le chevronné aussi. 
 
La commande se passe soit en mode utilisateur normal soit en root à laquelle ont spécifie s'il s'agit d'un périphérique usb ou pci, puis le choix du type de pilotes cad s'il est libre ou propriétaire auquel on attribut un code à 4 chiffre, ce code correspondant à un type spécifique de hardware. Le seul code connu à ce jour (vu qu'il s'agit d'un outil en développement comme je l'ai déjà sus-cité) est celui pour l'installation des cartes graphiques qui est le 0300. Ce qui nous donne donc pour les cas suivants :


Affichage de la liste du hardware installé avec vue détaillée (ou pas), seulement les périphériques usb ou pci (ou pas)

..Note:: On peut soit utiliser les diminutifs soit l’appellation exacte comme souvent dans un programme en CLI.


	mhwd -lh(--listhardware) -d(--detail) --pci/--usb
	
Ce qui donne pour du pci détaillé par exemple sur une carte mère B550 avec un Ryzen 5700G

	mhwd -lh -d --pci
	
	06: PCI 08.0: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:08.0
  SysFS BusID: 0000:00:08.0
  Hardware Class: bridge
  Model: "AMD Renoir PCIe Dummy Host Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1632 "Renoir PCIe Dummy Host Bridge"
  Module Alias: "pci:v00001022d00001632sv00000000sd00000000bc06sc00i00"

07: PCI a00.6: 0403 Audio device
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.6
  SysFS BusID: 0000:0a:00.6
  Hardware Class: sound
  Model: "AMD Family 17h (Models 10h-1fh) HD Audio Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x15e3 "Family 17h (Models 10h-1fh) HD Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x87c5 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfca80000-0xfca87fff (rw,non-prefetchable)
  IRQ: 102 (1486 events)
  Module Alias: "pci:v00001022d000015E3sv00001043sd000087C5bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Attached to: #26 (PCI bridge)

08: PCI 18.3: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.3
  SysFS BusID: 0000:00:18.3
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x166d 
  Driver: "k10temp"
  Driver Modules: "k10temp"
  Module Alias: "pci:v00001022d0000166Dsv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: k10temp is active
    Driver Activation Cmd: "modprobe k10temp"

09: PCI 900.0: 0108 Non-Volatile memory controller (NVM Express)
  SysFS ID: /devices/pci0000:00/0000:00:02.2/0000:09:00.0
  SysFS BusID: 0000:09:00.0
  Hardware Class: storage
  Model: "Samsung Electronics NVMe SSD Controller SM981/PM981/PM983"
  Vendor: pci 0x144d "Samsung Electronics Co Ltd"
  Device: pci 0xa808 "NVMe SSD Controller SM981/PM981/PM983"
  SubVendor: pci 0x144d "Samsung Electronics Co Ltd"
  SubDevice: pci 0xa801 
  Driver: "nvme"
  Driver Modules: "nvme"
  Memory Range: 0xfcf00000-0xfcf03fff (rw,non-prefetchable)
  IRQ: 40 (no events)
  Module Alias: "pci:v0000144Dd0000A808sv0000144Dsd0000A801bc01sc08i02"
  Attached to: #34 (PCI bridge)

10: PCI a00.4: 0c03 USB Controller (XHCI)
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.4
  SysFS BusID: 0000:0a:00.4
  Hardware Class: usb controller
  Model: "AMD Renoir USB 3.1"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1639 "Renoir USB 3.1"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x87e1 
  Driver: "xhci_hcd"
  Driver Modules: "xhci_pci"
  Memory Range: 0xfc700000-0xfc7fffff (rw,non-prefetchable)
  IRQ: 29 (no events)
  Module Alias: "pci:v00001022d00001639sv00001043sd000087E1bc0Csc03i30"
  Driver Info #0:
    Driver Status: xhci_pci is active
    Driver Activation Cmd: "modprobe xhci_pci"
  Attached to: #26 (PCI bridge)

11: PCI 18.1: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.1
  SysFS BusID: 0000:00:18.1
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x166b 
  Module Alias: "pci:v00001022d0000166Bsv00000000sd00000000bc06sc00i00"

12: PCI 200.0: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ea 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x3308 
  Driver: "pcieport"
  IRQ: 32 (no events)
  Module Alias: "pci:v00001022d000043EAsv00001B21sd00003308bc06sc04i00"
  Attached to: #15 (PCI bridge)

13: PCI 01.0: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "AMD Renoir PCIe Dummy Host Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1632 "Renoir PCIe Dummy Host Bridge"
  Module Alias: "pci:v00001022d00001632sv00000000sd00000000bc06sc00i00"

14: PCI 800.0: 0200 Ethernet controller
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:09.0/0000:08:00.0
  SysFS BusID: 0000:08:00.0
  Hardware Class: network
  Model: "Intel Ethernet Controller I225-V"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x15f3 "Ethernet Controller I225-V"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x87d2 
  Revision: 0x03
  Driver: "igc"
  Driver Modules: "igc"
  Device File: enp8s0
  Memory Range: 0xfcb00000-0xfcbfffff (rw,non-prefetchable)
  Memory Range: 0xfcc00000-0xfcc03fff (rw,non-prefetchable)
  IRQ: 33 (no events)
  HW Address: 7c:10:c9:3e:d3:bc
  Permanent HW Address: 7c:10:c9:3e:d3:bc
  Link detected: no
  Module Alias: "pci:v00008086d000015F3sv00001043sd000087D2bc02sc00i00"
  Driver Info #0:
    Driver Status: igc is active
    Driver Activation Cmd: "modprobe igc"
  Attached to: #24 (PCI bridge)

15: PCI 100.2: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2
  SysFS BusID: 0000:01:00.2
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43e9 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x0201 
  Driver: "pcieport"
  IRQ: 30 (no events)
  Module Alias: "pci:v00001022d000043E9sv00001B21sd00000201bc06sc04i00"
  Attached to: #20 (PCI bridge)

16: PCI a00.2: 1080 Encryption controller
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.2
  SysFS BusID: 0000:0a:00.2
  Hardware Class: unknown
  Model: "AMD Family 17h (Models 10h-1fh) Platform Security Processor"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x15df "Family 17h (Models 10h-1fh) Platform Security Processor"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Driver: "ccp"
  Driver Modules: "ccp"
  Memory Range: 0xfc900000-0xfc9fffff (rw,non-prefetchable)
  Memory Range: 0xfca8c000-0xfca8dfff (rw,non-prefetchable)
  IRQ: 31 (no events)
  Module Alias: "pci:v00001022d000015DFsv00001043sd00008809bc10sc80i00"
  Driver Info #0:
    Driver Status: ccp is active
    Driver Activation Cmd: "modprobe ccp"
  Attached to: #26 (PCI bridge)

17: PCI 203.0: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:03.0
  SysFS BusID: 0000:02:03.0
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ea 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x3308 
  Driver: "pcieport"
  IRQ: 37 (no events)
  Module Alias: "pci:v00001022d000043EAsv00001B21sd00003308bc06sc04i00"
  Attached to: #15 (PCI bridge)

18: PCI 14.3: 0601 ISA bridge
  SysFS ID: /devices/pci0000:00/0000:00:14.3
  SysFS BusID: 0000:00:14.3
  Hardware Class: bridge
  Model: "AMD FCH LPC Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x790e "FCH LPC Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x87e1 
  Revision: 0x51
  Module Alias: "pci:v00001022d0000790Esv00001043sd000087E1bc06sc01i00"

19: PCI 100.0: 0c03 USB Controller (XHCI)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: usb controller
  Model: "AMD USB Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ee 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x1142 
  Driver: "xhci_hcd"
  Driver Modules: "xhci_pci"
  Memory Range: 0xfcea0000-0xfcea7fff (rw,non-prefetchable)
  IRQ: 31 (no events)
  Module Alias: "pci:v00001022d000043EEsv00001B21sd00001142bc0Csc03i30"
  Driver Info #0:
    Driver Status: xhci_pci is active
    Driver Activation Cmd: "modprobe xhci_pci"
  Attached to: #20 (PCI bridge)

20: PCI 02.1: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: bridge
  Model: "AMD Renoir PCIe GPP Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1634 "Renoir PCIe GPP Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Driver: "pcieport"
  IRQ: 26 (no events)
  Module Alias: "pci:v00001022d00001634sv00001043sd00008809bc06sc04i00"

21: PCI a00.0: 0300 VGA compatible controller (VGA)
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.0
  SysFS BusID: 0000:0a:00.0
  Hardware Class: graphics card
  Model: "ATI Cezanne"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x1638 "Cezanne"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Revision: 0xc8
  Driver: "amdgpu"
  Driver Modules: "amdgpu"
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xe0000000-0xe01fffff (ro,non-prefetchable)
  I/O Ports: 0xf000-0xf0ff (rw)
  Memory Range: 0xfca00000-0xfca7ffff (rw,non-prefetchable)
  Memory Range: 0x000c0000-0x000dffff (rw,non-prefetchable,disabled)
  IRQ: 29 (no events)
  Module Alias: "pci:v00001002d00001638sv00001043sd00008809bc03sc00i00"
  Driver Info #0:
    Driver Status: amdgpu is active
    Driver Activation Cmd: "modprobe amdgpu"
  Attached to: #26 (PCI bridge)

22: PCI 00.2: 0806 IOMMU
  SysFS ID: /devices/pci0000:00/0000:00:00.2
  SysFS BusID: 0000:00:00.2
  Hardware Class: unknown
  Model: "AMD Renoir IOMMU"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1631 "Renoir IOMMU"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  IRQ: 2147483648 (no events)
  Module Alias: "pci:v00001022d00001631sv00001043sd00008809bc08sc06i00"

23: PCI 18.6: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.6
  SysFS BusID: 0000:00:18.6
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1670 
  Module Alias: "pci:v00001022d00001670sv00000000sd00000000bc06sc00i00"

24: PCI 209.0: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:09.0
  SysFS BusID: 0000:02:09.0
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ea 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x3308 
  Driver: "pcieport"
  IRQ: 39 (no events)
  Module Alias: "pci:v00001022d000043EAsv00001B21sd00003308bc06sc04i00"
  Attached to: #15 (PCI bridge)

25: PCI 00.0: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "AMD Renoir Root Complex"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1630 "Renoir Root Complex"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Module Alias: "pci:v00001022d00001630sv00001043sd00008809bc06sc00i00"

26: PCI 08.1: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:08.1
  SysFS BusID: 0000:00:08.1
  Hardware Class: bridge
  Model: "AMD Renoir Internal PCIe GPP Bridge to Bus"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1635 "Renoir Internal PCIe GPP Bridge to Bus"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Driver: "pcieport"
  IRQ: 28 (no events)
  Module Alias: "pci:v00001022d00001635sv00001043sd00008809bc06sc04i00"

27: PCI 18.4: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.4
  SysFS BusID: 0000:00:18.4
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x166e 
  Module Alias: "pci:v00001022d0000166Esv00000000sd00000000bc06sc00i00"

28: PCI 202.0: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:02.0
  SysFS BusID: 0000:02:02.0
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ea 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x3308 
  Driver: "pcieport"
  IRQ: 35 (no events)
  Module Alias: "pci:v00001022d000043EAsv00001B21sd00003308bc06sc04i00"
  Attached to: #15 (PCI bridge)

29: PCI 18.2: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.2
  SysFS BusID: 0000:00:18.2
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x166c 
  Module Alias: "pci:v00001022d0000166Csv00000000sd00000000bc06sc00i00"

30: PCI a00.3: 0c03 USB Controller (XHCI)
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.3
  SysFS BusID: 0000:0a:00.3
  Hardware Class: usb controller
  Model: "AMD Renoir USB 3.1"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1639 "Renoir USB 3.1"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x87e1 
  Driver: "xhci_hcd"
  Driver Modules: "xhci_pci"
  Memory Range: 0xfc800000-0xfc8fffff (rw,non-prefetchable)
  IRQ: 33 (no events)
  Module Alias: "pci:v00001022d00001639sv00001043sd000087E1bc0Csc03i30"
  Driver Info #0:
    Driver Status: xhci_pci is active
    Driver Activation Cmd: "modprobe xhci_pci"
  Attached to: #26 (PCI bridge)

31: PCI 18.0: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.0
  SysFS BusID: 0000:00:18.0
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x166a 
  Module Alias: "pci:v00001022d0000166Asv00000000sd00000000bc06sc00i00"

32: PCI 208.0: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:08.0
  SysFS BusID: 0000:02:08.0
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ea 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x3308 
  Driver: "pcieport"
  IRQ: 38 (no events)
  Module Alias: "pci:v00001022d000043EAsv00001B21sd00003308bc06sc04i00"
  Attached to: #15 (PCI bridge)

33: PCI 100.1: 0106 SATA controller (AHCI 1.0)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: storage
  Model: "AMD SATA controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43eb 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x1062 
  Driver: "ahci"
  Driver Modules: "ahci"
  Memory Range: 0xfce80000-0xfce9ffff (rw,non-prefetchable)
  Memory Range: 0xfce00000-0xfce7ffff (ro,non-prefetchable,disabled)
  IRQ: 42 (290 events)
  Module Alias: "pci:v00001022d000043EBsv00001B21sd00001062bc01sc06i01"
  Attached to: #20 (PCI bridge)

34: PCI 02.2: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.2
  SysFS BusID: 0000:00:02.2
  Hardware Class: bridge
  Model: "AMD Renoir PCIe GPP Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1634 "Renoir PCIe GPP Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Driver: "pcieport"
  IRQ: 27 (no events)
  Module Alias: "pci:v00001022d00001634sv00001043sd00008809bc06sc04i00"

35: PCI a00.1: 0403 Audio device
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.1
  SysFS BusID: 0000:0a:00.1
  Hardware Class: sound
  Model: "ATI Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x1637 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8809 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfca88000-0xfca8bfff (rw,non-prefetchable)
  IRQ: 101 (218 events)
  Module Alias: "pci:v00001002d00001637sv00001043sd00008809bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Attached to: #26 (PCI bridge)

36: PCI 400.0: 0200 Ethernet controller
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:01.0/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: network
  Model: "Intel Wi-Fi 6 AX200NGW"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2723 "Wi-Fi 6 AX200"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x0084 "Wi-Fi 6 AX200NGW"
  Revision: 0x1a
  Driver: "iwlwifi"
  Driver Modules: "iwlwifi"
  Device File: wlp4s0
  Memory Range: 0xfcd00000-0xfcd03fff (rw,non-prefetchable)
  IRQ: 33 (no events)
  HW Address: c8:e2:65:fa:8a:5c
  Permanent HW Address: c8:e2:65:fa:8a:5c
  Link detected: yes
  Module Alias: "pci:v00008086d00002723sv00008086sd00000084bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlwifi is active
    Driver Activation Cmd: "modprobe iwlwifi"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Attached to: #37 (PCI bridge)

37: PCI 201.0: 0604 PCI bridge (Normal decode)
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:01.0
  SysFS BusID: 0000:02:01.0
  Hardware Class: bridge
  Model: "AMD PCI bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x43ea 
  SubVendor: pci 0x1b21 "ASMedia Technology Inc."
  SubDevice: pci 0x3308 
  Driver: "pcieport"
  IRQ: 34 (no events)
  Module Alias: "pci:v00001022d000043EAsv00001B21sd00003308bc06sc04i00"
  Attached to: #15 (PCI bridge)

38: PCI 02.0: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: bridge
  Device Name: "Onboard IGD"
  Model: "AMD Renoir PCIe Dummy Host Bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1632 "Renoir PCIe Dummy Host Bridge"
  Module Alias: "pci:v00001022d00001632sv00000000sd00000000bc06sc00i00"

39: PCI 18.7: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.7
  SysFS BusID: 0000:00:18.7
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1671 
  Module Alias: "pci:v00001022d00001671sv00000000sd00000000bc06sc00i00"

40: PCI 14.0: 0c05 SMBus
  SysFS ID: /devices/pci0000:00/0000:00:14.0
  SysFS BusID: 0000:00:14.0
  Hardware Class: unknown
  Model: "AMD FCH SMBus Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x790b "FCH SMBus Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x87e1 
  Revision: 0x51
  Driver: "piix4_smbus"
  Driver Modules: "i2c_piix4"
  Module Alias: "pci:v00001022d0000790Bsv00001043sd000087E1bc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_piix4 is active
    Driver Activation Cmd: "modprobe i2c_piix4"
  Driver Info #1:
    Driver Status: sp5100_tco is active
    Driver Activation Cmd: "modprobe sp5100_tco"

41: PCI 18.5: 0600 Host bridge
  SysFS ID: /devices/pci0000:00/0000:00:18.5
  SysFS BusID: 0000:00:18.5
  Hardware Class: bridge
  Model: "AMD Host bridge"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x166f 
  Module Alias: "pci:v00001022d0000166Fsv00000000sd00000000bc06sc00i00"


Voici ce que l'on obtient pour l'usb toujours sur la même configuration que la commande précédante.

	mhwd -lh -d --usb
	03: USB 00.0: 10503 USB Mouse
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-9/1-9:1.0
  SysFS BusID: 1-9:1.0
  Hardware Class: mouse
  Model: "Razer RC30-0315, Gaming Mouse [Basilisk X HyperSpeed]"
  Hotplug: USB
  Vendor: usb 0x1532 "Razer USA, Ltd"
  Device: usb 0x0083 "RC30-0315, Gaming Mouse [Basilisk X HyperSpeed]"
  Revision: "2.00"
  Compatible to: int 0x0210 0x0025
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event15, /dev/input/by-id/usb-Razer_Razer_Basilisk_X_HyperSpeed-event-mouse, /dev/input/by-path/pci-0000:01:00.0-usb-0:9:1.0-event-mouse, /dev/input/by-path/pci-0000:01:00.0-usb-0:9:1.0-mouse, /dev/input/by-id/usb-Razer_Razer_Basilisk_X_HyperSpeed-mouse
  Device Number: char 13:63 (char 13:33)
  Speed: 12 Mbps
  Module Alias: "usb:v1532p0083d0200dc00dsc00dp00ic03isc01ip02in00"
  Driver Info #0:
    Buttons: 5
    Wheels: 2
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Attached to: #14 (Hub)

04: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.4/usb6/6-0:1.0
  SysFS BusID: 6-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 3.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0003 "3.0 root hub"
  Revision: "5.15"
  Serial ID: "0000:0a:00.4"
  Driver: "hub"
  Driver Modules: "usbcore"
  Module Alias: "usb:v1D6Bp0003d0515dc09dsc00dp03ic09isc00ip00in00"

05: USB 00.2: 0000 Unclassified device
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-6/1-6:1.2
  SysFS BusID: 1-6:1.2
  Hardware Class: unknown
  Model: "ASUSTek AURA LED Controller"
  Hotplug: USB
  Vendor: usb 0x0b05 "ASUSTek Computer, Inc."
  Device: usb 0x1939 "AURA LED Controller"
  Revision: "1.00"
  Serial ID: "9876543210"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v0B05p1939d0100dc00dsc00dp00ic03isc00ip00in02"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Attached to: #14 (Hub)

07: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.3/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 2.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0002 "2.0 root hub"
  Revision: "5.15"
  Serial ID: "0000:0a:00.3"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0515dc09dsc00dp01ic09isc00ip00in00"

08: USB 00.0: 11500 Bluetooth Device
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-7/1-7.2/1-7.2:1.0
  SysFS BusID: 1-7.2:1.0
  Hardware Class: bluetooth
  Model: "Intel AX200 Bluetooth"
  Hotplug: USB
  Vendor: usb 0x8087 "Intel Corp."
  Device: usb 0x0029 "AX200 Bluetooth"
  Revision: "0.01"
  Driver: "btusb"
  Driver Modules: "btusb"
  Speed: 12 Mbps
  Module Alias: "usb:v8087p0029d0001dcE0dsc01dp01icE0isc01ip01in00"
  Driver Info #0:
    Driver Status: btusb is active
    Driver Activation Cmd: "modprobe btusb"
  Attached to: #11 (Hub)

09: USB 00.2: 0000 Unclassified device
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.3/usb3/3-1/3-1:1.2
  SysFS BusID: 3-1:1.2
  Hardware Class: unknown
  Model: "Logitech USB Receiver"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc547 "USB Receiver"
  Revision: "4.02"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC547d0402dc00dsc00dp00ic03isc00ip00in02"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Attached to: #7 (Hub)

10: USB 00.1: 0000 Unclassified device
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-9/1-9:1.1
  SysFS BusID: 1-9:1.1
  Hardware Class: unknown
  Model: "Razer RC30-0315, Gaming Mouse [Basilisk X HyperSpeed]"
  Hotplug: USB
  Vendor: usb 0x1532 "Razer USA, Ltd"
  Device: usb 0x0083 "RC30-0315, Gaming Mouse [Basilisk X HyperSpeed]"
  Revision: "2.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event16
  Device Files: /dev/input/event16, /dev/input/by-path/pci-0000:01:00.0-usb-0:9:1.1-event-kbd, /dev/input/by-id/usb-Razer_Razer_Basilisk_X_HyperSpeed-if01-event-kbd
  Device Number: char 13:80
  Speed: 12 Mbps
  Module Alias: "usb:v1532p0083d0200dc00dsc00dp00ic03isc00ip01in01"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Attached to: #14 (Hub)

11: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-7/1-7:1.0
  SysFS BusID: 1-7:1.0
  Hardware Class: hub
  Model: "Genesys Logic Hub"
  Hotplug: USB
  Vendor: usb 0x05e3 "Genesys Logic, Inc."
  Device: usb 0x0608 "Hub"
  Revision: "60.90"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v05E3p0608d6090dc09dsc00dp01ic09isc00ip00in00"
  Attached to: #14 (Hub)

12: USB 00.0: 10503 USB Mouse
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.3/usb3/3-1/3-1:1.0
  SysFS BusID: 3-1:1.0
  Hardware Class: mouse
  Model: "Logitech USB Receiver"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc547 "USB Receiver"
  Revision: "4.02"
  Compatible to: int 0x0210 0x0048
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event2, /dev/input/by-path/pci-0000:0a:00.3-usb-0:1:1.0-event-mouse, /dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse, /dev/input/by-id/usb-Logitech_USB_Receiver-mouse, /dev/input/by-path/pci-0000:0a:00.3-usb-0:1:1.0-mouse
  Device Number: char 13:63 (char 13:32)
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC547d0402dc00dsc00dp00ic03isc01ip02in00"
  Driver Info #0:
    Buttons: 8
    Wheels: 4
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Attached to: #7 (Hub)

13: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.3/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 3.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0003 "3.0 root hub"
  Revision: "5.15"
  Serial ID: "0000:0a:00.3"
  Driver: "hub"
  Driver Modules: "usbcore"
  Module Alias: "usb:v1D6Bp0003d0515dc09dsc00dp03ic09isc00ip00in00"

14: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 2.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0002 "2.0 root hub"
  Revision: "5.15"
  Serial ID: "0000:01:00.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0515dc09dsc00dp01ic09isc00ip00in00"

16: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.4/usb5/5-0:1.0
  SysFS BusID: 5-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 2.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0002 "2.0 root hub"
  Revision: "5.15"
  Serial ID: "0000:0a:00.4"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0515dc09dsc00dp01ic09isc00ip00in00"

18: USB 00.1: 10800 Keyboard
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:0a:00.3/usb3/3-1/3-1:1.1
  SysFS BusID: 3-1:1.1
  Hardware Class: keyboard
  Model: "Logitech USB Receiver"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc547 "USB Receiver"
  Revision: "4.02"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/input/by-id/usb-Logitech_USB_Receiver-if01-event-kbd, /dev/input/by-path/pci-0000:0a:00.3-usb-0:1:1.1-event-kbd
  Device Number: char 13:67
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC547d0402dc00dsc00dp00ic03isc01ip01in01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Attached to: #7 (Hub)

19: USB 00.0: 10a00 Hub
  SysFS ID: /devices/pci0000:00/0000:00:02.1/0000:01:00.0/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux Foundation 3.0 root hub"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux Foundation"
  Device: usb 0x0003 "3.0 root hub"
  Revision: "5.15"
  Serial ID: "0000:01:00.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Module Alias: "usb:v1D6Bp0003d0515dc09dsc00dp03ic09isc00ip00in00"

Et une dernière la plus simple possible

	mhwd -lh
	> PCI devices:
--------------------------------------------------------------------------------
                          TYPE            BUS   CLASS  VENDOR  DEVICE   CONFIGS
--------------------------------------------------------------------------------
                        Bridge   0000:00:08.0    0600    1022    1632         0
         Multimedia controller   0000:0a:00.6    0403    1022    15e3         0
                        Bridge   0000:00:18.3    0600    1022    166d         0
       Mass storage controller   0000:09:00.0    0108    144d    a808         0
         Serial bus controller   0000:0a:00.4    0c03    1022    1639         0
                        Bridge   0000:00:18.1    0600    1022    166b         0
                        Bridge   0000:02:00.0    0604    1022    43ea         0
                        Bridge   0000:00:01.0    0600    1022    1632         0
            Network controller   0000:08:00.0    0200    8086    15f3         0
                        Bridge   0000:01:00.2    0604    1022    43e9         0
         Encryption controller   0000:0a:00.2    1080    1022    15df         0
                        Bridge   0000:02:03.0    0604    1022    43ea         0
                        Bridge   0000:00:14.3    0601    1022    790e         0
         Serial bus controller   0000:01:00.0    0c03    1022    43ee         0
                        Bridge   0000:00:02.1    0604    1022    1634         0
            Display controller   0000:0a:00.0    0300    1002    1638         3
     Generic system peripheral   0000:00:00.2    0806    1022    1631         0
                        Bridge   0000:00:18.6    0600    1022    1670         0
                        Bridge   0000:02:09.0    0604    1022    43ea         0
                        Bridge   0000:00:00.0    0600    1022    1630         0
                        Bridge   0000:00:08.1    0604    1022    1635         0
                        Bridge   0000:00:18.4    0600    1022    166e         0
                        Bridge   0000:02:02.0    0604    1022    43ea         0
                        Bridge   0000:00:18.2    0600    1022    166c         0
         Serial bus controller   0000:0a:00.3    0c03    1022    1639         0
                        Bridge   0000:00:18.0    0600    1022    166a         0
                        Bridge   0000:02:08.0    0604    1022    43ea         0
       Mass storage controller   0000:01:00.1    0106    1022    43eb         0
                        Bridge   0000:00:02.2    0604    1022    1634         0
         Multimedia controller   0000:0a:00.1    0403    1002    1637         0
            Network controller   0000:04:00.0    0200    8086    2723         0
                        Bridge   0000:02:01.0    0604    1022    43ea         0
                        Bridge   0000:00:02.0    0600    1022    1632         0
                        Bridge   0000:00:18.7    0600    1022    1671         0
         Serial bus controller   0000:00:14.0    0c05    1022    790b         0
                        Bridge   0000:00:18.5    0600    1022    166f         0


> USB devices:
--------------------------------------------------------------------------------
                          TYPE            BUS   CLASS  VENDOR  DEVICE   CONFIGS
--------------------------------------------------------------------------------
                         Mouse        1-9:1.0   10503    1532    0083         0
                           Hub        6-0:1.0   10a00    1d6b    0003         0
           Unclassified device        1-6:1.2    0000    0b05    1939         0
                           Hub        3-0:1.0   10a00    1d6b    0002         0
              Bluetooth Device      1-7.2:1.0   11500    8087    0029         0
           Unclassified device        3-1:1.2    0000    046d    c547         0
           Unclassified device        1-9:1.1    0000    1532    0083         0
                           Hub        1-7:1.0   10a00    05e3    0608         0
                         Mouse        3-1:1.0   10503    046d    c547         0
                           Hub        4-0:1.0   10a00    1d6b    0003         0
                           Hub        1-0:1.0   10a00    1d6b    0002         0
                           Hub        5-0:1.0   10a00    1d6b    0002         0
                      Keyboard        3-1:1.1   10800    046d    c547         0
                           Hub        2-0:1.0   10a00    1d6b    0003         0


On identifie et liste tous les drivers installés en utilisant le même principe détaillé (ou pas), usb ou pci (ou pas) que la  commande précédante.

On veut une liste détaillée.

	mhwd -li -d
	NAME:        video-linux
   ATTACHED:    PCI
   VERSION:     2018.05.04
   INFO:        Standard open source drivers.
   PRIORITY:    2
   FREEDRIVER:  true
   DEPENDS:     -
   CONFLICTS:   -
   CLASSIDS:    0300 0380 0302 
   VENDORIDS:   1002 8086 10de 


Warning: no installed configs for USB devices found!


On peut aussi lister les drivers disponibles globalement ou en usb ou en pci seulement.

	mhwd -la
	> All PCI configs:
--------------------------------------------------------------------------------
                  NAME               VERSION          FREEDRIVER           TYPE
--------------------------------------------------------------------------------
   network-broadcom-wl            2018.10.07               false            PCI
     network-rt3562sta            2013.12.07                true            PCI
       network-slmodem            2013.12.07                true            PCI
         network-r8168            2016.04.20                true            PCI
            video-vesa            2017.03.12                true            PCI
          video-sisusb            2020.01.18                true            PCI
    video-nvidia-470xx            2021.11.04               false            PCI
           video-linux            2018.05.04                true            PCI
          video-nvidia            2021.11.04               false            PCI
video-hybrid-intel-nvidia-470xx-prime            2021.11.04               false            PCI
       video-rendition            2020.01.18                true            PCI
    video-nvidia-390xx            2021.11.26               false            PCI
     video-modesetting            2020.01.13                true            PCI
              video-s3            2020.01.18                true            PCI
video-hybrid-amd-nvidia-prime            2021.11.04               false            PCI
video-hybrid-intel-nvidia-prime            2021.11.04               false            PCI
video-hybrid-amd-nvidia-470xx-prime            2021.11.04               false            PCI
          video-voodoo            2017.03.12                true            PCI
      video-openchrome            2020.01.18                true            PCI
video-hybrid-intel-nvidia-390xx-bumblebee            2021.11.26               false            PCI
  video-virtualmachine            2021.07.26                true            PCI


Warning: No USB configs found!


Pour lister le bon driver pour notre système avec ou sans usb/pci

	mhwd -l
	> 0000:0a:00.0 (0300:1002:1638) Display controller ATI Technologies Inc:
--------------------------------------------------------------------------------
                  NAME               VERSION          FREEDRIVER           TYPE
--------------------------------------------------------------------------------
           video-linux            2018.05.04                true            PCI
     video-modesetting            2020.01.13                true            PCI
            video-vesa            2017.03.12                true            PCI



	
..Note:: Je ne peux que vous conseiller d'aller voir toutes les options de Mhwd en rajoutant la commande -h ou --help. On a même la possibilité de forcer l'installation/réinstallation d'un pilote.


## GPU

Pour identifier les pilotes graphique disponibles:

	mhwd -l (vue détaillée optionnelle avec l'option -i) (connexion --pci ou --usb optionnelle aussi)
	
..Note:: Tous les pilotes vont avoir un préfixe video- avant leur nom. La version, le type de connexion (usb ou pci) et sa licence (libre ou propriétaire) sont aussi indiqués. 

Ce qui nous donnes:

Pour détecter et installer un pilote graphique d'une carte graphique pci avec le pilote open-source :

	sudo mhwd -a pci free 0300
	
Pour faire la même chose mais en installant le pilote propriétaire (ex amd ou nvidia ou intel):

	sudo mhwd -a pci nonfree 0300

	

Pour forcer la réinstallation d'un pilote
	sudo mhwd -f -i pci non_du_pilote (ex: video-nvidia) 
	

Pour supprimer un pilote (généralement un propriétaire)
	sudo mhwd -r pci nom_du_pilote (ex: video-nvidia)
	

..Note:: Une autre commande existait mais semble ne plus fonctionner même si le package semble être encore présent: **mhwd-gpu**. Celle-ci nous donnait un peu plus d'informations sur le gpu qui sont les suivantes (avec le résultat actuel mi-aôut 2022).

..Note:: Pour **Amd**, les pilotes graphiques depuis 2015/2016 sont nommés **amdgpu** pour les pilotes libres et **amdgpu-pro** pour les pilotes propriétaires.

..Note:: Aucune idée pour l'instant en ce qui concerne les pilotes graphiques **Intel**.

..Note:: Depuis mi 2022, **Nvidia** semble s'être décidé à enfin jouer la carte de l'open-source en proposant des pilotes libres sous le nom de **Nouveau** et ses pilotes propriétaires **Nvidia**.

- Affiche le status actuel

	mhwd-gpu --status                                                                                                                                                                	:: status
	warning: could not find '/etc/X11/xorg.conf.d/90-mhwd.conf'!

- Vérifie et répare les liens symboliques s'il le faut

	mhwd-gpu --check
	
- Affiche le fichier de configuration de Xorg

	
	sudo mhwd-gpu --setxorg '/etc/X11/xorg.conf.d/90-mhwd.conf'                                                                                                                                       
	warning: could not find '/etc/X11/xorg.conf.d/90-mhwd.conf'!

- Affiche les modules soit nvidia soit catalyst

	sudo mhwd-gpu --setmod catalyst                                                                                       
	                                                                             

# MHWD-KERNEL
 
 
 Tout ce qui touche aux Kernels est un peu tabou sur la majorité des distributions Linux. D'ailleurs, on n'a souvent qu'un Kernel d'installé, celui-qui vient avec celle-ci.
 
Sous Manjaro, c'est totalement différent. On a le choix et d'ailleurs, il est fortement conseillé d'avoir deux kernels stables en plus du kernel que l'on utilise. Et C'est d'une facilité déconcertant. Le mieux est de voir avec quelques exemples la puissance et la simplicité de cet outil.

Listons d'abord nos Kernels installés sur notre système

	mhwd-kernel -li

Listons les Kernels qui sont disponibles à l'installation

	mhwd-kernel 
	
Installons le kernel 5.19 qui est le dernier lors de la création de ces lignes Sans supprimer celui-que l'on utilise ici le 


	sudo mhwd-kernel -i linux5.19
	
On peut faire tout autrement à la fois en installant le 5.19 et celui que l'on utilise avec la commande rmc

	sudo mhwd-kernel -i linux5.19 rmc

Desinstallons un kernel autre que celui que l'on utilise

	sudo mhwd-kernel -r linux4.19
	
Pour supprimer les headers du Kernel, on est obligé de passer par pacman

	sudo pacman -R linux4.19-headers
	
Pour supprimer les modules extras, on est obligé de passer par pacman 

	sudo pacman -R linux4.19-extramodules
	
Pour tout supprimer à la fois cad le kernel, les headers et les extras du module, on se sert de pacman

	sudo pacman -R linux4.19 linux4.19-headers linux4.19-extramodules


# Interface Graphique

Pour cela, il suffit d'aller dans Configuration System. Toutefois, le résultat graphique peut varier suivant l'environnement que vous utilisez. 
Dans KDE il est intégré à Configuration System tandis que sous Cinnamon il est disponible séparément. 

Pour KDE, mhwd puis mhwd-kernel

.. figure:: ./images/mhwd_kde.png

.. figure:: ./images/mhwd-kernel_kde.png


Pour Cinnamon

.. figure:: ./images/mhwd_cinnamon.png

.. figure:: ./images/mhwd-kernel_cinnamon.png


# Mais pas que:

En Cli notre système peut nous fournir pas mal d'informations sur  le GPU. 
En voici quelques unes:

Identifier son GPU
	sudo lspci | grep -i vga
	
Pour un Ryzen 7 5700G avec IGP RDNA1 intégré
	0a:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne (rev c8)

Pour un portable avec un Ryzen 7 5800 H avec IGP RDNA1 intégré
	0a:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne (rev c5)
	
	
..Note:: On se rend compte que quelque soit le résultat et sous n'importe quelle forme, il provient de la commande **dmesg**. 