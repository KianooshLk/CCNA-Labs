# Multi-Area OSPF – Zagros Logistics

![Protocol](https://img.shields.io/badge/Protocol-OSPFv2-blue)
![Level](https://img.shields.io/badge/Exam-CCNA%20200--301-green)
![Platform](https://img.shields.io/badge/Platform-PNETLab-orange)
![Areas](https://img.shields.io/badge/Areas-0%20%7C%2010%20%7C%2020-lightgrey)

A CCNA 200-301 lab implementing **multi-area OSPFv2** for a fictional company, **Zagros Logistics**, with a headquarters and two branch offices. The design covers DR/BDR control, point-to-point links, passive interfaces, timer tuning, and MD5 authentication.

---

## 📌 Overview

| Item | Details |
|---|---|
| **Scenario** | Headquarters + two branch sites |
| **Routing protocol** | OSPFv2 (multi-area) |
| **Areas** | Area 0 (backbone), Area 10, Area 20 |
| **Platform** | PNETLab |
| **Focus** | Area design, ABR behavior, DR/BDR election, authentication, route analysis |

> **Note:** PNETLab labs cannot be exported as a single file here, so verification screenshots are provided instead of a lab file.

---

## 🎯 Objectives

- Design and configure a multi-area OSPF network with a proper backbone
- Control **DR/BDR election** using interface priority and router ID
- Configure **point-to-point** network type on WAN links
- Secure adjacencies with **OSPF MD5 authentication**
- Tune **hello/dead timers** and verify they match on neighbors
- Use **passive interfaces** on LAN-facing ports
- Analyze the routing table and distinguish **O** vs **O IA** routes

---

## 🗺️ Topology

Open [`topology.html`](topology.html) in a browser for the interactive topology and full addressing plan.



---

## 📁 Repository Structure

```
.
├── topology.html        # Topology and addressing plan (open in browser)
├── configs/             # Full running configuration of every device
└── screenshots/         # PNETLab topology and verification outputs
```

---

## ⚙️ Key Configuration Features

| Feature | Purpose |
|---|---|
| Multi-area design (0 / 10 / 20) | Scalability and reduced LSA flooding |
| ABR | Inter-area route exchange between backbone and non-backbone areas |
| DR/BDR control | Deterministic election on multi-access segments |
| `ip ospf network point-to-point` | Removes DR/BDR election on WAN links, faster convergence |
| `passive-interface` | Stops OSPF hellos toward end-user LANs |
| Hello/Dead timer tuning | Faster failure detection |
| MD5 authentication | Prevents unauthorized routers from forming adjacencies |

---

## ✅ Verification

All outputs are available in the [`screenshots/`](screenshots/) folder.

| Command | What it verifies |
|---|---|
| `show ip ospf neighbor` | Adjacency state (FULL) and DR/BDR roles |
| `show ip ospf interface` | Area, network type, timers, authentication, priority |
| `show ip route ospf` | Learned routes: `O` (intra-area) and `O IA` (inter-area) |
| `show ip protocols` | Router ID, networks, passive interfaces |
| `ping PC-BR1 ↔ PC-BR2` | End-to-end connectivity between the two branches |

---

## 🧠 Skills Demonstrated

- Multi-area OSPF design
- ABR configuration and inter-area routing
- DR/BDR election control
- OSPF MD5 authentication
- Timer tuning
- Route analysis (`O` / `O IA`)
- Network documentation and troubleshooting workflow

---

## 🚀 How to Reproduce

1. Build the topology in PNETLab following `topology.html`.
2. Apply the configuration from each file in `configs/` to the matching device.
3. Wait for adjacencies to reach **FULL** state.
4. Run the verification commands and compare with the screenshots.

---

## 📜 License

This project is for educational purposes.
