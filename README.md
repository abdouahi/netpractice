# NetPractice

**Version:** 3.4  
**Summary:** Learn the fundamentals of networking by configuring and troubleshooting simulated networks through a web-based interface.

---

## Table of Contents

- [Introduction](#introduction)
- [What is Computer Networking?](#what-is-computer-networking)
- [Key Networking Concepts (Deep Dive)](#key-networking-concepts-deep-dive)
  - [1. IP Addressing](#1-ip-addressing)
  - [2. Subnet Masks & Subnetting](#2-subnet-masks--subnetting)
  - [3. Routers & Routing](#3-routers--routing)
  - [4. The Default Gateway](#4-the-default-gateway)
  - [5. TCP/IP Protocol Suite](#5-tcpip-protocol-suite)
  - [6. IPv4 vs. IPv6](#6-ipv4-vs-ipv6)
  - [7. Network Devices](#7-network-devices)
  - [8. Communication Models: OSI & TCP/IP](#8-communication-models-osi--tcpip)
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

**A computer network** is a collection of computers and devices connected together to share information and resources. These connections can be physical (cables) or wireless (Wi-Fi). The Internet is the largest network, connecting millions of private, public, and business networks.

---

## Key Networking Concepts (Deep Dive)

### 1. IP Addressing

#### What is an IP Address?

- An **IP (Internet Protocol) address** is a unique identifier assigned to each device on a network.
- Think of it like a postal address for your computer—without it, data can’t find its destination.

#### Types of IP Addresses

- **IPv4:**  
  - Format: Four decimal numbers (0-255) separated by dots, e.g., `192.168.1.1`
  - 32 bits in size, about 4.3 billion unique addresses

- **IPv6:**  
  - Format: Eight groups of four hexadecimal digits, e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
  - 128 bits, providing a virtually unlimited number of addresses

#### Types of Assignment

- **Static IP:** Manually set and does not change
- **Dynamic IP:** Assigned by a server (DHCP) and can change over time

#### Classes of IPv4 Addresses

- **Class A:** `1.0.0.0` to `126.255.255.255` (large networks)
- **Class B:** `128.0.0.0` to `191.255.255.255` (medium networks)
- **Class C:** `192.0.0.0` to `223.255.255.255` (small networks)
- **Class D & E:** Multicast and reserved

#### Special Addresses

- **Loopback:** `127.0.0.1` (refers to the local machine)
- **Broadcast:** Last address in a subnet, e.g., `192.168.1.255`
- **Network Address:** First address in a subnet, e.g., `192.168.1.0`

---

### 2. Subnet Masks & Subnetting

#### What is a Subnet Mask?

- A **subnet mask** determines which portion of the IP address is the “network” and which part is the “host.”
- Example: In `192.168.1.15` with mask `255.255.255.0`:
  - `192.168.1` = Network part
  - `.15` = Host part

#### How Subnet Masks Work

- **255** in the mask means “network,” and **0** means “host.”
- Expressed in “dotted decimal” (`255.255.255.0`) or “slash notation” (`/24`).

#### Why is Subnetting Important?

- Divides a large network into smaller sub-networks (subnets) for:
  - Security
  - Performance (reduces broadcast traffic)
  - Easier management

#### Calculating Subnets

- **Formula:**  
  - Number of hosts per subnet = 2^(number of host bits) – 2
    - (Subtract 2 for network and broadcast addresses)
- Example:  
  - Mask: `255.255.255.0` (or `/24`) → 8 host bits → 254 hosts

#### Common Masks

| CIDR   | Dotted Decimal    | Hosts   |
|--------|-------------------|---------|
| /8     | 255.0.0.0         | 16,777,214 |
| /16    | 255.255.0.0       | 65,534     |
| /24    | 255.255.255.0     | 254        |
| /30    | 255.255.255.252   | 2          |

---

### 3. Routers & Routing

#### What is a Router?

- A **router** connects different networks and directs data packets between them.
- Each interface on a router belongs to a different network/subnet.

#### How Routing Works

- Routers use **routing tables** to decide where to send packets.
- **Static routing:** Manually configured paths.
- **Dynamic routing:** Routers exchange information automatically (using protocols like RIP, OSPF, BGP).

#### Default Route

- A route that matches all destinations not known in the table (usually pointing to the Internet).

#### Example

- If PC A (192.168.1.10) wants to talk to PC B (10.0.0.5), their routers need to know how to reach each network.

---

### 4. The Default Gateway

- The **default gateway** is the router your device uses to access devices outside its own subnet.
- Every host should know its default gateway IP.
- If you can’t reach another network, check your default gateway!

---

### 5. TCP/IP Protocol Suite

#### What is TCP/IP?

- The **TCP/IP suite** is the foundation of Internet and local network communication.
- It includes many protocols, but two stand out:

  - **TCP (Transmission Control Protocol):**
    - Reliable, connection-oriented
    - Ensures all data arrives and is in order
    - Used for web browsing, email, file transfers

  - **IP (Internet Protocol):**
    - Handles addressing and packet routing
    - Responsible for getting data from source to destination

#### Other Important Protocols

- **UDP (User Datagram Protocol):** Faster, but less reliable. Used for streaming, games.
- **ICMP (Internet Control Message Protocol):** Used for diagnostics (e.g., ping).
- **ARP (Address Resolution Protocol):** Resolves IP addresses to MAC addresses on local networks.

---

### 6. IPv4 vs. IPv6

| Feature        | IPv4                      | IPv6                              |
|----------------|---------------------------|-----------------------------------|
| Length         | 32 bits                   | 128 bits                          |
| Format         | 192.168.1.1               | 2001:0db8:85a3:0000:0000:8a2e:0370:7334 |
| Number of addresses | ~4.3 billion         | 3.4×10^38 (massive!)              |
| Address exhaustion | Yes                   | No                                |
| NAT required?  | Often                     | Not usually                       |

**Tip:** Most NetPractice projects use IPv4, but understanding both is useful.

---

### 7. Network Devices

- **Host/Workstation:** Any device with an IP (PC, server, printer)
- **Switch:** Connects devices within the same network; works at Layer 2 (Data Link)
- **Router:** Connects different networks/subnets; works at Layer 3 (Network)
- **Firewall:** Controls traffic, protects networks
- **Access Point:** Connects wireless devices to a wired network
- **DHCP Server:** Assigns dynamic IP addresses to devices

---

### 8. Communication Models: OSI & TCP/IP

#### OSI Model: 7 Layers

1. **Physical:** Cables, signals
2. **Data Link:** MAC addresses, switches, Ethernet
3. **Network:** IP addressing, routing
4. **Transport:** TCP/UDP, ports
5. **Session:** Connections, dialogs
6. **Presentation:** Encryption, formatting
7. **Application:** Web, email, FTP

#### TCP/IP Model: 4 Layers

1. **Network Interface (Link)**
2. **Internet (IP)**
3. **Transport (TCP/UDP)**
4. **Application**

**Why does this matter?**  
Understanding which layer a problem is on helps you troubleshoot efficiently.

---

### 9. Common Network Problems

- **IP Address Conflict:** Two devices share an IP
- **Incorrect Subnet Mask:** Devices think they're on different networks
- **Wrong Default Gateway:** Can't reach other networks
- **Routing Table Errors:** Routers don't know where to send data
- **Missing/Incorrect Routes:** Packets get lost
- **Physical Issues:** Cables unplugged, hardware failure

---

## Project Structure

Your repository should contain:

- `level1.txt`  
- `level2.txt`  
- ...  
- `level10.txt`  

Each file is your exported solution for a level in the NetPractice simulator.

---

## How to Use NetPractice

1. **Download and Extract** the simulator package.
2. **Open `index.html`** in your browser.
3. **Enter Your Login** (mandatory for grading).
4. **Solve Each Level:**
   - Read the scenario and goal.
   - Assign correct IPs, masks, gateways, and routes.
   - Use [Check again] to test your config.
   - Use [Get my config] to export your solution.
5. **Place all config files at the root of your repo** before submission.

---

## Tips for Success

- **Understand IPv4 addressing and subnetting deeply.**
- **Double-check your subnet masks and default gateways.**
- **If devices can’t communicate, check:**
  - Are they in the same subnet? If not, is routing correct?
  - Are gateways set correctly?
  - Is there an IP conflict?
- **Work step-by-step:** Fix one device at a time and test.
- **Use the logs:** They tell you what’s broken.
- **Practice subnet calculations by hand:** You’ll need this speed in real evaluations.

---

## FAQ

**Q: What if I use the wrong mask?**  
A: Devices may think they're not in the same network and won’t communicate.

**Q: How do I pick the right gateway?**  
A: The gateway must be an IP address on the same subnet as the device.

**Q: What does [Get my config] do?**  
A: It exports your current configuration, which you submit for grading.

**Q: Can I use online calculators?**  
A: For practice, yes. During evaluation, only a basic calculator is allowed.

---

## License

Distributed for educational purposes only.  
Project template and interface © [1337 UM6P / ABDOUAHI].  
All rights reserved.

---
