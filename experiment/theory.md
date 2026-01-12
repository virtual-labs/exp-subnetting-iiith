### 1. IP Address 
An **IP address** is a unique numerical identifier assigned to every device on a network that uses the Internet Protocol. It serves to identify the device and its network location. The most common version, **IPv4**, is a 32-bit number. For example, a web server might have the IP address `172.217.168.14`.

---

### 2. Dotted Decimal Notation 
To make the 32-bit binary IP address more readable for humans, it is converted into **dotted decimal notation**. This is done by dividing the 32 bits into four 8-bit sections, or **octets**, and then converting each octet's binary value into a decimal number separated by dots.
* **Example:** The binary IP address `10000000.11010000.00000010.10010111` is represented as `128.208.2.151` in dotted decimal notation. 

---

### 3. Network ID and Host ID 
Every IP address is logically divided into two parts: the **Network ID** and the **Host ID**. The Network ID identifies the specific network, while the Host ID identifies the device within that network.
* **Example:** In the IP address `192.168.1.10`, if the Network ID is `192.168.1`, then `10` is the Host ID. All devices on the same network, such as `192.168.1.11` and `192.168.1.12`, share the same Network ID (`192.168.1`) but have unique Host IDs.

---

### 4. Subnet Mask 
A **subnet mask** is a 32-bit number used to determine which part of an IP address is reserved for Network ID and which is for the Host ID. It consists of `1`s for the network portion and `0`s for the host portion.
* **Example:** For a network, the subnet mask is `255.255.255.128`. In binary, this is `11111111.11111111.11111111.10000000`. 

    Consider a IP address in this network - `192.168.1.16` (`11000000.10101000.00000001.00010000`)

    - **Network ID:** The Network ID is the first **25 bits** of the IP address. For `192.168.1.10`, the Network ID is `192.168.1.0`(`11000000.10101000.00000001.0`).

    - **Host ID:** The Host ID is the last **7 bits**. For `192.168.1.10`, the Host ID is `16`(`0010000`).

    Also, possible values of IP addresess belonging to the above network will be in the range : `192.168.1.0` to `192.168.1.127`
    (`11000000.10101000.00000001.00000000` to `11000000.10101000.00000001.01111111`)

---

### 5. CIDR Notation 
**CIDR (Classless Inter-Domain Routing)** is a modern, flexible method for specifying the network portion of an IP address. It uses a slash (`/`) followed by a number indicating the number of bits in the network ID. This system replaced the rigid classful addressing system.
* **Example:** An IP address of `192.168.1.0` with a subnet mask of `255.255.255.0` can be written in CIDR notation as `192.168.1.0/24`. The `/24` signifies that the first 24 bits of the address are the network ID. A `/16` network would have 16 network bits, and so on.

---

### 6. Classes of IP Addresses 

* **Class A:** For very large networks, with a first octet range of `1-126`. Default subnet mask is `255.0.0.0` or `/8`.
* **Class B:** For medium-to-large networks, with a first octet range of `128-191`. Default subnet mask is `255.255.0.0` or `/16`.
* **Class C:** For small networks, with a first octet range of `192-223`. Default subnet mask is `255.255.255.0` or `/24`.
* **Class D:** Reserved for **multicast** addressing, with a first octet range of `224-239`.
* **Class E:** Reserved for **experimental** use, with a first octet range of `240-255`.

---

### 7. Subnetting 
**Subnetting** is the process of dividing a large network into smaller, more efficient sub-networks. This is achieved by "borrowing" bits from the host portion of the IP address to create additional network IDs.

### Illustration: 
A company has a purchased the Class C IP address range `192.168.1.0/24`. Now they wish to equally divide the addresses in 2 equal subnets. One subnet will be for the **IT Department** and the other for the **HR Department**.

Let's propose a solution to this problem:


#### 1. Complete Network

A typical **Class C network** has a default subnet mask of `/24` (255.255.255.0). In this example, we are given network address `192.168.1.0`.

* **Network ID:** `192.168.1.0`
* **Host ID Range:** The last 8 bits of the address represent the host ID, from `192.168.1.0` to `192.168.1.255`.

***

### 2. Two subnets

To divide the network into two equal parts, we need to "borrow" one bit from the host portion of the address and add it to the network portion. Our original network has a `/24` prefix. By borrowing one bit, we extend the network prefix to **`/25`**. This new bit allows us to create two subnets because a single bit can have two states: `0` or `1`.

* **Original Mask:** `/24` (255.255.255.0) -> `11111111.11111111.11111111.00000000`
* **New Mask:** `/25` (255.255.255.128) -> `11111111.11111111.11111111.10000000`

***

### 3. IP Ranges for Each Subnet

The borrowed bit now determines which subnet an IP address belongs to.

**Subnet 1: IT Department (Subnet ID = 0)**
* **IP Range:** `192.168.1.0` to `192.168.1.127`
* **Network Address:** `192.168.1.0` (all host bits are 0).
* **Broadcast Address:** `192.168.1.127` (all host bits are 1).
* **Usable Host Range:** `192.168.1.1` to `192.168.1.126` (usable for devices).

**Subnet 2: HR Department (Subnet ID = 1)**
* **IP Range:** `192.168.1.128` to `192.168.1.255`
* **Network Address:** `192.168.1.128` (all host bits are 0).
* **Broadcast Address:** `192.168.1.255` (all host bits are 1).
* **Usable Host Range:** `192.168.1.129` to `192.168.1.254` (usable for devices).


**Note**: The very first IP address in each range is reserved as the **network address**, and the very last is reserved as the **broadcast address**. These cannot be assigned to devices.