# school-campus-network
School campus network design using Cisco Packet Tracer with VLANs, DHCP, DNS, ACLs, STP, and Port Security.
# School Campus Network Design — Cisco Packet Tracer

##  Project Overview

This project demonstrates the design and configuration of a school campus network using **Cisco Packet Tracer**. The network is divided into multiple VLANs to improve network segmentation, security, and manageability.

The project includes inter-VLAN routing, DHCP, DNS, Access Control Lists (ACLs), Spanning Tree Protocol (STP), redundant switch links, and switch port security.

## Project Objectives

- Design a segmented school campus network.
- Configure VLANs for different departments.
- Enable communication between VLANs using Router-on-a-Stick.
- Automatically assign IP addresses using DHCP.
- Configure DNS for internal name resolution.
- Apply ACLs to control communication between departments.
- Understand STP and redundant link behavior.
- Configure switch port security to protect access ports.

##  Network Topology

The network consists of the following devices:

- 1 × Cisco 2911 Router
- 4 × Cisco 2960 Switches
- 8 × PCs
- 1 × Server


An additional link between SCHOOL-SW1 and SCHOOL-SW2 is used to practice redundant switching links and STP behavior.

##  VLAN Configuration

| VLAN ID | VLAN Name | Network Address | Default Gateway |
|---|---|---|---|
| 10 | ADMIN | 192.168.10.0/24 | 192.168.10.1 |
| 20 | TEACHERS | 192.168.20.0/24 | 192.168.20.1 |
| 30 | COMPUTER-LAB | 192.168.30.0/24 | 192.168.30.1 |
| 40 | LIBRARY | 192.168.40.0/24 | 192.168.40.1 |
| 50 | SERVER | 192.168.50.0/24 | 192.168.50.1 |

##  Technologies and Features

### 1. VLAN Configuration
Created separate VLANs for Administration, Teachers, Computer Lab, Library, and Servers.

### 2. Trunking
Configured trunk links between switches and between the core switch and router to carry multiple VLANs.

### 3. Inter-VLAN Routing
Configured Router-on-a-Stick using router subinterfaces and IEEE 802.1Q encapsulation.

### 4. DHCP
Configured DHCP pools on the router to automatically assign IP addresses, default gateways, and DNS server information to client PCs.

### 5. DNS
Configured an internal DNS service on the server with the hostname `school.local`.

- DNS Server: `192.168.50.10`
- Hostname: `school.local`

### 6. Access Control Lists (ACLs)
Implemented an extended ACL to restrict traffic from the Computer Lab VLAN to the Administration VLAN while permitting other configured traffic.

**Security policy:** Computer Lab devices should not initiate communication with Administration devices. Administration-to-Lab access and return traffic must be tested to verify the intended policy.

### 7. Spanning Tree Protocol (STP)
Configured SCHOOL-SW1 as the preferred root bridge for VLANs 10, 20, 30, 40, and 50.

STP helps prevent Layer 2 switching loops when redundant links exist.

### 8. Redundant Links
Added an extra link between SCHOOL-SW1 and SCHOOL-SW2 to practice STP port roles, blocking behavior, and link-failure recovery.

### 9. Port Security
Configured port security on Administration access ports.

- Maximum secure MAC addresses: 1
- MAC address learning: Sticky
- Violation action: Shutdown

##  Verification Commands

Use the following commands to verify the configuration.

**VLANs**
```cisco
show vlan brief
```

**Trunk links**
```cisco
show interfaces trunk
```

**STP**
```cisco
show spanning-tree vlan 10
```

**Router interfaces**
```cisco
show ip interface brief
```

**DHCP leases**
```cisco
show ip dhcp binding
```

**ACL**
```cisco
show access-lists
```

**Port Security**
```cisco
show port-security
show port-security address
```

**Connectivity**
```text
ipconfig
ping 192.168.10.1
ping 192.168.50.10
```

##  Security and Design Benefits

- Department-wise network segmentation
- Controlled inter-VLAN communication
- Centralized DHCP and internal DNS
- Reduced risk of Layer 2 switching loops
- Basic protection against unauthorized devices
- Improved troubleshooting and network management

##  Skills Demonstrated

- Cisco IOS CLI configuration
- VLANs and 802.1Q trunking
- Router-on-a-Stick
- DHCP and DNS
- Extended ACLs
- STP and switching redundancy
- Port Security
- Network troubleshooting and connectivity testing

##  Future Improvements

- Configure DHCP Snooping and Dynamic ARP Inspection.
- Implement Rapid Spanning Tree Protocol (RSTP).
- Add a dedicated wireless network for students and staff.
- Configure centralized logging and network monitoring.
- Document successful connectivity and failover test results.
- Improve ACL rules to enforce the school's security policy.

##  Software Used

- Cisco Packet Tracer

##  Author

**Suman Talukdar**

B.Sc. Information Technology | CCNA Certified

Interested in Network Engineering, NOC Operations, and Network Security.

---

*This project was created for hands-on networking practice and CCNA skill development. Configuration and security policies should be validated in Cisco Packet Tracer before deployment.*
