# Week 3 — Day 4  
## Firewalls & Packet Filtering (UFW + iptables)

## What I learned today
- Understood what a firewall is and how it filters network traffic.
- Learned how UFW provides a simple interface for managing firewall rules.
- Practised enabling UFW safely and allowing/denying ports.
- Learned how iptables works at a lower level for advanced control.
- Practised adding basic iptables rules for SSH, HTTP, and HTTPS.
- Learned how to view, save, and persist iptables rules.

---

## What is a Firewall?
A firewall controls incoming and outgoing network traffic based on rules.

It can:
- **ALLOW** traffic  
- **DENY/DROP** traffic  
- **REJECT** traffic with an error  

Linux firewalls use **netfilter** in the kernel.  
Tools like **UFW** and **iptables** manage netfilter rules.

---

## UFW — Uncomplicated Firewall

### Install UFW
```
sudo apt install ufw -y
```

### Check status
```
sudo ufw status verbose
```

### Allow SSH (important before enabling)
```
sudo ufw allow 22/tcp
```

### Enable UFW
```
sudo ufw enable
```

### Allow common ports
```
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

### Default policies
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

### View rules
```
sudo ufw status numbered
```

### Delete a rule
```
sudo ufw delete <rule-number>
```

---

## iptables — Advanced Firewall

### Install iptables
```
sudo apt install iptables -y
```

### View current rules
```
sudo iptables -L -n -v --line-numbers
```

---

## Basic iptables Rules

### Set default policies
```
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT ACCEPT
```

### Allow loopback
```
sudo iptables -A INPUT -i lo -j ACCEPT
```

### Allow established connections
```
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

### Allow SSH
```
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

### Allow HTTP/HTTPS
```
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

---

## Make iptables Rules Persistent
```
sudo apt install iptables-persistent -y
sudo netfilter-persistent save
```

## Question
Teach me Week 3 Day 5 — Wireshark & Packet Analysis.
