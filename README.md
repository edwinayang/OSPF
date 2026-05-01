OSPF Multi-Router Network (Project 4)

## Overview
This project simulates a 4-router OSPF network using a square topology.
It demonstrates dynamic routing, OSPF neighbor formation, and full connectivity.

## Topology
OSPF-neighbor.jpg
ospf-route.jpg
ospf-topo.jpg
successful-ping.jpg

## IP Addressing

R1-R2 = 192.168.10.0/24
R2-R4 = 192.168.20.0/24
R4-R3 = 192.168.30.0/24
R3-R1 = 192.168.40.0/24

## Configuration

### R1
conf t
interface g0/0
ip address 192.168.10.1 255.255.255.0
no shutdown

interface g0/1
ip address 192.168.40.2 255.255.255.0
no shutdown

router ospf 1
network 192.168.10.0 0.0.0.255 area 0
network 192.168.40.0 0.0.0.255 area 0
end

### R2
conf t
interface g0/0
ip address 192.168.10.2 255.255.255.0
no shutdown

interface g0/1
ip address 192.168.20.1 255.255.255.0
no shutdown

router ospf 1
network 192.168.10.0 0.0.0.255 area 0
network 192.168.20.0 0.0.0.255 area 0
end

### R3
conf t
interface g0/0
ip address 192.168.40.1 255.255.255.0
no shutdown

interface g0/1
ip address 192.168.30.2 255.255.255.0
no shutdown

router ospf 1
network 192.168.30.0 0.0.0.255 area 0
network 192.168.40.0 0.0.0.255 area 0
end

### R4
conf t
interface g0/0
ip address 192.168.20.2 255.255.255.0
no shutdown

interface g0/1
ip address 192.168.30.1 255.255.255.0
no shutdown

router ospf 1
network 192.168.20.0 0.0.0.255 area 0
network 192.168.30.0 0.0.0.255 area 0
end

## Verification

show ip ospf neighbor
show ip route ospf
ping 192.168.20.1

## Result

- All routers formed OSPF neighbors
- Routes were dynamically learned
- Full end-to-end connectivity achieved
