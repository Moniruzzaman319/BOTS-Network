# Demonstration Guide

A concise live demonstration sequence for the BOTS Network project.

1. Open the complete EVE-NG topology and explain the major network sections.
2. On Core_RTR, show `show ip ospf neighbor` and `show ip route`.
3. On CL_2, show `show vlan brief` and `show interfaces trunk`.
4. Demonstrate end-to-end reachability to INFRA-SRV at `10.30.10.10`.
5. Demonstrate internal DNS with `nslookup infra.bots.test 10.30.10.10`.
6. Open the Zabbix dashboard and show monitored routers and INFRA-SRV.
7. On MikroTik, show the PPPoE server, pool, profiles and active sessions.
8. On FortiGate, show interface addresses, routing table and firewall policies.
9. Finish with the core-path failure test and demonstrate OSPF reconvergence through Backup_RTR.

## Safety

Do not expose passwords, VPN pre-shared keys, private keys, real credentials, or licensed network operating-system images during the demonstration or in this repository.
