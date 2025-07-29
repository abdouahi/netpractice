# NetPractice

**Version:** 3.4  
**Summary:** Learn the fundamentals of networking by configuring and troubleshooting simulated networks through a web-based interface.

---

## Table of Contents

- [Introduction](#introduction)
- [What is Computer Networking?](#what-is-computer-networking)
- [Key Networking Concepts (Deep Dive)](#key-networking-concepts-deep-dive)
  - [1. IP Addressing (IPv4, IPv6, Static, Dynamic)](#1-ip-addressing-ipv4-ipv6-static-dynamic)
  - [2. Subnet Masks & Subnetting](#2-subnet-masks--subnetting)
  - [3. Routers & Routing](#3-routers--routing)
  - [4. The Default Gateway](#4-the-default-gateway)
  - [5. TCP/IP Protocol Suite (with Common Protocols)](#5-tcpip-protocol-suite-with-common-protocols)
  - [6. IPv4 vs. IPv6](#6-ipv4-vs-ipv6)
  - [7. Network Devices](#7-network-devices)
  - [8. Communication Models: OSI vs. TCP/IP](#8-communication-models-osi-vs-tcpip)
  - [9. Common Network Problems](#9-common-network-problems)
- [Project Structure](#project-structure)
- [How to Use NetPractice](#how-to-use-netpractice)
- [Tips for Success](#tips-for-success)
- [FAQ](#faq)
- [License](#license)

---

## Introduction

NetPractice is a practical project designed to help you deeply understand computer networking. The project uses a browser-based simulator to present you with various broken network scenarios. Your task is to fix them by correctly configuring devices, addressing, and routing.

The following explanations cover every fundamental topic you'll need—not just to complete this project, but to truly understand computer networking. Master these, and you'll be equipped for top marks and real-world networking situations.

---

## What is Computer Networking?

A **computer network** is a collection of computers and devices connected together to share information and resources. These connections can be physical (cables) or wireless (Wi-Fi). The Internet is the largest network, connecting millions of private, public, and business networks.

---

## Key Networking Concepts (Deep Dive)

### 1. IP Addressing (IPv4, IPv6, Static, Dynamic)

#### What is an IP Address?

- An **IP (Internet Protocol) address** is a unique identifier for a device on a network, needed to send/receive data.

#### IPv4

- Format: Four decimal numbers (0–255) separated by dots, e.g., `192.168.1.1`
- 32 bits in size, ~4.3 billion unique addresses

#### IPv6

- Format: Eight groups of four hexadecimal digits, e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- 128 bits, virtually unlimited addresses

#### Static vs. Dynamic IP Assignment

- **Static IP:** Manually set, persistent (never changes unless you change it).
- **Dynamic IP:** Assigned automatically by **DHCP (Dynamic Host Configuration Protocol)** server; can change over time.

#### Special IPv4 Address Classes and Ranges

| Class   | Range                          | Purpose/Notes                                        |
|---------|--------------------------------|------------------------------------------------------|
| A       | 1.0.0.0 – 126.255.255.255      | Large networks                                       |
| B       | 128.0.0.0 – 191.255.255.255    | Medium networks                                      |
| C       | 192.0.0.0 – 223.255.255.255    | Small networks                                       |
| D       | 224.0.0.0 – 239.255.255.255    | Multicast                                            |
| E       | 240.0.0.0 – 255.255.255.254    | Reserved for research (not for general use)          |
| **Loopback** | **127.0.0.0/8**               | Localhost testing, e.g., `127.0.0.1` – `127.255.255.254` |
| **Broadcast** | Last address in subnet         | E.g. `192.168.1.255` in `192.168.1.0/24`             |
| **Network Address** | First address in subnet    | Identifies the subnet, e.g., `192.168.1.0`           |

---

### 2. Subnet Masks & Subnetting

#### What is a Subnet Mask?

- A **subnet mask** splits an IP address into its "network" and "host" parts.
- Example:  
  - IP: `192.168.1.15`, Mask: `255.255.255.0`
  - `192.168.1` is the network part, `.15` is the host part.

#### Subnet Mask Function

- A **mask** uses binary: `255` = network bit, `0` = host bit.
- **CIDR Notation**: `/24` means 24 bits are network (e.g., `255.255.255.0`)
- **Hosts per subnet** = 2^(host bits) − 2 (for network & broadcast addresses)

#### Why Subnet?

- Breaks a large network into smaller, manageable, more secure, and efficient pieces.
- Reduces broadcast traffic; easier troubleshooting.

#### Example Table

| CIDR   | Dotted Decimal      | Hosts per Subnet |
|--------|---------------------|------------------|
| /8     | 255.0.0.0           | 16,777,214       |
| /16    | 255.255.0.0         | 65,534           |
| /24    | 255.255.255.0       | 254              |
| /30    | 255.255.255.252     | 2                |

---

### 3. Routers & Routing

#### What is a Router?

- Connects different networks (subnets) and forwards packets between them.
- Each router interface is in a different network.

#### Routing Tables

- Routers use **routing tables** to decide where to send packets.
- **Static Routes:** Manually configured.
- **Dynamic Routes:** Added via routing protocols (RIP, OSPF, BGP, etc).

#### Calculating Routes

- **Default Route**: `0.0.0.0/0` (the "catch-all" for unknown destinations; usually points to the Internet gateway)
- If PC A (`192.168.1.10`) needs to talk to PC B (`10.0.0.5`), routers must have routes to both networks.

---

### 4. The Default Gateway

- The **default gateway** is the router IP that your device sends traffic to for addresses outside its own subnet.
- Must be on the same subnet as the host.
- Without a correct gateway, you can’t reach external networks (e.g. the Internet).

---

### 5. TCP/IP Protocol Suite (with Common Protocols)

#### What is TCP/IP?

- The foundational suite of protocols for networking (used everywhere).
- Main protocols:
  - **TCP (Transmission Control Protocol):** Reliable, ordered delivery; used for web, email, file transfer.
  - **IP (Internet Protocol):** Handles addressing and routing packets.
  - **UDP (User Datagram Protocol):** Fast, unreliable; used for streaming, gaming.
  - **ARP (Address Resolution Protocol):** Maps IPv4 addresses to MAC (hardware) addresses on a LAN.
  - **ICMP (Internet Control Message Protocol):** Used for diagnostics & error reporting (e.g., `ping`, `traceroute`).

---

### 6. IPv4 vs. IPv6

| Feature         | IPv4                         | IPv6                                   |
|-----------------|-----------------------------|----------------------------------------|
| Length          | 32 bits                      | 128 bits                               |
| Format          | 192.168.1.1                  | 2001:0db8:85a3:0000:0000:8a2e:0370:7334|
| Address count   | ~4.3 billion                 | 3.4×10^38                              |
| NAT needed?     | Often                        | Rarely                                 |
| Address exhaustion | Yes                       | No                                     |

**Tip:** NetPractice focuses on IPv4, but understanding both is valuable.

---

### 7. Network Devices

- **Host/Workstation:** Any device with an IP (PC, server, printer)
- **Switch:** Connects devices within the same network (Layer 2)
- **Router:** Connects different networks/subnets (Layer 3)
- **Firewall:** Filters traffic for security
- **Access Point:** Wireless bridge to a wired network
- **DHCP Server:** Assigns dynamic IPs

---

### 8. Communication Models: OSI vs. TCP/IP

The **OSI Model** is a conceptual framework for understanding networking, but not all layers map directly to real protocols. The **TCP/IP Model** is what’s actually used.

| OSI Layer     | Function                                  | TCP/IP Equivalent          |
|---------------|-------------------------------------------|---------------------------|
| Application   | User-facing services (web, email, FTP, etc.) | Application               |
| Presentation  | Data formatting, encryption (rarely separate) | Application               |
| Session       | Dialog management (rarely separate)       | Application (often)       |
| Transport     | Host-to-host communication (conceptual; TCP/UDP) | Transport (TCP/UDP)   |
| Network       | IP addressing, routing                    | Internet                  |
| Data Link     | MAC addresses, switches                   | Network Interface         |
| Physical      | Cables, signals                           | Network Interface         |

**Notes:**
- TCP/UDP protocols live in the TCP/IP Transport layer, and are not defined by the OSI standard.
- Session/Presentation layers are rarely mapped to discrete protocols; their functions are often built into Application layer protocols.

---

### 9. Common Network Problems

- **IP Address Conflict:** Two devices with the same IP
- **Incorrect Subnet Mask:** Devices can’t see each other
- **Wrong Default Gateway:** Can’t reach outside networks
- **Routing Table Errors:** Routers can’t forward packets correctly
- **Missing/Incorrect Routes:** Data gets lost or can’t leave the network
- **Physical Issues:** Unplugged cables, dead hardware

---

## Project Structure

- `level1.txt`  
- `level2.txt`  
- ...  
- `level10.txt`  
Exported from the simulator after solving each level.

---

## How to Use NetPractice

1. **Download and Extract** the simulator package.
2. **Open `index.html`** in your browser.
3. **Enter Your Login** (mandatory for grading).
4. **Solve Each Level:** Assign correct IPs, masks, gateways, and routes. Test with [Check again]. Export with [Get my config].
5. **Place all config files at the root of your repo** before submission.

---

## Tips for Success

- **Master IPv4 addressing and subnetting.**
- **Double-check subnet masks and gateways.**
- **When devices can’t communicate, check:**
  - Are they in the same subnet?
  - Is routing configured correctly?
  - Are the gateways correct?
  - Any IP conflicts?
- **Work step-by-step:** Fix one device/route at a time. Use logs for troubleshooting.
- **Practice subnet calculations by hand:** You’ll need speed in real exams.

---

## FAQ

**Q: What if I use the wrong mask?**  
A: Devices may think they're not in the same network and won’t communicate.

**Q: How do I pick the right gateway?**  
A: The gateway must be an IP address on the same subnet as the device.

**Q: What does [Get my config] do?**  
A: It exports your current configuration for grading.

**Q: Can I use online calculators?**  
A: For practice, yes. During evaluation, only a basic calculator is allowed.

---

## License

Distributed for educational purposes only.  
Project template and interface © [Your School/Organization].  
All rights reserved.

---
