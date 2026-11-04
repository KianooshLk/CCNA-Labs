# 01 – Static Routing & SSH: Parsa Logistics

![Routing](https://img.shields.io/badge/Routing-Static-blue)
![SSH](https://img.shields.io/badge/Management-SSHv2-green)
![CCNA](https://img.shields.io/badge/Exam-CCNA%20200--301-orange)
![Tools](https://img.shields.io/badge/Tools-Packet%20Tracer%20%7C%20PNETLab-lightgrey)

CCNA 200-301 lab with an HQ, a branch and an ISP. All routing is static, and every device is managed only over SSH v2 (Telnet refused).



## Addressing

| Device | Interface | IP Address |
|---|---|---|
| R-HQ | G0/0 · G0/1 · G0/2 | 10.10.1.1/24 · 172.16.0.1/30 · 203.0.113.2/30 |
| R-BR | G0/0 · G0/1 | 10.10.2.1/24 · 172.16.0.2/30 |
| R-ISP | G0/0 · Lo0 | 203.0.113.1/30 · 8.8.8.8/32 |
| SW-HQ / SW-BR | Vlan1 | 10.10.1.2/24 · 10.10.2.2/24 |
| PC-HQ / PC-BR | Fa0 | 10.10.1.10/24 · 10.10.2.10/24 |

## Tasks

- Static route on R-HQ to the branch LAN
- Default routes: R-HQ → ISP, R-BR → HQ
- Summary route `10.10.0.0/22` on R-ISP
- SSH v2 on all devices: domain name, RSA 2048, local user, `transport input ssh`, timeouts

## Verification

```
show ip route static
show ip ssh
traceroute 8.8.8.8
ssh -l netadmin 10.10.2.1
```

**Expected:** PC-to-PC and PC-to-8.8.8.8 pings succeed, SSH works on all devices, Telnet is refused.

## Files

- [`topology.html`](topology.html) – topology and addressing (open in a browser)
- [`configs/`](configs/) – full configuration of every device
- [`screenshots/`](screenshots/) – verification outputs
- `parsa-static-ssh.pkt` – Packet Tracer lab file

## Skills Demonstrated

Static, default and summary routing · Route verification · SSH hardening
