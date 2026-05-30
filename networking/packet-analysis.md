# Week 3 — Day 5  
## Wireshark & Packet Analysis

## What I learned today
- Learned what Wireshark is and how it captures and analyzes packets.
- Installed Wireshark on my Linux VM and configured permissions.
- Understood the three main panes: packet list, packet details, and packet bytes.
- Learned how to apply display filters to isolate specific traffic.
- Practised analyzing DNS, ICMP, HTTP, and ARP packets.
- Learned how to follow TCP streams to view full conversations.

---

## What is Wireshark?
Wireshark is a packet analyzer that lets you inspect network traffic in real time.

It shows:
- Who is talking to who  
- What protocols are used  
- What data is being sent  
- How packets move across the network  

It is essential for learning networking and debugging traffic.

---

## Installing Wireshark
```
sudo apt update
sudo apt install wireshark -y
```

Allow non-superusers to capture packets → choose **Yes**.

Add yourself to the Wireshark group:
```
sudo usermod -aG wireshark $USER
```

Reboot your VM.

---

## Starting Wireshark
Launch it:
```
wireshark
```

Select your active interface (usually `eth0` or `wlan0`) and click **Start Capture**.

---

## Wireshark Interface Overview
Wireshark has 3 main panes:

1. **Packet List** — all captured packets  
2. **Packet Details** — protocol layers (Ethernet → IP → TCP → HTTP)  
3. **Packet Bytes** — raw hex data  

---

## Useful Display Filters

### Protocol filters
```
http
dns
icmp
arp
```

### IP filters
```
ip.addr == 192.168.1.10
```

### Port filters
```
tcp.port == 80
udp.port == 53
```

Filters help isolate specific traffic from thousands of packets.

---

## Packet Analysis Examples

### DNS Lookup
1. Start capture  
2. Run:
   ```
   ping google.com
   ```
3. Filter:
   ```
   dns
   ```

### ICMP (Ping)
Filter:
```
icmp
```

### HTTP Traffic
Visit a non-HTTPS site and filter:
```
http
```

### ARP (Local Network Discovery)
Filter:
```
arp
```

---

## Follow TCP Stream
Right-click any TCP packet → **Follow → TCP Stream**

This shows the entire conversation between two devices.

---

## Notes
- Wireshark is a core tool for understanding how networks actually work.
- Filters are essential for making sense of large captures.
- Packet analysis helps with debugging, recon, and learning protocols.
- Following streams is useful for analyzing conversations and traffic flows.

---

## Question
Teach me Week 3 Day 6 — Practical Networking Tasks.
