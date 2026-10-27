VLAN Segmentation, Inter-VLAN Routing & ACL

Overview

This lab demonstrates how to configure VLAN segmentation, establish communication between different VLANs using Router-on-a-Stick, and implement an Access Control List (ACL) to restrict traffic between departments.

The lab was built and tested using Cisco Packet Tracer.

Objectives

- Create and configure VLANs.
- Assign switch ports to the appropriate VLANs.
- Configure 802.1Q trunk links.
- Implement inter-VLAN routing using a Cisco router.
- Configure an extended ACL to restrict communication between departments.
- Verify connectivity using ICMP ping tests.

Network Topology

Devices

- 2 × Cisco Catalyst 2960 switches
- 1 × Cisco 2911 router
- 6 × PCs

VLAN and IP Addressing Plan

VLAN| Department| Network| Default Gateway
10| Development| 192.168.10.0/24| 192.168.10.1
20| HR| 192.168.20.0/24| 192.168.20.1
30| Administration| 192.168.30.0/24| 192.168.30.1

Technologies and Concepts

- Cisco IOS
- VLANs and access ports
- IEEE 802.1Q trunking
- Router-on-a-Stick
- Extended Access Control Lists (ACLs)
- ICMP connectivity testing
- IPv4 addressing and subnet masks

ACL Configuration

An extended ACL was configured on the router to block traffic originating from the HR network and destined for the Development network.

ip access-list extended BLOCK-RH-TO-DEV
 deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
 permit ip any any

The ACL was applied inbound on subinterface "GigabitEthernet0/0.20".

Verification and Results

- Communication within the same VLAN: successful.
- Inter-VLAN routing: successful before applying the ACL.
- Communication between Development and Administration: successful.
- Traffic from HR to Development: blocked by the ACL.
- Ping tests between HR and Development: unsuccessful, as the ACL also blocks the ICMP reply traffic.

Files

- "01-vlan-intervlan.pkt" — Cisco Packet Tracer project file.

Skills Demonstrated

Network segmentation, switch configuration, trunking, inter-VLAN routing, ACL implementation, and network troubleshooting.

---

Author: Juba Tensaout
Field: Network Administration & Security
