# Lab Network Design

## Addressing - 10.10.10.0/24 (VMware VMnet2, host-only)
| Machine | IP | Role |
|---|---|---|
| Kali | 10.10.10.10 | Attacker |
| Metasploitable2 | 10.10.10.20 | Vulnerable target |
| Ubuntu web target | 10.10.10.30 | DVWA, Juice Shop |
| Wazuh server | 10.10.10.40 | SIEM (Phase 7) |

## Design decisions
- **Host-only network:** To maintain isolation from home/work network and internet.
- **No host virtual adapter:** Prevents host exploitation and eliminate accidental leaks
- **Static IPs instead of DHCP:** Pradictable environment and isolation of the lab
- **Install on NAT, then isolate:** Efficient patching and provisioning, hardening before exposure