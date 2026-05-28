# Week 3 — Day 2  
## Ports, Protocols & Services

## What I learned today
- Understood what ports are and how they allow communication between applications.
- Learned the difference between TCP and UDP.
- Studied the three port ranges: well-known, registered, and dynamic.
- Learned the most important ports used in cybersecurity.
- Understood how services run behind ports and how protocols define communication rules.
- Learned how ports are used in scanning, enumeration, and exploitation.

---

## What Are Ports?
Ports are logical communication endpoints used by applications.

- IP address = the device  
- Port = the specific application on that device  

Example:
```
192.168.1.10:443
```

---

## Port Ranges

| Range | Numbers | Purpose |
|-------|----------|----------|
| **Well-known ports** | 0–1023 | Standard services |
| **Registered ports** | 1024–49151 | Vendor applications |
| **Dynamic ports** | 49152–65535 | Temporary client ports |

---

## TCP vs UDP

### TCP
- Reliable  
- Connection-oriented  
- Guarantees delivery  
- Used for: HTTP, HTTPS, SSH, FTP  

### UDP
- Fast  
- Connectionless  
- No guarantee  
- Used for: DNS, VoIP, games  

---

## Common Ports You Must Know

| Service | Protocol | Port |
|---------|----------|------|
| FTP | TCP | 21 |
| SSH | TCP | 22 |
| Telnet | TCP | 23 |
| SMTP | TCP | 25 |
| DNS | UDP/TCP | 53 |
| HTTP | TCP | 80 |
| POP3 | TCP | 110 |
| HTTPS | TCP | 443 |
| SMB | TCP | 445 |
| MySQL | TCP | 3306 |
| RDP | TCP | 3389 |
| HTTP-alt | TCP | 8080 |

---

## How Ports Work (Example)
When you visit a website:

1. Your computer opens a random high port (e.g., 53211).  
2. It connects to the server’s port 443.  
3. Data flows between:
   ```
   your_ip:53211 → server_ip:443
   ```

---

## Why Ports Matter in Cybersecurity
- Nmap scans ports to find attack surfaces.  
- Exploits target specific services (e.g., SMB, SSH).  
- Firewalls allow/deny traffic based on ports.  
- Enumeration depends on knowing which service runs where.  

Ports are the entry points for attacks and defenses.

---

## Practice Tasks

### Identify open ports on your VM
```
sudo ss -tulnp
```

### Scan your VM with Nmap
```
nmap -sV -p- <your-ip>
```

### Memorise the top 15 ports
22, 21, 23, 25, 53, 80, 110, 139, 143, 443, 445, 3306, 3389, 8080, 53

---

## Notes
- Ports + protocols = the foundation of network communication.
- Understanding services is essential for scanning and exploitation.
- This knowledge prepares you for Nmap, Netcat, and web hacking.

---

## Question
Teach me Week 3 Day 3 — Network Tools (Nmap, Netcat, Dig, Curl).
