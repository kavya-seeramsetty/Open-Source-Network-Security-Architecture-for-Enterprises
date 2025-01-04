# Secure Networking - A Company Network Project on Open-Source

## Project Overview
This project involves building a robust, enterprise-grade network security infrastructure using open-source tools, including **openSUSE**. The goal was to simulate a secure company network within a virtual environment, focusing on secure traffic flow, remote access, and comprehensive access control. The following tools were leveraged to create the architecture: **GNS3**, **Cumulus Linux**, **openSUSE**, **nftables**, **pfsense**, **WireGuard**, **PacketFence**, and **StrongSwan**.

## Environment Setup

### Tools and Technologies Used:
- **openSUSE**: Deployed as the core OS for some virtual network devices, providing a stable and reliable platform for running security tools, VPN servers, and network access controls.
- **GNS3**: Utilized for simulating a complex network topology, connecting multiple virtual devices such as routers, firewalls, and switches to test configurations and protocols.
- **Cumulus Linux**: Deployed as the core network OS on virtual switches, optimized for modern data centers and providing native support for industry-standard protocols.
- **nftables**: Used to configure advanced firewall rules on Linux hosts, providing packet filtering, NAT, and IP routing capabilities.
- **pfsense**: Implemented for enterprise-grade firewalling, offering stateful packet inspection (SPI), VPN support, load balancing, and high availability.
- **WireGuard**: A lightweight VPN solution used for encrypted site-to-site and remote access connections, ensuring secure communication over untrusted networks.
- **PacketFence**: A network access control (NAC) system used for managing network devices, ensuring compliance with network security policies, and providing 802.1X authentication.
- **StrongSwan**: An IPsec-based VPN solution configured to handle secure communication for remote users, ensuring encryption and integrity of the data.

## Responsibilities

### 1. **Network Lab Design and Deployment**
- Designed a GNS3-based virtual lab simulating an enterprise network with multiple subnets, routing protocols, and access control policies. Integrated virtual routers, firewalls, and switches to create a realistic environment.
- Configured **openSUSE** as the operating system for some of the network infrastructure, handling routing, firewalling, and VPN services.
- Configured **Cumulus Linux** as a virtual Layer 3 switch and as the backbone for routing between multiple network segments.
- Configured **OSPF (Open Shortest Path First)** for dynamic routing and **VLANs** to segment traffic and enforce security boundaries within the network.

### 2. **Firewall Configuration**
- Configured **nftables** on **openSUSE** hosts for advanced packet filtering and NAT:
  - Created rules for packet filtering based on source/destination IPs, ports, and protocols.
  - Implemented **DNAT** and **SNAT** for handling inbound and outbound traffic from the private network to the public internet.
  - Designed network zones (internal, DMZ, public) and defined access controls to restrict traffic flow between zones.
- Deployed a **pfsense** firewall cluster to protect the perimeter network and ensure high availability:
  - Configured **stateful packet inspection** to track and allow only valid connection states.
  - Set up **VPN passthrough** for secure remote access and encrypted communication.

### 3. **VPN Integration for Secure Remote Access**
- Integrated **WireGuard** for creating encrypted tunnels for remote access:
  - Configured **WireGuard** peers and interfaces on routers to provide secure site-to-site connections between different office locations.
  - Set up client configurations for remote users to securely access company resources over the internet.
- Implemented **StrongSwan** for IPsec-based VPNs:
  - Configured **IPsec VPN tunnels** between remote users and the corporate network.
  - Used **X.509 certificates** for authentication, ensuring secure and authenticated connections for remote employees.
  - Applied **IKEv2** for key exchange to establish encrypted tunnels and secure data transmission.

### 4. **Network Access Control with PacketFence**
- Implemented **PacketFence** as a NAC solution to enforce security policies across the network:
  - Deployed PacketFence in a **centralized authentication server role** with support for **802.1X**, **RADIUS**, and **MAC authentication** for device access control.
  - Configured **VLAN assignments** based on device status (compliant, non-compliant, quarantined).
  - Implemented **2FA** (Two-Factor Authentication) for SSH access to management VLAN servers, using **Google Authenticator** for enhanced security during administrative sessions.
  - Leveraged **Guest Network Access** with customizable access policies to provide secure internet access to non-corporate devices.

### 5. **Penetration Testing and Vulnerability Resolution**
- Simulated **penetration testing** attacks to evaluate the security posture of the network:
  - Conducted **port scanning** using **nmap** to identify open ports and services.
  - Performed **network sniffing** using **tcpdump** to capture and analyze packets, checking for unencrypted traffic and weak authentication mechanisms.
  - Ran **brute-force attacks** against weakly configured VPNs and SSH services.
  - Identified security gaps such as unpatched software vulnerabilities, misconfigured firewalls, and weak passwords, and promptly resolved them by applying patches, reconfiguring firewall rules, and enforcing stronger authentication mechanisms.
