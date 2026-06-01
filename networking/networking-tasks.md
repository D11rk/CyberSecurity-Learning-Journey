# Week 3 — Day 6  
## Practical Networking Tasks

## What I learned today
- Learned how to check network interfaces using `ip link`.
- Learned how to view IP addresses and subnet information with `ip addr`.
- Practised testing connectivity using `ping`.
- Used `traceroute` to see the path packets take across the network.
- Learned how to check open ports and listening services using `ss`.
- Practised DNS troubleshooting with `dig` and `/etc/resolv.conf`.
- Learned how to view routing tables using `ip route`.

---

## Checking Network Interfaces
List all interfaces:
```
ip link show
```

Common interfaces:
- `eth0` → wired  
- `wlan0` → wireless  
- `lo` → loopback  

---

## Checking Your IP Address
```
ip addr show
```

Shows:
- IPv4 address  
- subnet mask  
- broadcast address  
- interface state  

---

## Testing Connectivity (Ping)
Ping a website:
```
ping -c 4 google.com
```

If DNS fails:
```
ping -c 4 8.8.8.8
```

---

## Tracing the Route (traceroute)
```
traceroute google.com
```

Shows each hop between you and the destination.

---

## Checking Open Ports (ss)
```
sudo ss -nltu
```

Shows:
- listening ports  
- TCP/UDP services  
- local addresses  

---

## DNS Troubleshooting

### Check DNS server:
```
cat /etc/resolv.conf
```

### Test DNS resolution:
```
dig google.com
```

---

## Viewing Routing Table
```
ip route show
```

Shows:
- default gateway  
- local routes  
- interface routing  

---

## Practice Tasks

### Task 1 — Identify your active interface
```
ip link show
```

### Task 2 — Find your IP address
```
ip addr show
```

### Task 3 — Test internet connectivity
```
ping -c 4 google.com
```

### Task 4 — Trace route to Google
```
traceroute google.com
```

### Task 5 — Check open ports
```
sudo ss -nltu
```

### Task 6 — Check DNS server
```
cat /etc/resolv.conf
```

### Task 7 — View routing table
```
ip route show
```

---

## Notes
- These commands are used daily by sysadmins, pentesters, and network engineers.
- Understanding how to diagnose connectivity, DNS, routing, and ports is essential.
- This day ties together everything learned in Week 3.

---

## Question
Teach me Week 3 Day 7 — Networking Mini-Project.
