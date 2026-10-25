# 01 - Static Route & SSH: Parsa Logistics

CCNA 200-301 lab (Packet Tracer / PNETLab). An HQ, a branch and an ISP, with all routing static and every device managed only over SSH v2.

## Topology
See [`topology.html`](topology.html). Devices: R-HQ, R-BR, R-ISP, SW-HQ, SW-BR, PC-HQ, PC-BR.

| Device | Interface | IP |
|--------|-----------|----|
| R-HQ | G0/0, G0/1, G0/2 | 10.10.1.1/24, 172.16.0.1/30, 203.0.113.2/30 |
| R-BR | G0/0, G0/1 | 10.10.2.1/24, 172.16.0.2/30 |
| R-ISP | G0/0, Lo0 | 203.0.113.1/30, 8.8.8.8/32 |
| SW-HQ / SW-BR | Vlan1 | 10.10.1.2/24, 10.10.2.2/24 |
| PC-HQ / PC-BR | Fa0 | 10.10.1.10/24, 10.10.2.10/24 |

## Tasks
- Static route on R-HQ to the branch LAN
- Default routes on R-HQ (to ISP) and R-BR (to HQ)
- Summary route 10.10.0.0/22 on R-ISP
- SSH v2 on all devices: domain name, RSA 2048, local user, VTY `transport input ssh`, timeouts

## Verification
```
show ip route static
show ip ssh
traceroute 8.8.8.8
ssh -l netadmin 10.10.2.1
```
Expected: PC-to-PC and PC-to-8.8.8.8 ping succeed, SSH works on all devices, Telnet is refused.

## Files
`topology.html`, `configs/`, `screenshots/`, `parsa-static-ssh.pkt`

## Skills
Static/default/summary routing, route verification, SSH hardening.
