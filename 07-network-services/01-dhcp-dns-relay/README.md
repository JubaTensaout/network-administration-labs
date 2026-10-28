# DHCP and DNS Services — Cisco Packet Tracer

## Overview
This lab demonstrates centralized DHCP and DNS services across two separate LANs, using a Cisco router as a DHCP relay.

## Objectives
- Configure IPv4 addresses on router interfaces.
- Configure a centralized DHCP server.
- Configure DHCP relay using `ip helper-address`.
- Configure DNS name resolution for an internal server.
- Verify IP address assignment and end-to-end connectivity.

## Network Topology
- 1 Cisco 2911 router: R1
- 2 Cisco 2960 switches: SW1 and SW2
- 1 DHCP/DNS server
- 3 PCs: PC0, PC1 and PC2

## IP Addressing Plan

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| R1 | GigabitEthernet0/0 | 192.168.10.1 | 255.255.255.0 |
| R1 | GigabitEthernet0/1 | 192.168.20.1 | 255.255.255.0 |
| DHCP/DNS Server | FastEthernet0 | 192.168.10.2 | 255.255.255.0 |
| PC0 | FastEthernet0 | DHCP | 255.255.255.0 |
| PC1 | FastEthernet0 | DHCP | 255.255.255.0 |
| PC2 | FastEthernet0 | DHCP | 255.255.255.0 |

## Network Segments

- **Server LAN:** `192.168.10.0/24`
  - Default gateway: `192.168.10.1`
  - DHCP/DNS server: `192.168.10.2`
- **Employees LAN:** `192.168.20.0/24`
  - Default gateway: `192.168.20.1`
  - Client addresses are assigned automatically by DHCP.

## DHCP Configuration

The DHCP service runs on the server in the Server LAN.

DHCP pool: `EMPLOYES`

- Network: `192.168.20.0/24`
- Default gateway: `192.168.20.1`
- DNS server: `192.168.10.2`
- Starting IP address: `192.168.20.100`
- Maximum users: `51`

## DHCP Relay Configuration

The router relays DHCP requests from the Employees LAN to the centralized DHCP server.

```text
interface GigabitEthernet0/1
 ip helper-address 192.168.10.2
```

## DNS Configuration

The DNS service is enabled on the server.

| Record Type | Name | IPv4 Address |
|---|---|---|
| A | serveur.entreprise.local | 192.168.10.2 |

The DNS record allows clients to resolve the internal server name to its IPv4 address.

## Verification

The following tests were performed:

- DHCP address assignment to client PCs.
- Connectivity between clients and the router.
- Connectivity between the Employees LAN and the server.
- DNS resolution of `serveur.entreprise.local`.
- Successful ping tests to verify connectivity.

## Project File
- `04-dhcp-dns-relay.pkt` — Cisco Packet Tracer topology.

## Tools
Cisco Packet Tracer, Cisco IOS CLI, IPv4, DHCP, DNS.
