# Enterprise Packet Tracer Network Lab – GRE over IPsec

<img width="1595" height="896" alt="GRE Over IPsec" src="https://github.com/user-attachments/assets/fc54efb2-8a74-45dc-b9e5-495955dc9895" />


## 📌 Overview

This repository documents an **enterprise-style network topology** built in **Cisco Packet Tracer**, designed to demonstrate real-world routing, redundancy, security, and site-to-site connectivity concepts.

The lab simulates a **primary campus network** and a **remote branch site**, interconnected via a **GRE tunnel secured with IPsec**, with dynamic routing handled by **OSPF** and resilient LAN design using **HSRP, EtherChannel, and Spanning Tree**.

This project is intended for:

* CCNA / CCNP-level study
* Hands-on enterprise design practice
* GRE over IPsec learning in a lab-safe environment

---

## 🗺️ Topology Highlights

### Core Design

* Hierarchical campus design (Access → Distribution → Edge)
* Dual distribution switches with HSRP
* Redundant Layer 2 uplinks using EtherChannel
* OSPF for internal and tunnel routing

### WAN & Security

* GRE tunnel between sites (10.10.10.0/30)
* IPsec securing GRE traffic
* NAT overload for internet-bound traffic
* Static routes for public peer reachability

### LAN Services

*attach image or link*

* VLAN segmentation:

  * VLAN 10 – Tech
  * VLAN 20 – HR
  * VLAN 30 – Finance
* Centralized DHCP & DNS server
* IP helper-address configured on SVIs

---

## 🔐 Security Features Implemented

### Layer 2 Security

* Port Security (sticky MAC)
* BPDU Guard
* PortFast
* DHCP Snooping
* Dynamic ARP Inspection (DAI)

### WAN Security

* IPsec Phase 1 (ISAKMP):

  * AES-256
  * Pre-shared keys
  * DH Group 5
* IPsec Phase 2:

  * ESP-AES-256
  * SHA-HMAC

---

## 🔁 Routing & Redundancy

### OSPF

* Area 1 for internal campus routing
* Area 0 for GRE tunnel
* Tuned OSPF costs for path preference

### HSRP

* Virtual gateways per VLAN:

  * 192.168.10.1
  * 192.168.20.1
  * 192.168.30.1
* Active/Standby roles split across distribution switches

---

## 🌐 NAT & Internet Access

* PAT (NAT overload) on both edge routers
* Default route toward ISP
* Internal networks translated:

  * 192.168.0.0/16
  * 172.16.0.0/24 (remote site)

---

## 📂 Repository Structure

```text
├── PT_files/GRE_IPSEC_Tunnel.pkt
│   ├── access-switches.txt
├── configs/
│   ├── access-switches.txt
│   ├── distribution-switches.txt
│   ├── edge-router-1.txt
│   └── edge-router-2.txt
├── diagrams/
│   └── topology.png
├── docs/
│   └── GRE-over-IPsec-steps.pdf
└── README.md
```

---

## ⚙️ Device Summary

### Access Switches (2960)

* VLAN access ports
* Port security (sticky MAC)
* Trunked EtherChannels upstream

### Distribution Switches (3560)

* Inter-VLAN routing
* HSRP
* OSPF adjacency to edge router
* Root bridge control

### Edge Routers (2911)

* OSPF
* NAT overload
* GRE tunnel
* IPsec encryption

### ISP Router

* Transit only
* Simulated public internet

---

## 🚀 How to Use This Lab

1. Open the `.pkt` file in Cisco Packet Tracer
2. Verify:

   * OSPF adjacencies
   * HSRP states
   * Tunnel status (`show int tunnel1`)
   * IPsec SAs (`show crypto isakmp sa`)
3. Test:

   * Inter-VLAN routing
   * Site-to-site connectivity
   * Internet access (ping 8.8.8.8)

---

## 🎯 Learning Objectives

* Design an enterprise-grade LAN
* Implement GRE over IPsec
* Secure Layer 2 access
* Understand routing boundaries and NAT
* Prepare for CCNA / CCNP Enterprise

---

## 📝 Notes

* Public IP ranges use **documentation subnets (203.0.113.0/24)**
* Designed purely for lab and educational use

---

## 🙌 Author

**Joseph Ferraro**
Enterprise Networking Lab – Cisco Packet Tracer
