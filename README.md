# Basic Network Topology & Configuration with GNS3
## Overview
This project demonstrates a basic network design and configuration using Cisco IOSv in GNS3. The setup includes configuring IP addressing, static routing, VLANs, and Inter-VLAN routing in a simulated environment. This will help us understand and implement fundamental networking concepts using GNS3 in a Virtualized Environment.
## Objectives
- Design and configure a small network topology with 3 Ubuntu docker containers, 2 Switches and a single Router.
- Implement basic IP addressing and subnetting.
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
- Ubuntu-Docker-1: 192.168.1.2/24 (Interface connected to Switch1)
- Ubuntu-Docker-2: 192.168.2.2/24 (Interface connected to Switch2)
- Ubuntu-Docker-3: 192.168.2.3/24 (Interface connected to Switch2)
- Router G0/0 (192.168.1.1)
         G0/1 (192.168.2.1)

# Process
## Step 1: Create a new project
Open GNS3 and create a new project by going to File -> New Project
### Step 2: Design the Network Topology

- Add Devices:
For a basic setup, we use 3 Ubuntu Docker containers, 2 Switches and 1 Router

- Connect Devices:

![Screenshot 2024-08-28 165544](https://github.com/user-attachments/assets/29ed5fb1-d82d-473c-b4d7-bf97d9eead36)

## Step 3: Assigning Static IP address
- Open console for Router

```sh
enable
conf t
int g0/0
ip address 192.168.1.1 255.255.255.0
int g0/1
ip address 192.168.2.1 255.255.255.0
no shut
end
wr
```
![Screenshot 2024-08-28 165923](https://github.com/user-attachments/assets/58a84d75-b6d2-474a-b00b-89817abb9bb1)

- Open console for Ubuntu-Docker-1

```sh
ip addr add 192.168.1.2/24 dev eth0
ip link set dev eth0 up
route add default gw 192.168.1.1 dev eth0
```
![Screenshot 2024-08-28 170113](https://github.com/user-attachments/assets/dba0f14b-db55-42ac-9a6f-fb90b967056f)

- Open console for Ubuntu-Docker-2

```sh
ip addr add 192.168.2.2/24 dev eth0
ip link set dev eth0 up
route add default gw 192.168.0.1 dev eth0
```

![Screenshot 2024-08-28 170223](https://github.com/user-attachments/assets/f33e31fd-b302-469a-9cc0-69a4c0b204c5)

- Open console for Ubuntu-Docker-3

```sh
ip addr add 192.168.2.3/24 dev eth0
ip link set dev eth0 up
route add default gw 192.168.2.1 dev eth0
```
![Screenshot 2024-08-28 170547](https://github.com/user-attachments/assets/78d09f43-52ad-49b7-98b1-cf17a4167824)

## Step 4: Testing Connectivity

From Ubuntu-Docker-1 to Ubuntu-Docker-3
```sh
ping 192.168.2.3
```
Output:

![Screenshot 2024-08-28 170816](https://github.com/user-attachments/assets/df98f711-9a9b-48b1-98cb-609aba1bb0fb)
