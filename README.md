# Enterprise Network Design Using OSPF and Extended ACLs

## Project Overview

This project involves designing and simulating a three-router enterprise network using Cisco Packet Tracer.

The network uses Open Shortest Path First (OSPF) for dynamic routing, DHCP for automatic IP address allocation, and Extended Access Control Lists (ACLs) to enforce communication restrictions between departments.

The objective was to build a network that supports dynamic routing, redundancy, inter-network communication and departmental isolation.

## Network Topology

The network consists of:

- 3 Cisco 2911 routers
- 3 Cisco 2960 switches
- 6 client PCs
- 1 server
- Router-to-router connections forming a triangular topology

## IP Addressing

### LAN Networks

| Network | Subnet | Default Gateway |
|---|---|---|
| LAN 1 | 192.168.1.0/24 | 192.168.1.1 |
| LAN 2 | 192.168.2.0/24 | 192.168.2.1 |
| LAN 3 (IT) | 192.168.3.0/24 | 192.168.3.1 |

### Router-to-Router Networks

| Link | Network |
|---|---|
| Router link 1 | 10.0.10.0/30 |
| Router link 2 | 10.0.11.0/30 |
| Router link 3 | 10.0.12.0/30 |

## Technologies and Concepts

- Cisco Packet Tracer
- IPv4 addressing and subnetting
- DHCP configuration
- Dynamic routing with OSPF Area 0
- OSPF neighbour formation
- Routing table verification
- Equal-cost multipath routing
- Network redundancy and failover
- Extended Access Control Lists
- ICMP and TCP traffic filtering

## Routing Implementation

OSPF was configured on all three routers to exchange routing information dynamically.

The triangular topology provides alternative paths between routers.

Failover was tested by shutting down a router-to-router interface and verifying that communication could continue through an alternative path.

## Access Control and Network Security

Extended ACLs were configured to implement the following departmental access policy:

| Source Network | LAN 1 | LAN 2 | LAN 3 (IT) |
|---|---|---|---|
| LAN 1 | Allowed | Denied | Denied |
| LAN 2 | Denied | Allowed | Denied |
| LAN 3 (IT) | Allowed | Allowed | Allowed |

Additional ACL rules were configured to permit ICMP echo replies and TCP return traffic for connections initiated by IT.

The TCP `established` keyword was used to match TCP packets with ACK or RST flags. This is not full stateful firewall inspection.

## Testing and Verification

The following tests were performed:

- Verified OSPF neighbour relationships.
- Checked dynamically learned routes.
- Tested communication between different LANs.
- Tested alternative routing after shutting down a router link.
- Verified DHCP address allocation.
- Tested communication restrictions between departments.
- Verified that IT could initiate ICMP and TCP communication with other departments.
- Tested HTTP connectivity using a server.

## Key Learning Outcomes

Through this project, I gained practical experience in:

1. Designing multi-router network topologies.
2. Configuring and troubleshooting OSPF.
3. Understanding dynamic route selection and failover.
4. Configuring DHCP on Cisco routers.
5. Implementing network segmentation and access restrictions.
6. Understanding how ACL direction, sequence and implicit deny affect traffic.
7. Troubleshooting network connectivity using Cisco IOS commands.

## Tools

- Cisco Packet Tracer

## Project Status

Completed — additional documentation and testing may be added.