# University Network Design with Multiple Subnets

## Project Overview

This project involves the design and implementation of a comprehensive university network spanning five campuses. The network is built using Cisco Packet Tracer, incorporating multiple subnets, dynamic routing (OSPF), DHCP services, DNS resolution, and web hosting capabilities. The entire infrastructure is configured to ensure seamless connectivity across all campuses, with automatic IP assignment and centralized service management.

## Features

- **Multi-Campus Network**: Five campuses interconnected with routers following a specified topology
- **Dynamic Routing**: OSPF (Open Shortest Path First) protocol implemented for efficient routing
- **Centralized Services**: Single DHCP server for automatic IP assignment across all campuses
- **DNS Resolution**: Central DNS server for accessing the university website
- **Web Server**: Hosts the university website accessible via `http://www.apex.edu.bd`
- **Mixed Connectivity**: Both wired and wireless hosts in each campus network
- **Scalable Architecture**: Designed for future expansion and growth

## Network Topology

The network consists of 8 routers (Campus 1-8) with the following IP address allocations:

### Class A Networks
| Campus | Network Address | Gateway |
|--------|-----------------|---------|
| Campus 1 | 115.0.0.0/8 | 115.0.0.254 |
| Campus 2 | 116.0.0.0/8 | 116.0.0.254 |
| Campus 8 | 117.0.0.0/8 | 117.0.0.254 |

### Class B Networks
| Campus | Network Address | Gateway |
|--------|-----------------|---------|
| Campus 6 | 156.45.0.0/16 | 156.45.0.254 |
| Campus 7 | 156.32.0.0/16 | 156.32.0.254 |

### Class C Networks
| Campus | Network Address | Gateway |
|--------|-----------------|---------|
| Campus 3 | 192.168.10.0/24 | 192.168.10.254 |
| Campus 4 | 192.168.20.0/24 | 192.168.20.254 |
| Campus 5 | 192.168.15.0/24 | 192.168.15.254 |

## Router Configuration

### Basic Router Setup

Each router is configured with interface IP addresses and serial connections between routers. The inter-router networks use the 192.166.x.x address space.

#### Example Configuration (Campus 1):
interface fa0/0
ip address 115.0.0.254 255.0.0.0
no shut
do wr
exit

interface se3/0
ip address 192.166.20.2 255.255.255.0
no shut
do wr
exit

interface se2/0
ip address 192.166.30.1 255.255.255.0
clock rate 64000
no shut
do wr
exit

text

### OSPF Configuration

OSPF dynamic routing is configured on all routers to ensure proper routing between campuses.

#### Example OSPF Configuration (Campus 1):
router ospf 1
network 115.0.0.0 0.255.255.255 area 1
network 192.166.20.0 0.0.0.255 area 1
network 192.166.30.0 0.0.0.255 area 1
exit

text

### DHCP Helper Configuration

To enable DHCP services across all campuses from the central DHCP server (located at 192.168.15.25), IP helper addresses are configured on each router's interface:
interface fa0/0
ip helper-address 192.168.15.25
exit

text

## Services

### DHCP Server
- **Location**: Campus 5 (192.168.15.25)
- **Function**: Automatically assigns IP addresses to all hosts across all campuses
- **Scope**: All five campuses with appropriate IP ranges for each network

### DNS Server
- **Location**: Campus 5
- **Function**: Resolves `www.apex.edu.bd` to the web server's IP address
- **Records**: A record for the university website

### Web Server
- **Location**: Campus 5
- **Function**: Hosts the university's official website
- **Access URL**: `http://www.apex.edu.bd`

## Hardware Components Used

- **Routers**: Generic Router-PT (8 units)
- **Switches**: 2960 IOS 15 (Multiple units)
- **End Devices**: PC-PT, Laptop-PT, Smartphone-PT
- **Wireless**: AccessPoint-PT
- **Servers**: DNS Server, DHCP Server, Web Server
- **Connectors**: Copper Straight-Through, Serial DCE

## Technical Specifications

- **Software**: Cisco Packet Tracer 8.2.2
- **Routing Protocol**: OSPF (Open Shortest Path First)
- **IP Addressing**: Mixed Class A, B, and C networks
- **Inter-Router Connections**: Serial DCE connections with clock rate 64000
- **Network Services**: DHCP, DNS, HTTP/HTTPS

## Connectivity Verification

All hosts across all campuses can:
- Communicate with each other regardless of campus location
- Automatically obtain IP addresses from the central DHCP server
- Access the university website via `http://www.apex.edu.bd`
- Reach any network segment through OSPF routing

## Future Expansion

The network architecture supports:
- Addition of new campuses
- Integration of additional subnets
- Scalability of existing networks
- Deployment of additional services

## Conclusion

This university network design successfully implements a robust, scalable infrastructure connecting five campuses with centralized services. The use of OSPF ensures efficient routing, while the central DHCP server simplifies network management. Mixed wired and wireless connectivity provides flexibility for users, and the DNS/web servers enable easy access to university resources. The design meets all specified requirements while maintaining the flexibility for future growth and expansion.

## Author

**Chinmoy Karmakar**  
ID: 2022-1-60-381  
Department of Computer Science and Engineering  

**Instructor**: Dr. Anisur Rahman  
Associate Professor, Department of Computer Science and Engineering  

**Date**: 02 February 2025

---

## Project Files

- `Project Report.pdf` - Complete project documentation
- `SmartSubnet_Network.png` - Network topology diagram
- Cisco Packet Tracer configuration files (if applicable)

## License

This project was created for academic purposes as part of the Computer Networks course (CSE405).
