# Subnetting

## Introduction
- IP addresses are hierarchical and consist of a **network portion** and a **host portion**.
- The network portion is the same for all devices in a network, while the host portion varies.
- This structure allows for efficient routing and address allocation.

## IP Address Structure
- An IP address is **32 bits** long, divided into **network** and **host** portions.
- IP addresses are written in **dotted decimal notation** (e.g., `128.208.2.151`).

## Network Prefix
- A **network prefix** represents a block of IP addresses assigned to a network.
- Prefixes are written in **CIDR notation** (e.g., `128.208.0.0/24` indicates `24` bits for the network ID).

## Subnet Mask
- A **subnet mask** defines which part of an IP address belongs to the network.
- It consists of **a sequence of 1s** for the network portion and **0s for the host** portion.
- Example: The subnet mask for `128.208.0.0/24` is `255.255.255.0`.

## Routing and Prefix Distribution
- Routers use **prefix lengths** to determine network boundaries.
- Routing protocols distribute prefixes to ensure correct packet forwarding.
- Prefixes are often referred to by length, such as **“/16” (slash 16)**.

### Reference Books
1. Kurose, J. F., & Ross, K. W. *Computer Networking: A Top-Down Approach*. Pearson.
2. Tanenbaum, A. S., & Wetherall, D. J. *Computer Networks*. Pearson.

