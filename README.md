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

![Topology](Cyber%20Internhsip%20Assignment%203/01_topology.png)

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

## ⚙️ Configuration Summary

Static routing was configured on all three routers so each LAN could reach the other two.
