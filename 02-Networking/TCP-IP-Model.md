# Transmission Control Protocol/Internet Protocol (TCP/IP) Model

## Description:
The TCP/IP Model is a conceptual framework used to describe how data is transmitted over a network. It simplifies the OSI model into four layers, focusing on practical implementation for Internet communication. TCP/IP defines the protocols, rules, and standards that enable computers and devices to exchange information reliably across networks.

In simpler terms, the TCP/IP model is like the blueprint for sending data online—it shows how computers “talk” to each other and ensures messages get to the right place safely and efficiently.

The four layers are: 4.) Application, 3.) Transport, 2.) Internet, and 1.) Network Access (Link) Layers.

## Diagram:
![Diagram of TCP/IP Model](../10-Personal/Images/OSI-vs-TCP-vs-Hybrid-2.webp)

---

## Breaking Down the Layers

The **top layer**, the Application Layer, handles user-facing processes, software communication, and protocols like HTTP, FTP, and SMTP.  

The **Transport Layer** manages end-to-end communication, providing reliability, sequencing, and flow control through protocols such as TCP and UDP.  

The **Internet Layer** (sometimes called the Network Layer) handles logical addressing and routing to ensure data reaches the correct destination across networks, using protocols like IP and ICMP.  

The **Network Access (Link) Layer** covers the physical and data link components for transmitting raw data across a medium. It includes Ethernet, Wi-Fi, and other hardware-specific protocols.

**In plain English:**  
Think of TCP/IP like sending a letter: the Network Access layer handles putting the letter in the mailbox, the Internet layer decides the best route, the Transport layer ensures the letter is delivered in order and intact, and the Application layer is the envelope and content—the message the recipient actually reads.

---

### Ways to remember the order (mnemonics):
- **A**pplication, **T**ransport, **I**nternet, **N**etwork Access: "All The Internet Needs"

---

## Each Layer:

### Application Layer (Layer 4):
The top layer provides services and interfaces for software applications. It handles communication protocols and supports tasks like email, file transfer, and web browsing.

**Examples/Protocols:** HTTP, HTTPS, FTP, SMTP, DNS, Telnet, SSH

**In plain English:**  
This is the part of the network your software interacts with—like your browser, email client, or chat app—allowing you to communicate with other systems.

---

### Transport Layer (Layer 3):
This layer is responsible for end-to-end communication and reliability. It segments and reassembles data, manages flow control, and ensures proper sequencing.

**Examples/Protocols:** TCP (reliable, connection-oriented), UDP (connectionless, faster)

**In plain English:**  
Think of it as the postal service that makes sure your packages (data) arrive safely, in order, and without missing pieces.

---

### Internet Layer (Layer 2):
The Internet Layer routes data between devices across networks. It determines logical addressing, packet forwarding, and path selection.

**Examples/Protocols:** IP, IPv6, ICMP, IGMP

**In plain English:**  
This is like the GPS for your data, finding the best route to the recipient's device across multiple networks.

---

### Network Access (Link) Layer (Layer 1):
This layer is responsible for physical transmission of data and managing access to the network medium. It includes hardware addressing, frame formatting, and error detection.

**Examples/Protocols/Technologies:** Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11), PPP, DSL, ATM

**In plain English:**  
This is the road and delivery trucks that physically move your data from one device to another.

---

## Data Encapsulation
Similar to OSI, TCP/IP encapsulates data as it moves down the layers:

| PDU | Layer |
|------|--------|
| Data | Application |
| Segment | Transport |
| Packet | Internet |
| Frame | Network Access |

---

## Reference/Resources:
- Chapter 6 from Network+ Sybex Study Guide
- [Professor Messer](https://www.professormesser.com/network-plus/n10-009/n10-009-video/introduction-to-ip-n10-009/)