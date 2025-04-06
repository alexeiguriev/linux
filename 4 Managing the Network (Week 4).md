* Objective: Learn how to manage and troubleshoot network settings and connectivity.

Topics to Cover:

* Checking network interfaces: ```ip a```, ```ifconfig```
    * ```ip addr show``` - Show all active network connections:
    * ```ip route```
* Network diagnostics: 
    * ```ping```,
    * ```traceroute```, 
    * ```nslookup```, 
    * ```dig``` (Domain Information Groper) command is used to query DNS information.
        * ```dig google.com```
* Checking open ports and active connections: 
    * ```netstat```, 
        * ```sudo netstat -tuln``` check for open ports
    * ```ss```
        * ```ss -tuln``` check the open ports
* Configuring and testing network connections: ```ip```, ```ifconfig```, ```route```, ```nmcli```
* Monitoring network traffic: ```iftop```, ```nload```

Practice:

* Test network connectivity using ```ping``` and ```traceroute```.
* View and analyze network interfaces and routing tables with ```ip a``` and ```route```.
* Monitor network traffic with ```iftop```.



Managing the network in Linux can involve a variety of tasks such as checking the status of network interfaces, viewing network statistics, configuring interfaces, and diagnosing network problems. Here are some key commands for managing networks in Linux:


Configuring the network after installing a Linux operating system involves ensuring that the system can connect to the internet (or a local network), which typically requires configuring network interfaces, IP addresses, DNS, and possibly a gateway.

Here’s an overview of the steps you might take to configure the network on Linux after installation:




1. Check Network Interfaces

After the installation, the first step is to identify the available network interfaces (like Ethernet or Wi-Fi). You can use commands like:


* ```ip link``` or ```ifconfig``` to list network interfaces.

```
ip link show
```


Example output:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
```

Here, ```enp3s0``` might represent a wired connection, and ```wlp2s0``` represents a Wi-Fi connection.




2. Connect to a Wired Network (Ethernet)

For Ethernet (wired) connections, Linux usually auto-detects the connection, and there’s often no need for manual configuration.


* If the Ethernet interface is not active, bring it up manually:

```
sudo ip link set enp3s0 up
```


Then, use DHCP (Dynamic Host Configuration Protocol) to automatically assign an IP address:

```
sudo dhclient enp3s0
```


This command will request an IP address from the network’s DHCP server.




3. Connect to a Wireless Network (Wi-Fi)

If you're using a Wi-Fi connection, the process is a bit more involved. You need to:


* Ensure that **wpa_supplicant** or **NetworkManager** is installed for managing Wi-Fi networks.

To connect **via the command line**:


* First, identify available Wi-Fi networks:

```
sudo iwlist wlp2s0 scan | grep SSID
```


* Then, use the nmcli tool (NetworkManager Command Line Interface) or wpa_supplicant to connect to a Wi-Fi network:

nmcli d wifi connect "your-SSID" password "your-password"


Alternatively, you can manually create a Wi-Fi configuration file for wpa_supplicant.




4. Configure Network Interface with Static IP (if needed)

If you need a static IP address instead of using DHCP, you can configure it by editing the network configuration file, depending on the Linux distribution:


* For systems using netplan (like Ubuntu 18.04+):

Edit the file /etc/netplan/01-netcfg.yaml (or similar):


network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: no
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8


After making changes, apply the configuration:


sudo netplan apply



* For older systems using ifupdown:

Edit the file /etc/network/interfaces:


auto enp3s0
iface enp3s0 inet static
  address 192.168.1.100
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 8.8.8.8


Then restart the networking service:


sudo systemctl restart networking





5. Verify Network Connectivity

Once you’ve configured the network, check connectivity by:


* Pinging an external server to ensure that you have an internet connection:

ping google.com



* Checking your IP address to verify network settings:

ip a





6. Configure DNS (Optional)

If you need to configure DNS (Domain Name System) settings manually, you can edit the /etc/resolv.conf file:


sudo nano /etc/resolv.conf


Add your preferred DNS server addresses (e.g., Google’s DNS):


nameserver 8.8.8.8
nameserver 8.8.4.4


Alternatively, for persistent changes, modify the netplan configuration or the appropriate network manager settings depending on your system.




7. Using NetworkManager for GUI Configuration

If you prefer a graphical interface for network management, NetworkManager (installed by default in many distributions) provides a GUI tool for managing network connections.


* For GNOME-based desktops, you can use Settings > Network.
* nm-applet can be used for managing connections from the system tray.




Summary:

1. Identify network interfaces (ip link, ifconfig).
2. Configure wired connection (usually automatic or with dhclient).
3. Configure wireless connection (use nmcli or NetworkManager).
4. Assign static IP addresses if needed (edit /etc/netplan/ or /etc/network/interfaces).
5. Verify connectivity (ping external websites, check IP address).
6. Configure DNS if necessary.
7. Optionally, use NetworkManager for GUI-based network management.

