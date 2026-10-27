# OSPF Routing — Cisco Packet Tracer

## Overview
This lab demonstrates dynamic routing between three routers using OSPF (Open Shortest Path First) in Cisco Packet Tracer.

## Objectives
- Configure IPv4 addresses on router interfaces.
- Connect three routers in a triangular topology.
- Configure OSPF in area 0.
- Verify OSPF neighbor adjacencies and routing tables.
- Test end-to-end connectivity between three LANs.

## Network Topology
- 3 Cisco routers: R1, R2 and R3
- 3 Cisco 2960 switches: S1, S2 and S3
- 3 PCs: PC0, PC1 and PC2

## IP Addressing Plan

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.1.10 | 255.255.255.0 |
| R1 | GigabitEthernet0/0 | 192.168.1.1 | 255.255.255.0 |
| R1 | GigabitEthernet0/1 | 10.0.12.1 | 255.255.255.252 |
| R1 | GigabitEthernet0/2 | 10.0.13.1 | 255.255.255.252 |
| PC1 | FastEthernet0 | 192.168.2.10 | 255.255.255.0 |
| R2 | GigabitEthernet0/0 | 192.168.2.1 | 255.255.255.0 |
| R2 | GigabitEthernet0/1 | 10.0.12.2 | 255.255.255.252 |
| R2 | GigabitEthernet0/2 | 10.0.23.1 | 255.255.255.252 |
| PC2 | FastEthernet0 | 192.168.3.10 | 255.255.255.0 |
| R3 | GigabitEthernet0/0 | 192.168.3.1 | 255.255.255.0 |
| R3 | GigabitEthernet0/1 | 10.0.13.2 | 255.255.255.252 |
| R3 | GigabitEthernet0/2 | 10.0.23.2 | 255.255.255.252 |

## PC Default Gateways
- PC0: 192.168.1.1
- PC1: 192.168.2.1
- PC2: 192.168.3.1

## OSPF Configuration

All routers use OSPF process 1 in area 0.

### R1
```text
router ospf 1
 router-id 1.1.1.1
 network 192.168.1.0 0.0.0.255 area 0
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.13.0 0.0.0.3 area 0
```

### R2
```text
router ospf 1
 router-id 2.2.2.2
 network 192.168.2.0 0.0.0.255 area 0
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.23.0 0.0.0.3 area 0
```

### R3
```text
router ospf 1
 router-id 3.3.3.3
 network 192.168.3.0 0.0.0.255 area 0
 network 10.0.13.0 0.0.0.3 area 0
 network 10.0.23.0 0.0.0.3 area 0
```

## Verification
- Verified OSPF neighbors using `show ip ospf neighbor`.
- Verified learned routes using `show ip route`.
- Confirmed that R3 learned the 192.168.1.0/24 and 192.168.2.0/24 networks through OSPF.
- Tested connectivity between PCs in different LANs. Successful replies were received after initial timeouts during the first ping.

## Project File
- `03-ospf-routing.pkt` — Cisco Packet Tracer topology.

## Tools
Cisco Packet Tracer, Cisco IOS CLI, IPv4, OSPF.
