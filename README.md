# enterprise-wan-multi-site-routing

# Multi-Site Enterprise WAN Infrastructure & ISP Core Routing 

Project Overview
This repository features the design and deployment of a multi-site Enterprise Wide Area Network (WAN) simulated in Cisco Packet Tracer. The project connects a main corporate Headquarters (HQ) to a remote Branch Office across a simulated Internet Service Provider (ISP) network using point-to-point Serial links and static multi-hop routing paths.

WAN Architecture & Topology Map
The design models a professional, distributed enterprise topology separating corporate office sites from public carrier spaces.

 Network Segment Breakdown:
Headquarters (HQ Network - Left): Powered by a Cisco 2901 edge router supporting standard local VLANs, local wireless access points, network printer hubs, and finance departments.
Simulated ISP Cloud (Core Network - Center): A central Cisco 2911 ISR router acting as the provider core, linking corporate sites using dedicated Serial interfaces (`Serial0/3/0` and `Serial0/3/1`).
Remote Branch Office (Branch Network - Right): A secondary Cisco 2901 router handling user computing workloads, local access points, and remote infrastructure.
Point-to-Point WAN Links: Bound within the `10.0.0.0/30` prefix domain to ensure optimal allocation of public transit spaces.
Core Engineering Implementations

1. End-to-End Enterprise Routing Engine
Configured static multi-hop routing tables across all routing units to allow clean inter-site traffic paths:
ISP Core Routing: Configured the ISP router to map the paths between internal networks by pointing traffic across transit interfaces (`via 10.0.0.1` and `via 10.0.0.6`).
Corporate Next-Hop Resolution: Injected target traffic lines to direct data packets out local Serial links straight into the provider edge gateway.

2. Localized Addressing Architecture (DHCP Scopes)
Configured edge gateways at each site to automatically assign IP configurations to user machines without overlap:
HQ Scope: Running an active `LAN1` address pool managing the `192.168.1.0/24` subnet landscape.
Branch Office Scope: Operating `BRANCH` and `BRANCH_POOL30` pools serving the `192.168.10.0/24` and `192.168.3.0/24` subnet boundaries.
3. Real-World Logging & DHCP Conflict Troubleshooting
This project captures active network troubleshooting events. During deployment, the router identified and logged a DHCP Address Conflict Alert:

%DHCPD-4-PING_CONFLICT: DHCP address conflict: server pinged 192.168.3.1


Root Cause Analysis: Before leasing an address, the Cisco IOS router ran a protective ICMP background check and received an active response on `192.168.3.1`, identifying that the address was already in use by another node.
Remediation Action: The router safely quarantined the conflicted address and dynamically selected an available host address to prevent a local IP address conflict.
Hardware & Platforms Used
Simulation Engine: Cisco Packet Tracer
Hardware Profile: Cisco 2911 Core Routers, Cisco 2901 Edge Routers, Cisco 2960 Switch Series
Technologies: WAN Serial Communications, Static Network Routing, Multi-Pool DHCP Provisioning, Cisco IOS Event Log Diagnostics
<img width="458" height="592" alt="routt" src="https://github.com/user-attachments/assets/4fafb856-7b7d-44cd-b477-5a476227ccda" />
<img width="733" height="568" alt="routr" src="https://github.com/user-attachments/assets/6f4927f0-9f3d-4d14-b879-887a6f9f524b" />
<img width="597" height="415" alt="router" src="https://github.com/user-attachments/assets/250c4d5d-95d8-487e-bbb1-3ca6408dec82" />
<img width="566" height="503" alt="rout" src="https://github.com/user-attachments/assets/7a5a8a1a-8b70-489e-bc01-764b8c3e15fc" />
<img width="645" height="420" alt="rot1" src="https://github.com/user-attachments/assets/3eafed5e-a673-4004-8df0-9225f80233d4" />
<img width="565" height="540" alt="r4" src="https://github.com/user-attachments/assets/4006efab-02db-4294-a5d0-d171ea685a5f" />
<img width="648" height="561" alt="r3" src="https://github.com/user-attachments/assets/029bf4c6-07f9-4f7f-8d09-bcc434dc0bcd" />
<img width="606" height="543" alt="R2" src="https://github.com/user-attachments/assets/4c79b7d6-cce5-479d-8238-7be20db6ee9c" />
<img width="1018" height="529" alt="branch router" src="https://github.com/user-attachments/assets/1f593900-3a6e-48df-8879-87a73ce9bbce" />
<img width="1321" height="438" alt="Capture" src="https://github.com/user-attachments/assets/2d70b14d-3f43-4926-a02c-862eadc8b949" />
