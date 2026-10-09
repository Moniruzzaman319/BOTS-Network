# BOTS Network — Enterprise Network Infrastructure Lab

An enterprise network simulation built in **EVE-NG** to demonstrate routing, switching, security, centralized infrastructure services, monitoring, subscriber access, and network redundancy.

## Project Overview

The lab models a multi-segment enterprise/ISP-style network with a primary and backup routing path, FortiGate firewalling, Cisco switching and routing, MikroTik PPPoE services, Linux infrastructure services, and Zabbix monitoring.

## Key Features

- Primary **Core_RTR** and **Backup_RTR** design for redundancy
- Dynamic routing using **OSPF**
- VLAN-based network segmentation
- Layer-2 access and distribution switching
- **FortiGate** firewall policies and NAT
- **MikroTik PPPoE** server for subscriber/home-user access
- Dedicated corporate network
- Dedicated server/DMZ network
- Dedicated BOTS network
- Centralized **Zabbix** monitoring
- SNMPv2 monitoring of network devices
- Linux-based DNS, DHCP, NTP and Syslog services
- Core-path failure and routing reconvergence demonstration

## Main Components

| Component | Purpose |
|---|---|
| Core_RTR | Primary core routing |
| Backup_RTR | Redundant routing path |
| DIST_NX | Distribution switching |
| FortiGate | Firewall, policy enforcement and NAT |
| Corp_RTR | Corporate network routing |
| CL_1 / CL_2 | Corporate Layer-2 access switching |
| SERVER | Server-side routing |
| DMZ_RTR | DMZ/server network routing |
| BOTS_RTR | BOTS network routing |
| MIK_PPPoE | MikroTik PPPoE subscriber service |
| INFRA-SRV | Central infrastructure services |
| Zabbix | Centralized network/server monitoring |

## Infrastructure Server

**INFRA-SRV — 10.30.10.10/24**

The Linux infrastructure server provides:

- DNS
- DHCP
- NTP
- Syslog
- Zabbix Server
- Zabbix Agent
- Apache/MariaDB components required by Zabbix

## Monitoring

Zabbix is used as the primary monitoring platform.

Network devices are monitored using **SNMPv2**, while the Linux infrastructure server is monitored using the **Zabbix Agent**. The implementation provides centralized visibility of device availability and operational metrics.

## Routing and High Availability

OSPF is used to exchange routes dynamically between network sections. The topology includes Core_RTR and Backup_RTR so that an alternate routing path can be used when the primary core path fails.

A failure demonstration can be performed by disabling the primary core-to-distribution link and observing OSPF reconvergence toward the backup path.

## Security

FortiGate sits at the network edge and is used for:

- Firewall policy enforcement
- Internal-to-external traffic control
- Source NAT
- Separation of the internal routed infrastructure from the external/VMware network

## PPPoE

The MikroTik router provides PPPoE subscriber services. The configuration includes:

- PPPoE server
- Subscriber address pool
- PPP profiles
- PPP secrets/authentication
- Active PPP session monitoring

## Example Verification Commands

### Cisco IOS

```text
show ip ospf neighbor
show ip route
show vlan brief
show interfaces trunk
```

### FortiGate

```text
get system status
diagnose ip address list
get router info routing-table all
show firewall policy
```

### MikroTik RouterOS

```text
/interface pppoe-server server print detail
/ip pool print detail
/ppp profile print detail
/ppp active print
```

### INFRA-SRV

```bash
systemctl status zabbix-server
systemctl status zabbix-agent
systemctl status apache2
systemctl status mariadb
nslookup infra.bots.test 10.30.10.10
```

## Repository Policy

This repository is intended to contain the EVE-NG lab topology, sanitized configuration examples, documentation, diagrams, and screenshots.

**Network operating-system images, VM images, licenses, private keys, passwords, VPN secrets, and other credentials are intentionally not included.**

## Technologies

EVE-NG · Cisco IOS/IOL · OSPF · VLANs · FortiGate · MikroTik RouterOS · PPPoE · Ubuntu Server · BIND9 · DHCP · NTP · Syslog · Zabbix · SNMP

## Author

**MD. Moniruzzaman**  
Computer Science & Engineering
