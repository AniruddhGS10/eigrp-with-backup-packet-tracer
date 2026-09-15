# EIGRP with Backup Path

## Overview

This project is a Cisco Packet Tracer lab demonstrating EIGRP routing with two different EIGRP autonomous systems and route redistribution.

The topology consists of three routers connected in a triangular design. EIGRP AS 1 and EIGRP AS 13 are used on different parts of the network, and routes are redistributed between the two EIGRP processes to provide connectivity and an alternate routing path.

## Network Topology

R1 ---------------- R2
 \                  /
  \                /
   ------ R3 ------

R1 and R2 primarily use EIGRP AS 1.

R1 and R3 use EIGRP AS 13.

Route redistribution is configured between EIGRP AS 1 and EIGRP AS 13 to exchange routes between the two routing domains.

## Routing Configuration

### R1

R1 participates in both EIGRP AS 1 and EIGRP AS 13.

EIGRP AS 1:

router eigrp 1
network 10.10.12.0 255.255.255.0
network 10.10.1.0 255.255.255.0

EIGRP AS 13:

router eigrp 13
network 10.10.13.0 255.255.255.0
network 10.10.1.0 255.255.255.0
redistribute eigrp 1

The EIGRP processes are used to exchange routes through redistribution.

### R2

R2 participates in EIGRP AS 1 and EIGRP AS 23.

EIGRP AS 1:

router eigrp 1
network 10.10.12.0 255.255.255.0
network 10.10.2.0 255.255.255.0

EIGRP AS 23:

router eigrp 23
network 10.10.23.0 255.255.255.0
network 10.10.2.0 255.255.255.0
redistribute eigrp 1

### R3

R3 participates in EIGRP AS 13 and EIGRP AS 23.

EIGRP AS 13:

router eigrp 13
network 10.10.13.0 255.255.255.0
network 1.1.1.1 255.255.255.255
network 2.2.2.2 255.255.255.255
network 3.3.3.3 255.255.255.255

EIGRP AS 23:

router eigrp 23
network 10.10.23.0 255.255.255.0
network 1.1.1.1 255.255.255.255
network 2.2.2.2 255.255.255.255
network 3.3.3.3 255.255.255.255

## Route Redistribution

Route redistribution is used to exchange routes between different EIGRP autonomous systems.

The lab demonstrates redistribution between:

- EIGRP AS 1
- EIGRP AS 13
- EIGRP AS 23

This allows routers running different EIGRP processes to learn routes from each other.

## Backup Path

The triangular topology provides an alternate path between the routers.

If the primary path becomes unavailable, the alternate path through the third router can be used to maintain connectivity, depending on the routing information and metrics available.

## Verification

The following commands can be used to verify the configuration:

show ip route
show ip eigrp neighbors
show ip protocols
show ip eigrp topology
show ip interface brief
ping
traceroute

These commands help verify EIGRP neighbors, learned routes, routing paths, and connectivity.

## What I Learned

This project helped me understand how EIGRP operates when multiple autonomous systems are used within the same topology.

I also practiced route redistribution between EIGRP processes and learned how an alternate path can provide redundancy when the primary routing path is unavailable.

## Tools Used

- Cisco Packet Tracer
- Cisco IOS
- EIGRP
- Route Redistribution
- IPv4
- Routing Redundancy
- EIGRP Autonomous Systems
