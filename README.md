# Layer 3 Switching and Inter-VLAN Routing

<p align="center">
    <a href="https://youtu.be/ZKg1Husvaqg"> 
        <img src="https://img.icons8.com/color/48/000000/youtube-play.png" width="50">
    </a>
    <br>
    <strong>Click Above For YouTube Demonstration</strong>
</p>


## Project Overview

This project demonstrates the configuration of VLANs and inter-VLAN routing using GNS3. The setup includes a Cisco 3600 router with an NM-16ESW module, allowing it to function as a Layer 3 switch. This configuration showcases fundamental networking skills such as VLAN creation, trunking, and routing between VLANs.

---

## Network Topology

<div align="center">
  <img src="https://i.imgur.com/Yd7jZXh.png" alt="Network Topology" width="600">
</div>

*Figure: Network topology showing VLANs and inter-VLAN routing setup.*

---

## Configuration Details

### VLAN Configuration
```plaintext
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
```

### Router Configuration
```plaintext
conf t
hostname Router1

interface f0/0
no shut

interface f0/0.10
encapsulation dot1q 10
ip address 10.10.0.1 255.255.255.0
exit

interface f0/0.20
encapsulation dot1q 20
ip address 10.20.0.1 255.255.255.0
exit
```

### Host Configuration

- **PC1 (VLAN 10):**
  - IP Address: `10.10.0.2`
  - Subnet Mask: `255.255.255.0`
  - Default Gateway: `10.10.0.1`

- **PC2 (VLAN 20):**
  - IP Address: `10.20.0.2`
  - Subnet Mask: `255.255.255.0`
  - Default Gateway: `10.20.0.1`

- **PC3 (VLAN 20):**
  - IP Address: `10.20.0.3`
  - Subnet Mask: `255.255.255.0`
  - Default Gateway: `10.20.0.1`

---

## Testing and Verification

### Ping Test Results

- **PC1 (VLAN 10) to PC2 (VLAN 20):** Success
[img]https://i.imgur.com/mKa2jsu.png 
- **PC2 (VLAN 20) to PC3 (VLAN 20):** Success

PC1:

  <img src="https://i.imgur.com/mKa2jsu.png" width="600">

  
PC2: 

  <img src="https://i.imgur.com/5EHavhp.png" width="600">
  

*Figure: Ping results confirming inter-VLAN connectivity.*

---

## Skills Demonstrated

- **VLAN Configuration:** Logical segmentation of the network.
- **Inter-VLAN Routing:** Routing traffic between VLANs using subinterfaces.
- **Network Simulation:** Practical experience with GNS3 to build and test network topologies.
- **Troubleshooting:** Diagnosing and resolving connectivity issues.

---

## Future Improvements

- Implement dynamic routing protocols like OSPF or EIGRP.
- Enhance security using Access Control Lists (ACLs).
- Automate configuration with Python or shell scripts.

---

## How to Recreate This Setup

1. Add a **Cisco 3600 Router** to your GNS3 topology.
2. Install the **NM-16ESW module** on the router.
3. Configure VLANs, trunking, and routing as described in the configuration files.
4. Assign IP addresses to hosts within their respective VLANs.
5. Test connectivity using `ping` and verify with packet captures.


**
