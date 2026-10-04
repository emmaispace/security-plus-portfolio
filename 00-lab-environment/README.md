# Security+ Lab Environment

## Purpose

This directory documents the isolated virtual cybersecurity
laboratory created for my CompTIA Security+ SY0-701 preparation.

The lab provides a controlled environment for:

- Security+ practical exercises
- Network security testing
- Vulnerability assessment
- Security monitoring
- SIEM exercises
- Incident response
- Detection engineering
- Security architecture
- Governance and risk exercises

## Virtualization

- VMware Workstation Pro
- Windows host
- Isolated virtual networks
- pfSense firewall

## Network Segmentation

| Network | Subnet | Purpose |
|---|---|---|
| LAB-LAN | 192.168.10.0/24 | Internal systems |
| LAB-DMZ | 192.168.20.0/24 | Web server |
| LAB-SOC | 192.168.40.0/24 | Security monitoring |
| LAB-ATTACK | 192.168.50.0/24 | Security testing |

## Systems

| Host | Role | Network |
|---|---|---|
| SEC-PFSENSE | Firewall/router | All networks |
| DC01 | Domain Controller/DNS | LAN |
| WIN01 | Windows client | LAN |
| FS01 | File server | LAN |
| WEB01 | IIS web server | DMZ |
| WAZUH01 | SIEM/security monitoring | SOC |
| KALI01 | Security testing | ATTACK |

## Security Principle

The environment is designed to remain isolated from
the physical/home network.

All offensive-security testing is performed only against
systems intentionally created for this laboratory.

## Week 0 Status

Lab environment established and operational.
