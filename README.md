# Spanning Tree Protocol (STP) Practical Lab

## Project Overview

This project demonstrates the implementation and analysis of Spanning Tree Protocol (STP) using Cisco Packet Tracer.

The network consists of three Cisco Catalyst 3560 multilayer switches connected in a redundant triangle topology. Two VLANs are configured to separate Sales and HR departments.

STP is used to prevent Layer 2 switching loops while maintaining redundant physical connections. The lab also explores Root Bridge election, port roles, link failure recovery, and network troubleshooting.

## Learning Objectives

- Understand the purpose of Spanning Tree Protocol.
- Prevent Layer 2 switching loops in a redundant network.
- Configure VLANs for departmental segmentation.
- Configure IEEE 802.1Q trunk links.
- Identify Root Bridges, Root Ports, Designated Ports and Alternate Ports.
- Manually configure STP Root Bridge priorities.
- Investigate STP behavior during link failures.
- Verify network connectivity and troubleshoot configuration issues.

## Network Topology

The network includes:

- 3 Cisco Catalyst 3560 multilayer switches
- 5 PCs
- Redundant triangle topology between switches
- VLAN 10 for Sales
- VLAN 20 for HR

## VLAN and IP Addressing Plan

| Department | VLAN | Device | IP Address |
|---|---:|---|---|
| Sales | 10 | PC0 | 192.168.10.10 |
| Sales | 10 | PC3 | 192.168.10.11 |
| Sales | 10 | PC1 | 192.168.10.12 |
| HR | 20 | PC4 | 192.168.20.10 |
| HR | 20 | PC2 | 192.168.20.11 |

Subnet mask for all PCs: `255.255.255.0`

## Implementation Tasks

1. Build a redundant triangle topology using three multilayer switches.
2. Create VLAN 10 (SALES) and VLAN 20 (HR) on all switches.
3. Assign end-device ports to the correct VLANs.
4. Configure trunk links between switches and allow VLANs 10 and 20.
5. Configure IP addresses on all PCs.
6. Investigate the default STP topology for VLANs 10 and 20.
7. Configure Switch0 as the preferred Root Bridge.
8. Configure different STP priorities and observe Root Bridge election.
9. Identify redundant links and STP blocking ports.
10. Disconnect an active link and investigate STP reconvergence.
11. Troubleshoot VLAN assignment and trunk configuration issues.

## STP Configuration Commands

View spanning-tree information:

```bash
show spanning-tree
show spanning-tree vlan 10
show spanning-tree vlan 20
```

Configure Switch0 as the preferred Root Bridge:

```bash
spanning-tree vlan 10 root primary
spanning-tree vlan 20 root primary
```

Configure manual priorities:

```bash
spanning-tree vlan 10 priority 4096
spanning-tree vlan 20 priority 4096
```

Configure Switch1 priority for VLAN 10:

```bash
spanning-tree vlan 10 priority 8192
```

## Verification Commands

```bash
show vlan brief
show interfaces trunk
show spanning-tree
show spanning-tree vlan 10
show spanning-tree vlan 20
show running-config
```

## Connectivity Testing

| Test | Expected Result |
|---|---|
| PC0 to PC3 | Successful |
| PC2 to PC4 | Successful |
| PC0 to PC2 | Unsuccessful |

Same-VLAN devices should communicate through the switched network. Communication between VLANs should fail because this lab does not configure Inter-VLAN routing.

## Key Learning Outcomes

- Understand how STP prevents Layer 2 switching loops.
- Identify the Root Bridge and understand Bridge ID election.
- Understand Root Port, Designated Port and Alternate Port roles.
- Learn how bridge priorities influence Root Bridge election.
- Understand how redundant links improve network availability.
- Observe STP topology changes when an active link fails.
- Develop Layer 2 troubleshooting skills.

## Technologies and Tools

- Cisco Packet Tracer
- Cisco Catalyst 3560 Switches
- Spanning Tree Protocol (STP)
- IEEE 802.1D
- Per-VLAN Spanning Tree (PVST+)
- VLAN Configuration
- IEEE 802.1Q Trunking
- IPv4 Addressing
- ICMP Ping Testing
