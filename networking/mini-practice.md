# Week 3 — Day 7  
## Networking Mini‑Project

## What I learned today
- Performed a full local network scan using Nmap.
- Captured and analysed packets in Wireshark.
- Identified SYN, SYN‑ACK, DNS, and ARP traffic using filters.
- Compared Nmap results with Wireshark packet behaviour.
- Learned how to document findings like a real pentester.
- Understood how tools from the entire week work together in a real workflow.

---

## Step 1 — Identify Network Information
```
ip addr show
ip route show
```

Record:
- IP address  
- Subnet  
- Default gateway  

---

## Step 2 — Scan the Local Network (Nmap)
Create a project folder:
```
mkdir network_project && cd network_project
```

Scan the entire subnet:
```
nmap -sS 192.168.1.0/24 -oN scan_results.txt
```

Look for:
- Active hosts  
- Open ports  
- Services  

---

## Step 3 — Capture Traffic (Wireshark)
1. Open Wireshark  
2. Select your active interface  
3. Start capture  
4. Run the Nmap scan again:
   ```
   nmap -sS 192.168.1.0/24
   ```
5. Save the capture as:
   ```
   nmap_scan_capture.pcapng
   ```

---

## Step 4 — Analyse Packets in Wireshark

### SYN packets (connection attempts)
```
tcp.flags.syn==1 && tcp.flags.ack==0
```

### SYN‑ACK packets (open ports)
```
tcp.flags.syn==1 && tcp.flags.ack==1
```

### DNS traffic
```
dns
```

### ARP traffic
```
arp
```

---

## Step 5 — Compare Nmap Results With Wireshark
For each host:
- Check if SYN → SYN‑ACK matches open ports  
- Check if SYN → RST matches closed ports  
- Confirm services  
- Identify unexpected traffic  

---

## Step 6 — Write Findings Summary
Create:
```
nano findings.md
```

Include:
- Devices discovered  
- Open ports  
- Interesting services  
- Packet behaviour  
- Any risks or misconfigurations  

---

## Optional Bonus Tasks
### Capture DNS lookup
```
ping google.com
```
Filter:
```
dns
```

### Follow a TCP stream
Right‑click → Follow → TCP Stream

### Deep scan a single host
```
nmap -sC -sV <ip>
```


## Question
Start Week 4
