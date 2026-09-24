# Lab Network Design

## Addressing - 10.10.10.0/24 (VMware VMnet2, host-only)
| Machine | IP | Role |
|---|---|---|
| Kali | 10.10.10.10 | Attacker |
| Metasploitable2 | 10.10.10.20 | Vulnerable target |
| Ubuntu web target | 10.10.10.30 | DVWA, Juice Shop |
| Wazuh server | 10.10.10.40 | SIEM (Phase 7) |

## Design decisions
- **Host-only network:** Keeps all lab traffic inside the laptop, isolated from the home network and the internet.
- **No host virtual adapter:** With it enabled, the Windows host would get an address (10.10.10.1) inside the lab. Two problems follow: (1) the host's services - file sharing, remote desktop - would be reachable and attackable from lab machines; (2) the host's own traffic would appear in lab captures and pollute the data.
- **Static IPs instead of DHCP:** Addresses never change, so attack commands, detection rules and ground-truth records that reference an IP stay valid for the whole project. DHCP is disabled because nothing on this network needs it.
- **Install on NAT, then isolate:** Machines are connected to NAT only to install the OS, packages and container images, then moved permanently to VMnet2. Metasploitable2 never touches NAT. Vulnerable applications are downloaded but not started until the machine is isolated. Verification: `ping 8.8.8.8` must fail from every VM.