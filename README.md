# week3-networking-cybersecurity
Three-router network built in Cisco Packet Tracer with static routing, ARP/ICMP/TCP traffic analysis, and a documented troubleshooting scenario — Week 3 of AstraQuantum Tech's Summer of Cybersecurity 2026.
# Week 3 — Networking for Cybersecurity
### AstraQuantum Tech — Summer of Cybersecurity 2026

## Overview
This project covers a full networking-for-cybersecurity assessment: building a 
3-router enterprise network in Cisco Packet Tracer, configuring static routing, 
testing connectivity, and analyzing ARP/ICMP/TCP traffic to connect networking 
fundamentals with SOC-relevant security concepts.

## Topology
![Topology](screenshots/01_topology.png)

3 Routers, 3 Switches, 3 PCs, 3 LANs, static routing between all networks.

## IP Addressing

| Segment | Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|---|
| LAN 1 | R1 | G0/0 | 192.168.10.1 | 255.255.255.0 |
| LAN 1 | PC1 | NIC | 192.168.10.10 | 255.255.255.0 |
| R1↔R2 | R1 | G0/1 | 10.0.12.1 | 255.255.255.252 |
| R1↔R2 | R2 | G0/0 | 10.0.12.2 | 255.255.255.252 |
| LAN 2 | R2 | G0/1 | 192.168.20.1 | 255.255.255.0 |
| LAN 2 | PC2 | NIC | 192.168.20.10 | 255.255.255.0 |
| R2↔R3 | R2 | G0/2 | 10.0.23.1 | 255.255.255.252 |
| R2↔R3 | R3 | G0/0 | 10.0.23.2 | 255.255.255.252 |
| LAN 3 | R3 | G0/1 | 192.168.30.1 | 255.255.255.0 |
| LAN 3 | PC3 | NIC | 192.168.30.10 | 255.255.255.0 |

## Verification
- Routing tables confirmed via `show ip route` on R1, R2, R3
- Full connectivity tested: PC1 ↔ PC2 ↔ PC3
- Traceroute confirms path PC1 → R1 → R2 → R3 → PC3

## Traffic Analysis
- **ARP** — captured in Simulation Mode before ICMP traffic
- **ICMP** — echo request/reply inspected hop-by-hop, TTL decrement observed
- **TCP/UDP** — source/destination ports and connection behavior compared

## Troubleshooting
A static route was intentionally removed from R2, breaking PC1 → PC3 connectivity. 
Diagnosed via `show ip route`, fixed by re-adding the route, and verified with ping.

## Online Labs Completed

| Lab | Platform | Status |
|---|---|---|
| Network Packet Analysis | LetsDefend | ✅ |
| Network Services | TryHackMe | ✅ |
| Network Services 2 | TryHackMe | ✅ |
| DNS in Detail | TryHackMe | ✅ |
| Network Security Essentials | TryHackMe | ✅ |
| Pickle Rick | TryHackMe | ✅ |

## Files
- `UmarImran_Week3_Networking_Assesment.pkt` — Packet Tracer source file
- `screenshots/` — all evidence screenshots
