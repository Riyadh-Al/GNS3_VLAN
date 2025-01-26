# Layer 3 Switching and Inter-VLAN Routing with Cisco 3600 Router

# Layer 3 Switching and Inter-VLAN Routing

<div align="center">
  <img src="https://i.imgur.com/Yd7jZXh.png" alt="Network Topology" width="600">
</div>

This project demonstrates the configuration of a Cisco 3600 router...



## Project Overview

This project demonstrates the transformation of a **Cisco 3600 Router** into a **Layer 3 switch** using the **NM-16ESW (Ethernet Switching) module** in a simulated **GNS3 environment**. The setup includes configuring VLANs, enabling inter-VLAN routing, and testing connectivity, showcasing essential skills in enterprise network design and management.

---

## Table of Contents

- [Network Topology](#network-topology)
- [Components](#components)
- [Configuration Details](#configuration-details)
  - [VLAN Configuration](#vlan-configuration)
  - [Router Configuration](#router-configuration)
  - [Host Configuration](#host-configuration)
- [Testing and Verification](#testing-and-verification)
- [Skills Demonstrated](#skills-demonstrated)
- [Future Improvements](#future-improvements)
- [References](#references)

---

## Network Topology

<div align="center">
  <img src="topology/network_topology.png" alt="Network Topology" width="800">
</div>

*Figure: Network topology showing the Cisco 3600 router acting as a Layer 3 switch, VLANs, and connected hosts.*

---

## Components

- **Router:** Cisco 3600 Router with NM-16ESW module (Layer 3 switch functionality).
- **Simulation Tool:** GNS3 for building and testing the network.
- **End Devices:** Three PCs configured in two separate VLANs.
- **VLANs:**
  - **VLAN 10**: Sales (10.10.0.0/24)
  - **VLAN 20**: Marketing (10.20.0.0/24)

---

## Configuration Details

### VLAN Configuration (NM-16ESW Module)

```bash
vlan database
vlan 10 name Sales
vlan 20 name Marketing
exit

interface e1
switchport mode access
switchport access vlan 10
exit

interface e2
switchport mode access
switchport access vlan 20
exit

interface e3
switchport mode trunk
switchport trunk encapsulation dot1q
exit
