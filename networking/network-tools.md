# Week 3 — Day 3  
## Network Tools (Nmap, Netcat, Dig, Curl)

## What I learned today
- Learned how to install essential networking tools on a Linux VM.
- Practised using Nmap for scanning hosts, ports, and services.
- Learned how to use Netcat for port testing, listeners, and file transfer.
- Used Dig for DNS lookups, tracing, and querying specific DNS servers.
- Used Curl to interact with web servers and APIs.
- Understood how each tool fits into reconnaissance and debugging.

---

## Installing All Tools
Install Nmap, Netcat, Dig, and Curl on any Debian-based VM:

```
sudo apt update && sudo apt install nmap netcat-openbsd dnsutils curl -y
```

Verify installation:
```
nmap --version
nc -h
dig -v
curl --version
```

---

## Nmap — Network Scanner

### Basic scan
```
nmap <target>
```

### Scan all ports
```
nmap -p- <target>
```

### Service & version detection
```
nmap -sV <target>
```

### OS detection
```
nmap -O <target>
```

### Example
```
nmap -sV -p- 192.168.1.10
```

---

## Netcat — Raw TCP/UDP Tool

### Check if a port is open
```
nc -vz <ip> <port>
```

### Create a listener
```
nc -l 4444
```

### Connect to listener
```
nc <ip> 4444
```

### File transfer
Receiver:
```
nc -l 9090 > received.txt
```

Sender:
```
nc <receiver-ip> 9090 < file.txt
```

---

## Dig — DNS Lookup Tool

### Basic lookup
```
dig example.com
```

### Short output (just IP)
```
dig +short example.com
```

### Trace DNS path
```
dig +trace example.com
```

### Query a specific DNS server
```
dig @8.8.8.8 example.com
```

---

## Curl — Web Request Tool

### GET request
```
curl http://example.com
```

### Show headers
```
curl -I http://example.com
```

### POST request
```
curl -X POST -d "user=test&pass=123" http://example.com/login
```

### Save output
```
curl http://example.com -o page.html
```

---

## Notes
- These tools form the foundation of network reconnaissance.
- Nmap maps networks, Netcat communicates raw data, Dig interrogates DNS, Curl interacts with web servers.
- All tools are essential for pentesting, debugging, and enumeration.

---

## Question
Teach me Week 3 Day 4 — Firewalls & Packet Filtering (ufw, iptables).
