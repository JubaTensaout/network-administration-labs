# Static Routing — Cisco Packet Tracer

## Overview
This project demonstrates static routing between two LANs using Cisco routers.

## Objectives
- Configure IPv4 addresses on router interfaces.
- Connect two LANs through an inter-router link.
- Configure static routes.
- Verify end-to-end connectivity.

## Network Topology
- 2 Cisco 2911 routers: R1 and R2
- 2 Cisco 2960 switches: S1 and S2
- 2 PCs: PC0 and PC1

## IP Addressing Plan

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.1.10 | 255.255.255.0 |
| R1 | GigabitEthernet0/0 | 192.168.1.1 | 255.255.255.0 |
| R1 | GigabitEthernet0/1 | 10.0.0.1 | 255.255.255.252 |
| R2 | GigabitEthernet0/1 | 10.0.0.2 | 255.255.255.252 |
| R2 | GigabitEthernet0/0 | 192.168.2.1 | 255.255.255.0 |
| PC1 | FastEthernet0 | 192.168.2.10 | 255.255.255.0 |

## Static Routing Configuration

On R1:
`ip route 192.168.2.0 255.255.255.0 10.0.0.2`

On R2:
`ip route 192.168.1.0 255.255.255.0 10.0.0.1`

## Verification
- Checked routing tables using `show ip route`.
- Verified connectivity between the routers.
- Successfully tested ping from PC0 to PC1.

## Project File
- `02-static-routing.pkt` — Cisco Packet Tracer topology.

## Tools
Cisco Packet Tracer, Cisco IOS CLI, IPv4 static routing.
