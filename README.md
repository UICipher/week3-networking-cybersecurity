# Networking for Cybersecurity — Week 3

**AstraQuantum Tech | Summer of Cybersecurity 2026**

[![Status](https://img.shields.io/badge/status-completed-brightgreen)]()
[![Tool](https://img.shields.io/badge/tool-Cisco%20Packet%20Tracer-blue)]()

---

## 📌 Overview

This project demonstrates a complete networking-for-cybersecurity workflow: designing 
and building a three-router enterprise network, implementing static routing, verifying 
end-to-end connectivity, and analyzing live traffic (ARP, ICMP, TCP/UDP) to understand 
how packets actually move across a network — and what that means from a security 
monitoring perspective.

**Theme:** Build → Configure → Test → Analyze → Secure

---

## 🖧 Network Topology

![Topology](01_topology.png)

| Component | Count |
|---|---|
| Routers (Cisco 2911) | 3 |
| Switches (Cisco 2960) | 3 |
| End Devices (PCs) | 3 |
| LANs | 3 |
| Router-to-Router Links | 2 |

---

## 🌐 IP Addressing Scheme

| Segment | Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|---|
| LAN 1 | R1 | G0/0 | 192.168.10.1 | 255.255.255.0 |
| LAN 1 | PC1 | NIC | 192.168.10.10 | 255.255.255.0 |
| R1 ↔ R2 | R1 | G0/1 | 10.0.12.1 | 255.255.255.252 |
| R1 ↔ R2 | R2 | G0/0 | 10.0.12.2 | 255.255.255.252 |
| LAN 2 | R2 | G0/1 | 192.168.20.1 | 255.255.255.0 |
| LAN 2 | PC2 | NIC | 192.168.20.10 | 255.255.255.0 |
| R2 ↔ R3 | R2 | G0/2 | 10.0.23.1 | 255.255.255.252 |
| R2 ↔ R3 | R3 | G0/0 | 10.0.23.2 | 255.255.255.252 |
| LAN 3 | R3 | G0/1 | 192.168.30.1 | 255.255.255.0 |
| LAN 3 | PC3 | NIC | 192.168.30.10 | 255.255.255.0 |

---
ip route <destination network> <subnet mask> <next-hop IP>


Verified using `show ip interface brief` and `show ip route` on each router.

---

## ✅ Connectivity Verification

- Full mesh connectivity confirmed: PC1 ↔ PC2 ↔ PC3
- `tracert` confirms traffic path: **PC1 → R1 → R2 → R3 → PC3**
- Routing tables verified with static routes (`S`) present on all three routers

---

## 🔍 Traffic Analysis

Performed in Packet Tracer **Simulation Mode**, inspecting PDU details hop-by-hop.

| Protocol | Key Observation |
|---|---|
| ARP | PC1 broadcasts ARP request to resolve its default gateway before sending ICMP traffic |
| ICMP | TTL decrements at each router hop; source/destination MAC changes hop-by-hop while IP stays constant end-to-end |
| TCP/UDP | Source/destination ports inspected to distinguish connection-oriented vs. connectionless behavior |

---

## 🛠️ Troubleshooting Exercise

| Stage | Detail |
|---|---|
| **Problem** | Static route to `192.168.30.0/24` removed from R2 |
| **Evidence** | Ping from PC1 to PC3 failed |
| **Diagnosis** | `show ip route` on R2 confirmed missing route |
| **Solution** | Re-added `ip route 192.168.30.0 255.255.255.0 10.0.23.2` |
| **Verification** | Ping from PC1 to PC3 succeeded |

---

## 📚 Online Labs Completed

| Lab | Platform | Status |
|---|---|---|
| Network Packet Analysis | LetsDefend | ✅ Completed |
| Network Services | TryHackMe | ✅ Completed |
| Network Services 2 | TryHackMe | ✅ Completed |
| DNS in Detail | TryHackMe | ✅ Completed |
| Network Security Essentials | TryHackMe | ✅ Completed |
| Pickle Rick (CTF) | TryHackMe | ✅ Completed |

---

## 📁 Repository Contents

- `UmarImran_Week3_Networking_Assesment.pkt` — Cisco Packet Tracer source file
- Screenshots — full evidence set covering topology, configuration, verification, 
  traffic analysis, and troubleshooting

---

## 🎯 Key Takeaway

IP addressing stays consistent end-to-end while MAC addressing changes at every hop — 
understanding this distinction is foundational to network traffic analysis and, by 
extension, to SOC monitoring and incident detection.
## ⚙️ Configuration Summary

Static routing was configured on all three routers so each LAN could reach the other two.
