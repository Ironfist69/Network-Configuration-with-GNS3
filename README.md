# Basic Network Design & Configuration with GNS3
## Overview
This project demonstrates a basic network design and configuration using Cisco IOSv in GNS3. The setup includes configuring IP addressing, static routing, VLANs, and Inter-VLAN routing in a simulated environment. This will help us understand and implement fundamental networking concepts using GNS3 in a Virtualized Environment.
## Objectives
- Design and configure a small network topology with 3 Ubuntu docker containers, 2 Switches and a single Router.
- Implement basic IP addressing and subnetting.
- Set up static routing between routers.
- 
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
- Ubuntu-Docker-3
### 2 Switches
- Switch-1
- Switch-2
### 1 Router
- Router
## IP Addressing Scheme
- Ubuntu-Docker-1: 192.168.0.10/24 (Interface connected to Switch1)
- Ubuntu-Docker-2: 192.168.0.20/24 (Interface connected to Switch2)
- Ubuntu-Docker-3: 192.168.0.30/24 (Interface connected to Switch2)

## Process
### Step 1: Create a new project
Open GNS3 and create a new project by going to File -> New Project
### Step 2: Design the Network Topology

- Add Devices:
For a basic setup, we use 3 Ubuntu Docker containers, 2 Switches and 1 Router

- Connect Devices:

![Screenshot 2024-08-28 140052](https://github.com/user-attachments/assets/f2a4a5aa-287a-44ab-b275-c262c01a6af9)

### Step 3: Assigning Static IP address
- Open console for Router
  
```enable``` <br>
```conf t``` <br>
```int g0/0``` <br>
```ip address 192.168.0.1 255.255.255.0``` <br>
```no shut``` <br>
```end``` <br>

![Screenshot 2024-08-28 134019](https://github.com/user-attachments/assets/3a20f91c-514b-4ffe-90e2-6887594b4560)

- Open console for Ubuntu-Docker-1

```sh
ip addr add 192.168.0.10/24
ip link set dev eth0 up
ip route add default via 192.168.0.1
```

![Screenshot 2024-08-28 123615](https://github.com/user-attachments/assets/13e5e6b2-95d8-431d-af97-dd988af428c0)

- Open console for Ubuntu-Docker-2

```sh
ip addr add 192.168.0.20/24
ip link set dev eth0 up
ip route add default via 192.168.0.1
```

![Screenshot 2024-08-28 135151](https://github.com/user-attachments/assets/07ba4112-7cec-4fc5-9ce0-2188d41d8ba4)

- Open console for Ubuntu-Docker-3

```sh
ip addr add 192.168.0.30/24
ip link set dev eth0 up
ip route add default via 192.168.0.1
```
![Screenshot 2024-08-28 140021](https://github.com/user-attachments/assets/d932858d-601f-459d-be99-bb1dcc2b0dbd)

### Step 4: Pinging devices

```sh
ping 192.168.0.20
```
