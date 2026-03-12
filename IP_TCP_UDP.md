
## Quick Notes:
**IP**
→ address on package

**TCP**
→ ensures pages arrive in order and none missing

**UDP**
→ throws pages quickly without checking order

### When To Use TCP vs UDP

Use TCP When Reliability Matters

Examples:
| Application           | Reason                |
| --------------------- | --------------------- |
| Websites (HTTP/HTTPS) | Need full data        |
| File transfer (FTP)   | No corruption allowed |
| Emails                | Must arrive correctly |
| Database connections  | Data integrity        |


Use **UDP** When Speed Matters

Examples:
| Application       | Why UDP                |
| ----------------- | ---------------------- |
| Video streaming   | Small packet loss ok   |
| Online gaming     | latency critical       |
| VoIP calls        | real-time              |
| DNS queries       | small messages         |
| Live broadcasting | speed over reliability |


| Feature     | TCP    | UDP    |
| ----------- | ------ | ------ |
| Connection  | Yes    | No     |
| Reliability | Yes    | No     |
| Ordering    | Yes    | No     |
| Speed       | Slower | Faster |
| Overhead    | High   | Low    |



## Internet Protocol

**What IP Does ?**

IP is responsible for **delivering packets from one machine to another across network**s. Think of it like postal service addressing. Routers read the destination IP and decide where to forward the packet.

```
Source IP:      192.168.1.10
Destination IP: 142.250.183.206
```

**IP Packet Structure (simplified)**

```
| Header | Payload |

Header Contains:

Version
Source IP
Destination IP
TTL
Protocol (TCP / UDP)
Fragment info


Example:
Protocol: 6  → TCP
Protocol: 17 → UDP
```

So **IP doesn't know HTTP or data meaning**. It only knows:
"Send this packet to that IP address."

**Key Characteristics of IP : **

IP is best-effort delivery. It does NOT guarantee:

1. Delivery
2. Order
3. No duplication
4. No corruption

Packets can:
```
arrive late
arrive twice
arrive out of order
get dropped
```

## TCP (Transmission Control Protocol)

TCP **sits above IP** and provides **reliable communication**.

Key idea:

TCP converts unreliable IP into reliable communication.

### TCP Packet Structure (simplified)
```
Source Port
Destination Port
Sequence Number
Acknowledgement Number
Flags (SYN, ACK, FIN)
Window Size
Checksum
Payload
```

Ports allow multiple applications:
```
80   → HTTP
443  → HTTPS
22   → SSH
3306 → MySQL
```

### TCP Features

**1. Connection-oriented**

  Before sending data:
  ```
  Client ---- SYN ----> Server
  Client <--- SYN-ACK --- Server
  Client ---- ACK ----> Server
  ```
  
  This is called **3-way handshake.**

**2. Reliable Delivery**

TCP guarantees:
1. packets delivered
2. correct order
3. no duplicates

How?

Sequence numbers

Packet1 → seq=1
Packet2 → seq=2
Packet3 → seq=3

Receiver acknowledges:

ACK = 3

Meaning: "I received up to packet 3".

**3. Retransmission**

If ACK not received:

timeout → resend packet

This ensures no packet loss.

**4. Flow Control**

Receiver tells sender: Window size = 5000 bytes

Meaning: "Don't send more than 5000 bytes at a time."

This prevents receiver overload.

**5. Congestion Control**

TCP adjusts speed based on network conditions.

Algorithms:
1. Slow Start
2. Congestion Avoidance
3. Fast Retransmit
4. Fast Recovery

Goal: avoid network collapse


## UDP (User Datagram Protocol)

**UDP is minimal transport protocol.**

**Goal**: Send packets fast with minimal overhead.

UDP does NOT provide:

1. connection : No handshake.
2. reliability
3. ordering
4. retransmission
5. congestion control

**UDP Packet**
```
Very small header:

Source Port
Destination Port
Length
Checksum
Payload
```




