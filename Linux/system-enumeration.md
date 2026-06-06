# Week 4 — Day 2  
## System Enumeration (Privilege Escalation)

## What I learned today
- Learned why enumeration is the most important step in privilege escalation.
- Understood how to gather system, user, process, and service information.
- Practised checking kernel versions, OS details, users, groups, and running processes.
- Learned how to inspect networking, cron jobs, SUID binaries, and sudo permissions.
- Built a full enumeration workflow used in real pentesting.

---

## Why Enumeration Matters
Before escalating privileges, you must understand the system.

Enumeration helps identify:
- misconfigurations  
- weak permissions  
- vulnerable software  
- exploitable services  
- writable files  
- scheduled tasks  
- SUID binaries  
- sudo misconfigurations  

Privilege escalation is mostly **information gathering**.

---

## System Information

### OS version
```
cat /etc/os-release
```

### Kernel version
```
uname -a
```

Older kernels may be vulnerable.

---

## User & Group Information

### List all users
```
cat /etc/passwd
```

### List all groups
```
cat /etc/group
```

### Logged-in users
```
who
w
```

### Login history
```
last
```

---

## Process Enumeration

### List all processes
```
ps aux
```

### Processes running as root
```
ps aux | grep root
```

Root-owned processes may be exploitable.

---

## Networking & Services

### Network interfaces
```
ip addr
```

### Listening ports
```
ss -nltu
```

### DNS configuration
```
cat /etc/resolv.conf
```

### Firewall rules
```
iptables -L
```

---

## Scheduled Tasks (Cron Jobs)

### System-wide cron jobs
```
cat /etc/crontab
```

### Cron directories
```
ls -la /etc/cron.*
```

Writable cron scripts can lead to root.

---

## Permissions & Misconfigurations

### SUID binaries
```
find / -perm -4000 2>/dev/null
```

SUID binaries run as root even if you don’t.

### Writable files
```
find / -writable 2>/dev/null
```

Writable root-owned files are dangerous.

### Sudo permissions
```
sudo -l
```

If you can run something as root → instant escalation.

---

## Installed Software

### List installed packages
```
dpkg -l
```

Outdated or vulnerable software may be exploitable.

---

## Practice Tasks

### Task 1 — Gather system info
```
uname -a
cat /etc/os-release
```

### Task 2 — Enumerate users & groups
```
cat /etc/passwd
cat /etc/group
```

### Task 3 — List processes
```
ps aux
```

### Task 4 — Check networking
```
ss -nltu
ip addr
```

### Task 5 — Inspect cron jobs
```
cat /etc/crontab
```

### Task 6 — Find SUID binaries
```
find / -perm -4000 2>/dev/null
```

### Task 7 — Check sudo permissions
```
sudo -l
```

---

## Notes
- Enumeration reveals the path to root.
- Every command helps build a picture of the system.
- This workflow is used in real pentests and CTFs.
- Day 2 builds the foundation for exploiting misconfigurations in the next lessons.

---

## Question
Teach me Week 4 Day 3 — Sudo & Misconfigurations.
