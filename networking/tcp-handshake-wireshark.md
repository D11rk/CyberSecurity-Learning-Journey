# TCP Handshake in Wireshark

## What I learned today
- The TCP handshake is the process used to establish a reliable connection.
- It has three steps: SYN → SYN/ACK → ACK.
- Wireshark shows each step clearly in the packet list.
- Understanding the handshake helps with debugging, hacking, and network analysis.

## The 3-Way Handshake (Simple)
1. **SYN**  
   Client → Server  
   “I want to start a connection.”

2. **SYN/ACK**  
   Server → Client  
   “I received your request. Here’s my response.”

3. **ACK**  
   Client → Server  
   “Great, connection established.”

## How It Looks in Wireshark

### **1. SYN Packet**
Filter:
```
tcp.flags.syn == 1 && tcp.flags.ack == 0
```
Info field example:
```
[SYN] Seq=0 Win=64240
```

### **2. SYN/ACK Packet**
Filter:
```
tcp.flags.syn == 1 && tcp.flags.ack == 1
```
Info field example:
```
[SYN, ACK] Seq=0 Ack=1
```

### **3. ACK Packet**
Filter:
```
tcp.flags.ack == 1 && tcp.flags.syn == 0
```
Info field example:
```
[ACK] Seq=1 Ack=1
```

## Why This Matters
- Confirms a connection is established.
- Helps detect network issues.
- Used in pentesting to identify open ports.
- Helps understand how TCP ensures reliability.


## Notes
- Every TCP connection starts with this handshake.
- If you see SYN but no SYN/ACK, the port is closed or blocked.
- If you see repeated SYN packets, it may indicate scanning or attacks.


