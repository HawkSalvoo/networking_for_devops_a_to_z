# TCP/IP & OSI Model
---
## Fundamentals of the OSI Model
---

## What is TCP/IP?

TCP/IP (Transmission Control Protocol/Internet Protocol) is the foundational communication protocol suite for modern computer networks, including the Internet. It defines how data is sent, received, and routed between devices. TCP/IP is a layered model that ensures interoperability across diverse hardware and software platforms.

---

## TCP/IP Model Layers

The TCP/IP protocol suite has four layers, each responsible for specific functions:

Application Layer

-  Interfaces directly with end-user applications.

-  Protocols: HTTP, HTTPS, FTP, SMTP, DNS, Telnet.

-  Responsible for network services, file transfers, email, and web browsing.

Transport Layer

-  Ensures reliable data transfer between devices.

-  Protocols: TCP (reliable, connection-oriented), UDP (unreliable, connectionless).

-  Handles segmentation, flow control, and error correction.

Internet Layer

-  Handles logical addressing and routing of data packets.

-  Protocols: IP (IPv4, IPv6), ICMP, ARP.

-  Determines the best path for data across networks.

Network Access / Link Layer

-  Deals with physical transmission over network hardware.

-  Protocols: Ethernet, Wi-Fi (IEEE 802.11), PPP.

-  Manages framing, MAC addressing, and access to the physical medium.

---

## Visual Diagram of TCP/IP Model

+------------------------+
|  Application Layer     |  <-- HTTP, FTP, SMTP, DNS
+------------------------+
|  Transport Layer       |  <-- TCP, UDP
+------------------------+
|  Internet Layer        |  <-- IP, ICMP, ARP
+------------------------+
|  Network Access Layer  |  <-- Ethernet, Wi-Fi, PPP
+------------------------+

Flow of Data:

Data originates from the Application Layer.

Transport Layer divides data into segments and ensures delivery.

Internet Layer encapsulates segments into packets with logical addresses.

Network Access Layer converts packets into frames for physical transmission.

---
## Two Main Protocols
---
### 1. TCP (Transmission Control Protocol)

TCP (Transmission Control Protocol) is a connection-oriented protocol in the Internet Protocol Suite (TCP/IP). It ensures:

-  Reliable data delivery
-  Ordered data transfer
-  Error detection and correction
-  Flow control
---
#### TCP Three-Way Handshake

TCP establishes a connection using a three-way handshake. This ensures both client and server are ready to communicate.

Steps:

SYN (Synchronize)

- The client sends a TCP packet with the SYN flag set to the server.

-    Purpose: Request to establish a connection and synchronize sequence numbers.

SYN-ACK (Synchronize-Acknowledge)

-    The server responds with a packet having SYN + ACK flags set.

-    Purpose: Acknowledge the client’s request and synchronize the server’s sequence number.

ACK (Acknowledge)

-   The client sends a final ACK packet to the server.

-    Purpose: Confirm the connection is established.

After this handshake, the TCP connection is open, and data can flow both ways.

---

#### TCP Connection Termination

TCP uses a four-way handshake to close a connection:

-  Client sends FIN → server

-  Server replies ACK → acknowledges FIN

-  Server sends FIN → closes its side

-  Client sends ACK → acknowledges server FIN

This ensures graceful connection closure.

---

### 2. UDP (User Datagram Protocol)

UDP (User Datagram Protocol) is a connectionless protocol in the TCP/IP suite. Key characteristics:

-  No connection setup – sends data without establishing a session

-  Unreliable delivery – packets may be lost, duplicated, or arrive out of order

-  No flow control or error correction

-  Used in applications where speed is more important than reliability, e.g., DNS, streaming, VoIP, online gaming

---

## TCP vs UDP comparison

| Feature               | TCP (Transmission Control Protocol)                   | UDP (User Datagram Protocol)                      |
| --------------------- | ----------------------------------------------------- | ------------------------------------------------- |
| **Type**              | Connection-oriented                                   | Connectionless                                    |
| **Reliability**       | Reliable (ensures delivery with acknowledgments)      | Unreliable (no guarantee of delivery)             |
| **Data Flow**         | Stream-oriented                                       | Message-oriented (datagrams)                      |
| **Error Checking**    | Error checking and correction                         | Error checking only (no correction)               |
| **Connection Setup**  | Requires a 3-way handshake                            | No connection setup                               |
| **Speed**             | Slower due to overhead                                | Faster due to minimal overhead                    |
| **Ordering**          | Ensures data is received in order                     | No guarantee of order                             |
| **Use Cases**         | Web browsing, emails, file transfer (HTTP, SMTP, FTP) | Video streaming, online gaming, VoIP, DNS queries |
| **Header Size**       | 20 bytes                                              | 8 bytes                                           |
| **Overhead**          | High                                                  | Low                                               |
| **Example Protocols** | HTTP, HTTPS, FTP, SMTP                                | DNS, DHCP, TFTP, VoIP                             |

---

## Fundamentals of the OSI Model
---

### What is OSI?

The OSI (Open Systems Interconnection) Model is a conceptual framework used to understand and implement network communications between different systems. It divides network communication into seven layers, each with distinct functions.

---

### OSI Model Layers

| Layer Number | Layer Name   | Key Function                                                   |
| ------------ | ------------ | -------------------------------------------------------------- |
| 7            | Application  | User interface, apps like browsers, email clients. (HTTP, FTP) |
| 6            | Presentation | Data formatting, encryption, compression.                      |
| 5            | Session      | Establishes, manages, terminates connections.                 |
| 4            | Transport    | Reliable data transfer (TCP/UDP), segmentation                     |
| 3            | Network      | Routing, logical addressing (IP).                    |
| 2            | Data Link    | MAC addresses, error detection, frames. |
| 1            | Physical     | Actual transmission over media (cables, wireless). |

---

### Visual Diagram

- Vertical flow: inside each device (top-down to send, bottom-up to receive).

- Horizontal arrows: communication between the same layers on two devices.

```
Device A                                    Device B
-----------                                  -----------
Application (7)  ------------------------>  Application (7)
Presentation (6) ------------------------>  Presentation (6)
Session (5)       ------------------------>  Session (5)
Transport (4)     ------------------------>  Transport (4)
Network (3)       ------------------------>  Network (3)
Data Link (2)     ------------------------>  Data Link (2)
Physical (1)      ========================> Physical (1)

```

---

## Key Takeaways

✅ TCP is reliable but slower (HTTP, SSH)
✅ UDP is fast but unreliable (streaming, DNS)
✅ Ports identify specific services on a host
✅ TCP handshake establishes connections
✅ Understanding layers helps debug network issues
✅ Most DevOps work happens at Layer 4 (Transport) and Layer 7 (Application).



