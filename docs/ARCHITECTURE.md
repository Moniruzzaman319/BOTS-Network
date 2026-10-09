# Architecture

## Logical Design

The BOTS Network lab is organized into multiple functional areas:

- **Edge/Security:** FortiGate firewall connected toward the VMware/external network.
- **Core:** Core_RTR provides the primary routed path and Backup_RTR provides redundancy.
- **Distribution:** DIST_NX aggregates major network sections.
- **Corporate:** Corp_RTR with CL_1 and CL_2 provides routed and VLAN-based corporate access.
- **Server/DMZ:** SERVER and DMZ_RTR connect centralized infrastructure services.
- **BOTS:** BOTS_RTR provides a dedicated BOTS subnet.
- **Subscriber Access:** MIK_PPPoE provides PPPoE service for home/subscriber users.
- **Monitoring:** Zabbix on INFRA-SRV provides centralized monitoring.

## Important Addressing

| Function | Address / Network |
|---|---|
| INFRA-SRV | 10.30.10.10/24 |
| BOTS LAN gateway | 10.40.10.1/24 |
| BOTS LAN | 10.40.10.0/24 |
| BOTS_RTR ↔ SERVER | 10.255.14.0/30 |
| Core_RTR ↔ FortiGate | 10.255.1.0/30 |
| FortiGate core-facing IP | 10.255.1.2/30 |
| Core_RTR firewall-facing IP | 10.255.1.1/30 |

## Dynamic Routing

OSPF is used for internal dynamic routing. The redundant core design allows the routing domain to reconverge toward Backup_RTR when the primary path is unavailable.

## Central Services

INFRA-SRV provides DNS, DHCP, NTP, Syslog and Zabbix services. Zabbix monitors network devices over SNMPv2 and monitors the Linux server using the Zabbix Agent.
