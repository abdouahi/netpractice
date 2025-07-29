What Is TCP? :
-> https://www.fortinet.com/resources/cyberglossary/tcp-ip

IP Address, ipv6 ipv4:
->https://www.fortinet.com/resources/cyberglossary/what-is-ip-address

What Is UDP (User Datagram Protocol)? :
->https://www.fortinet.com/resources/cyberglossary/user-datagram-protocol-udp


# NetPractice

**Version:** 3.4  
**Summary:** Learn the basics of networking by configuring and troubleshooting simulated networks through a web-based interface.

---

## Table of Contents

- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [How the Interface Works](#how-the-interface-works)
- [Levels and Objectives](#levels-and-objectives)
- [Configuration & Submission](#configuration--submission)
- [Essential Networking Concepts](#essential-networking-concepts)
  - [What is a Network?](#what-is-a-network)
  - [IP Addresses (IPv4 & IPv6)](#ip-addresses-ipv4--ipv6)
  - [Subnet Mask and Subnetting](#subnet-mask-and-subnetting)
  - [Routers and Routing](#routers-and-routing)
  - [Default Gateway](#default-gateway)
  - [TCP/IP Protocol Suite](#tcpip-protocol-suite)
  - [IPv4 vs. IPv6](#ipv4-vs-ipv6)
  - [Devices in a Network](#devices-in-a-network)
  - [Common Network Issues](#common-network-issues)
- [Tips for Success](#tips-for-success)
- [Peer-Evaluation & Defense](#peer-evaluation--defense)
- [FAQ](#faq)
- [License](#license)

---

## Introduction

NetPractice is a hands-on project designed to introduce you to the basics of computer networking. You’ll solve 10 practical network configuration challenges using a browser-based simulator. This project helps you understand how devices communicate over networks and how to troubleshoot common networking issues.

---

## Project Structure

You will submit the following files at the root of your repository:

- `level1.txt`  
- `level2.txt`  
- ...  
- `level10.txt`  

Each file is your solution for one of the 10 levels in the NetPractice interface.

---

## Getting Started

1. **Download the Project Files:**  
   Extract the NetPractice package and open `index.html` in your web browser.

2. **Enter Your Login:**  
   Enter your login in the interface to track your progress and ensure your work is credited.

3. **Solve the Exercises:**  
   Each level presents a broken network. Adjust its configuration (IP addresses, subnet masks, routes, etc.) until it works.

4. **Export & Submit:**  
   After each level, click [Get my config] to export your solution as a `.txt` file. Place all 10 files at the root of your GitHub repo.

---

## How the Interface Works

- **Objectives:** Each level describes a specific networking goal (e.g., "Make all hosts communicate").
- **Network Diagram:** Shows devices and their connections.
- **Editable Fields:** Fill in IP addresses, subnet masks, and routes.
- **Buttons:**
  - **[Check again]:** Validates your configuration.
  - **[Get my config]:** Exports your solution.

- **Logs:** Error messages help you debug broken configurations.

---

## Levels and Objectives

- **10 Levels:** Each provides a unique network scenario.
- **Solve and Export:** Configure each network until the goal is met, then export your solution.

---

## Configuration & Submission

1. **Configure Each Level:**  
   Solve the network problem as described.

2. **Export Solution:**  
   Use [Get my config] to download your configuration for each level.

3. **Name Files:**  
   Exported files should be named `level1.txt` through `level10.txt`.

4. **Place in Repo:**  
   All files must be at the root of your Git repo.

---

## Essential Networking Concepts

### What is a Network?

A **network** is a group of devices (computers, servers, routers, etc.) connected together to share information and resources.

---

### IP Addresses (IPv4 & IPv6)

**IP (Internet Protocol) Address**:  
A unique identifier for each device on a network.

- **IPv4**:  
  - Format: Four numbers separated by dots (e.g., `192.168.1.1`)
  - Each number (octet) can be 0–255.
  - Example: `10.0.0.5`

- **IPv6**:  
  - Format: Eight groups of four hexadecimal digits separated by colons (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`)
  - Much longer, allows for many more addresses.
  - Used as IPv4 addresses run out.

**Why do we need IP addresses?**  
They uniquely identify each device so data goes to the right place, just like postal addresses for houses.

---

### Subnet Mask and Subnetting

- **Subnet Mask**:  
  - Defines which part of an IP address is the network and which is the host.
  - Example: `255.255.255.0` (means the first 3 numbers identify the network, the last is the device)

- **Subnetting**:  
  - Dividing a large network into smaller, more manageable sub-networks.
  - Helps improve performance and security.

**Example:**  
A network `192.168.1.0/24` with subnet mask `255.255.255.0` allows 254 devices (hosts), from `192.168.1.1` to `192.168.1.254`.

---

### Routers and Routing

- **Router**:  
  - A device that connects different networks and forwards data between them.
  - Decides the best path for data to travel.

- **Routing**:  
  - The process of finding a path for data from one network to another.
  - Routers use routing tables to know where to send each packet.

**Why do we need routers?**  
To connect different networks (e.g., your home network to the internet).

---

### Default Gateway

- The **default gateway** is the device (usually a router) on your network that sends traffic to destinations outside your local network.
- Every device on a network needs to know its gateway to reach the internet or other networks.

---

### TCP/IP Protocol Suite

- **TCP/IP** is the fundamental suite of protocols used for networking.
  - **TCP (Transmission Control Protocol):** Ensures reliable, ordered delivery of data.
  - **IP (Internet Protocol):** Handles addressing and routing the data packets.

**Other Key Protocols:**
- **UDP (User Datagram Protocol):** Faster but less reliable than TCP.
- **ICMP (Internet Control Message Protocol):** Used for error messages and diagnostics (e.g., ping).

---

### IPv4 vs. IPv6

| Feature      | IPv4                      | IPv6                                   |
|--------------|---------------------------|----------------------------------------|
| Address size | 32 bits (4 octets)        | 128 bits (8 groups of 4 hex digits)    |
| Format       | 192.168.1.1               | 2001:0db8:85a3:0000:0000:8a2e:0370:7334|
| Total addresses | ~4 billion             | ~340 undecillion (enough for everyone!)|
| Usage        | Most common (but running out)| Newer, growing adoption              |

---

### Devices in a Network

- **Workstation/Host:** End-user device (PC, laptop, etc.)
- **Router:** Connects different networks and forwards data.
- **Switch:** Connects devices within the same network.
- **Server:** Provides services/data to other devices.

---

### Common Network Issues

- **IP Address Conflicts:** Two devices have the same IP address.
- **Incorrect Subnet Mask:** Devices can't communicate if masks don't match.
- **Wrong Default Gateway:** Devices can't reach outside networks.
- **Missing Routes:** Routers don't know where to send packets.

---

## Tips for Success

- **Practice subnetting and IP addressing.**
- **Read each exercise’s goal carefully.**
- **Use the logs for troubleshooting.**
- **Export your config after each level.**
- **During defense, only a basic calculator is allowed.**

---

## Peer-Evaluation & Defense

- **You will be asked to solve 3 random levels in 15 minutes.**
- **No external tools or notes allowed (except a calculator).**
- **Make sure your login is in your config files.**

---

## FAQ

**Q: What if I name my files wrong?**  
A: Only correctly named files at the root of your repo are graded.

**Q: Can I use subnet calculators?**  
A: For practice, yes. In the exam, only a basic calculator is allowed.

**Q: What if I forget to enter my login?**  
A: Your submission may be invalid—always enter your login before exporting.

---

## License

Distributed for educational purposes only.  
Project template and interface © [Your School/Organization].  
All rights reserved.

---
