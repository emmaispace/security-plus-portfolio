# 🏗️ Home Lab Environment

> **Objective:** An isolated virtual network for safe, legal security practice.
> Victim VMs have no route to the internet; only the attacker/analysis VM gets
> a temporary NAT adapter when downloads are needed.

## Topology

![Lab network diagram](network-diagram.png)
<!-- Draw yours free at https://diagrams.net — export as PNG into this folder -->

| VM | Role | OS | RAM | Network |
| --- | --- | --- | --- | --- |
| Kali | Attacker / analysis | Kali Linux | 4 GB | Host-only `192.168.56.0/24` (+temp NAT) |
| Metasploitable 2 | Intentionally vulnerable target | Ubuntu 8.04 | 1 GB | Host-only only — **no internet, ever** |
| Ubuntu Server | SIEM / services / hardening target | Ubuntu 24.04 LTS | 2 GB | Host-only + internal `dmz` |
| Windows 11 Eval | Endpoint / GPO / hardening target | Windows 11 Ent. Eval | 4 GB | Host-only + internal `lan` |
| pfSense | Zone firewall/router (Project 3) | pfSense CE | 1 GB | WAN host-only, DMZ `10.10.10.0/24`, LAN `10.20.20.0/24` |

## Why host-only isolation matters

Metasploitable 2 ships with real, weaponizable vulnerabilities (e.g. the vsftpd
2.3.4 backdoor). Exposing it to any network I don't fully control would be
negligent. Host-only networking lets VMs talk to each other and my host, but
gives them **no default route to the internet** — segmentation as a first principle.

## Verification

```bash
# From Kali — reach the target:
$ ping -c 3 192.168.56.102     # ✅ 3 replies
# From Metasploitable — confirm isolation:
$ ping -c 3 8.8.8.8            # ✅ 100% packet loss = properly isolated
```

## Snapshots

Every VM carries a `clean-install` snapshot taken before any lab work —
my universal undo button after destructive exercises.

**Full build walkthrough:** [setup-guide.md](setup-guide.md) *(mirror of Lab Manual — Tutorial 0)*****
