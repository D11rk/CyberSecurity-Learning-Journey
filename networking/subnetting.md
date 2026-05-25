# Week 3 — Day 1  
## IP Addressing Deep Dive (CIDR, Subnetting, Routing Basics)

## What I learned today
- Understood how IPv4 addresses are structured (network + host).
- Learned how CIDR notation defines network size.
- Practised subnetting and calculating usable hosts.
- Learned how to find network and broadcast addresses.
- Understood routing basics and how default gateways work.
- Learned how to view routing tables on Linux.

---

## IP Address Structure
An IPv4 address has two parts:
- **Network portion**
- **Host portion**

Example:
```
192.168.1.10
```

---

## CIDR Notation
CIDR tells how many bits belong to the network.

Examples:
- `/24` → 255.255.255.0  
- `/16` → 255.255.0.0  
- `/8`  → 255.0.0.0  

---

## Subnet Masks & Host Counts

| CIDR | Mask | Usable Hosts |
|------|------------------|----------------|
| /24  | 255.255.255.0    | 254            |
| /25  | 255.255.255.128  | 126            |
| /26  | 255.255.255.192  | 62             |
| /27  | 255.255.255.224  | 30             |
| /30  | 255.255.255.252  | 2              |

Formula:
```
2^(host bits) - 2
```

---

## Subnetting Example
Given:
```
192.168.1.0/24
```

Split into 4 subnets → `/26`

Subnets:
- 192.168.1.0/26  
- 192.168.1.64/26  
- 192.168.1.128/26  
- 192.168.1.192/26  

Each subnet has:
- 62 usable hosts  
- 1 network address  
- 1 broadcast address  

---

## Routing Basics

### Default Gateway
The router your system uses to reach other networks.

Check it:
```
ip route
```

---

## Question
Teach me Week 3 Day 2 — Ports, Protocols & Services.
