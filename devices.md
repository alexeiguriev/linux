**devices**

**How to See Devices in Linux

a) List Block Devices (Storage):**

To see all block storage devices (such as hard drives, USB drives, etc.), you can use:


```lsblk```


This will display a tree of block devices and their partitions. The output includes device names, mount points, and sizes.


**b) List USB Devices:**

To see USB devices connected to your system, use:


```lsusb```


This will show information about all connected USB devices.


**c) List PCI Devices:**

To view devices connected via PCI (such as network cards, sound cards, etc.), you can use:


```lspci```


This will display a list of all PCI devices on the system.


**1. Check Printer Status Using the lpstat Command**

The lpstat command is part of the CUPS (Common UNIX Printing System), which is typically used to manage printers on Linux.
Command:

lpstat -p



d) List Network Interfaces:

To see all network interfaces (wired, wireless, etc.), you can use:


```ip link show```


This will list all available network interfaces and their current status (up/down).

Alternatively, you can use:


```ifconfig -a```


This shows detailed information about network interfaces, including IP addresses.

