Switches
Switch1: Model 2960-24TT
Switch0: Model 2960-24TT

Router
Router3: Model ISR4331
GigabitEthernet0/0/0: 168.90.0.1 / 255.255.0.0
GigabitEthernet0/0/1: 210.3.14.1 / 255.255.255.0

Hosts and Servers
PC0: IP Address - 168.90.0.5
PC1: IP Address - 168.90.0.2
Laptop0: IP Address - 168.90.0.3
Server0: IP Address - 168.90.0.4
Server1: IP Address - 210.3.14.2
Server2: IP Address - 210.3.14.3
PC2: IP Address - 210.3.14.4

NEW PCS ADDED:
PC3: IP Address - 168.90.0.6
PC4: IP Address - 210.3.14.5

1.Enter Global Configuration Mode:
enable
configure terminal

2.Configure Interfaces:
interface GigabitEthernet0/0/0
ip address 168.90.0.1 255.255.0.0
no shutdown
exit

interface GigabitEthernet0/0/1
ip address 210.3.14.1 255.255.255.0
no shutdown
exit

3.Exclude IP Addresses:
ip dhcp excluded-address 168.90.0.1
ip dhcp excluded-address 210.3.14.1


4.Configure DHCP Pools:
FIRST NETWORK
ip dhcp pool FIRST_NETWORK
network 168.90.0.0 255.255.0.0
default-router 168.90.0.1
exit

SECOND NETWORK
ip dhcp pool SECOND_NETWORK
network 210.3.14.0 255.255.255.0
default-router 210.3.14.1
exit

5.Save the Configuration:
exit
copy running-config startup-config