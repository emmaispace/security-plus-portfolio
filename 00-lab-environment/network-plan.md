# Network Plan

## pfSense

| Interface | Network | Gateway |
|---|---|---|
| WAN | VMware NAT | DHCP |
| LAN | 192.168.10.0/24 | 192.168.10.1 |
| DMZ | 192.168.20.0/24 | 192.168.20.1 |
| SOC | 192.168.40.0/24 | 192.168.40.1 |
| ATTACK | 192.168.50.0/24 | 192.168.50.1 |

## Infrastructure Addressing

| System | IP |
|---|---|
| DC01 | 192.168.10.9 |
| FS01 | 192.168.10.10 |
| WEB01 | 192.168.20.10 |
| WAZUH01 | 192.168.40.10 |

## DHCP

### LAN

192.168.10.100–192.168.10.200

### ATTACK

192.168.50.100–192.168.50.200

## Security Design

Infrastructure addresses are separated from
dynamic client addressing.

The DMZ, SOC and ATTACK networks are separated
from the internal LAN using pfSense.
