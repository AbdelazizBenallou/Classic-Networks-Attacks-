# 🏢 Enterprise LAN Configuration

![Topology](topology.png)

> A complete enterprise Local Area Network deployment using VLAN segmentation,
> Router-on-a-Stick inter-VLAN routing, and centralized DHCP provisioning.

---

## 📋 Overview

This project implements a segmented enterprise LAN architecture across **5 VLANs**,
designed and documented as part of a network engineering study.
Each VLAN isolates a specific organizational unit with its own subnet,
gateway, and DHCP address pool.

---

## 🗂️ VLAN Architecture

| VLAN ID | Name    | Subnet              | Gateway           |
|---------|---------|---------------------|-------------------|
| 1       | Default | 192.168.1.0/24      | 192.168.1.254     |
| 10      | HR      | 192.168.10.0/24     | 192.168.10.254    |
| 20      | IT      | 192.168.20.0/24     | 192.168.20.254    |
| 99      | Servers | 192.168.99.0/24     | 192.168.99.254    |
| 100     | Admin   | 192.168.100.0/24    | 192.168.100.254   |

---

## ⚙️ Technologies Used

- **Cisco IOS** — Switch & Router configuration
- **IEEE 802.1Q** — VLAN trunking (dot1q encapsulation)
- **Router-on-a-Stick** — Single-interface inter-VLAN routing
- **ISC DHCP Server** — Centralized IP assignment via `isc-dhcp-server`
- **DHCP Relay** — `ip helper-address` for cross-VLAN lease distribution

---

## 📁 Project Structure

```
enterprise-lan-config/
├── configs/
│   ├── sw1-config.txt        # Switch 1 configuration
│   ├── sw2-config.txt        # Switch 2 configuration
│   └── router-config.txt     # Router subinterface configuration
├── dhcp/
│   └── dhcpd.conf            # ISC DHCP server config
├── topology.png              # Network topology diagram
├── Enterprise_LAN_Configuration_Guide.pdf
└── README.md
```

---

## 🚀 Deployment Steps

1. **Switch** — Create VLANs, assign access ports, configure trunk uplinks
2. **DHCP Server** — Static IP in VLAN 99, configure pools for all VLANs
3. **Router** — Create subinterfaces per VLAN with `ip helper-address`

> Full step-by-step documentation available in the PDF guide.

---

## 🔍 Verification Commands

```bash
do sh ip int br      # Check subinterface IPs
do sh vlan           # Verify VLAN-to-port mapping
do sh run            # Full running config
do sh ip route       # Router routing table
```

---

## 👨‍🏫 Supervisor

**Prof. Abdelaziz**

---
