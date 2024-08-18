# Basic Network Design & Configuration with GNS3
## Overview
This project demonstrates a basic network design and configuration using Cisco IOSv in GNS3. The setup includes configuring IP addressing, static routing, VLANs, and Inter-VLAN routing in a simulated environment. This will help us understand and implement fundamental networking concepts using GNS3 in a Virtualized Environment.
## Objectives
- Design and configure a small network topology with 3 routers and 2 switches.
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
### 3 Routers
- Router1
- Router2
- Router3
### 2 Switches
- Switch1
- Switch2
## IP Addressing Scheme
- Router1: 192.168.1.1/24 (Interface connected to Switch1)
- Router2: 192.168.1.2/24 (Interface connected to Switch1)
- Router3: 192.168.2.1/24 (Interface connected to Switch2)

## Process
### Step 1: Create a new project
Open GNS3 and create a new project by going to File -> New Project
### Step 2: Design the Network Topology

- Add Devices:
For a basic setup, we use 3 routers and 2 switches.

- Connect Devices:
Connecting routers to each other using serial or Ethernet links.
Connecting switches to routers or to each other if implementing VLANs.
