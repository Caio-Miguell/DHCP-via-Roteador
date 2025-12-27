Project DHCP Network
Description

This project demonstrates a simple LAN where PCs receive IP addresses automatically via DHCP.
Four PCs are connected to a single switch, with a router acting as the DHCP server.

Devices

4 PCs 💻

1 Switch (Cisco 2960) 🟦

1 Router (Cisco 1941) 📡

IP Addressing Scheme
Device	IP Address	Subnet Mask	Gateway
PC0	DHCP	255.255.255.0	192.168.1.1
PC1	DHCP	255.255.255.0	192.168.1.1
PC2	DHCP	255.255.255.0	192.168.1.1
PC3	DHCP	255.255.255.0	192.168.1.1
Router	192.168.1.1	255.255.255.0	—
Topology
PC0 💻      PC1 💻
   │          │
PC2 💻      PC3 💻
   │          │
   └── Switch 2960 🟦
          │
      Router 1941 📡

DHCP Configuration Commands (Router)
enable
configure terminal
hostname R1

interface gigabitEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

ip dhcp excluded-address 192.168.1.1 192.168.1.5
ip dhcp pool LAN
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8
exit

Testing

PCs configured to obtain IP via DHCP

Verified IP assignment using ipconfig

Ping tests performed to the router and between PCs to confirm connectivity

Next Steps

Implement VLANs for network segmentation

Configure routing between different subnets

Explore DHCP options such as lease time and multiple pools
