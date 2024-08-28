# Basic Network Design & Configuration with GNS3
## Overview
This project demonstrates a basic network design and configuration using Cisco IOSv in GNS3. The setup includes configuring IP addressing, static routing, VLANs, and Inter-VLAN routing in a simulated environment. This will help us understand and implement fundamental networking concepts using GNS3 in a Virtualized Environment.
## Objectives
- Design and configure a small network topology with 2 Ubuntu docker containers, 2 Switches and a single Router.
- Implement basic IP addressing and subnetting.
- Set up static routing between routers.
- Configure VLANs and perform Inter-VLAN routing on switches.
## Utilities used
- GNS3
- HyperV (For GNS3-VM)
- Cisco IOSv
- PuTTY
## Network Topology
The network consists of:
### 2 Ubuntu Docker Container
- Ubuntu-Docker-1
- Ubuntu-Docker-2
### 2 Switches
- Switch-1
- Switch-2
### 1 Router
- Router
## IP Addressing Scheme
- Ubuntu-Docker-1: 192.168.10.2/24 (Interface connected to Switch1)
- Ubuntu-Docker-2: 192.168.20.2/24 (Interface connected to Switch1)

## Process
### Step 1: Create a new project
Open GNS3 and create a new project by going to File -> New Project
### Step 2: Design the Network Topology

- Add Devices:
For a basic setup, we use 2 Ubuntu Docker containers, 2 Switches and 1 Router

- Connect Devices:

![Screenshot 2024-08-28 121107](https://github.com/user-attachments/assets/51f45120-0c6b-4642-b40a-698e30bcdf5e)

### Step 3: Assigning IP address
- Open console for Ubuntu-Docker-1

```ip addr add 192.168.10.2/24``` <br>
```ip link set dev eth0 up``` <br>
```ip route add default via 192.168.10.1```

![Screenshot 2024-08-28 123615](https://github.com/user-attachments/assets/13e5e6b2-95d8-431d-af97-dd988af428c0)

- Open console for Switch-1
  
```enable``` <br>
```conf t``` <br>
```int vlan 1``` <br>
```ip address 192.168.10.1``` <br>

