# Week 4 — Day 1  
## Linux Privilege Escalation Basics

## What I learned today
- Understood what privilege escalation is and why attackers use it.
- Learned the difference between vertical and horizontal privilege escalation.
- Learned the privilege escalation mindset: enumerate first, exploit later.
- Practised the core enumeration commands used in every Linux privesc.
- Learned the main privilege escalation vectors I will study this week.

---

## What is Privilege Escalation?
Privilege escalation is the process of going from a **normal user** to **root** on a Linux system.

Two types:
- **Vertical escalation** → user → root  
- **Horizontal escalation** → user A → user B  

Vertical escalation is the main focus in hacking and pentesting.

---

## Why Privilege Escalation Matters
A normal user has limited access.  
Root can:
- read any file  
- modify system configs  
- install tools  
- access passwords  
- control the entire machine  

Getting initial access is easy.  
Becoming root is the real goal.

---

## Privilege Escalation Mindset
Before trying to escalate, you must **enumerate**.

Privilege escalation is:
- 80% information gathering  
- 20% exploiting  

You look for:
- misconfigurations  
- weak permissions  
- vulnerable binaries  
- scripts running as root  
- writable files  
- sudo permissions  

---

## Core Enumeration Commands

### Who am I?
```
id
whoami
```

### System information
```
uname -a
cat /etc/os-release
```

### Running processes
```
ps aux
```

### Listening services
```
ss -nltu
```

### Sudo permissions
```
sudo -l
```

### Writable files
```
find / -writable 2>/dev/null
```

### SUID binaries
```
find / -perm -4000 2>/dev/null
```

### Cron jobs
```
cat /etc/crontab
```

These commands form the foundation of Linux privilege escalation.

---

## Common Privilege Escalation Vectors
- Misconfigured **sudo** permissions  
- Vulnerable **SUID** binaries  
- Writable **cron job scripts**  
- Weak file permissions  
- Password reuse  
- SSH keys  
- Kernel exploits  
- Capabilities  
- NFS misconfigurations  

Each of these will be covered in detail throughout Week 4.

---

## Practice Tasks
Run these on your VM:

1. Identify your user:
   ```
   id
   ```

2. Check system info:
   ```
   uname -a
   ```

3. List running processes:
   ```
   ps aux
   ```

4. Check open ports:
   ```
   ss -nltu
   ```

5. Check sudo permissions:
   ```
   sudo -l
   ```

6. Find SUID binaries:
   ```
   find / -perm -4000 2>/dev/null
   ```

7. View cron jobs:
   ```
   cat /etc/crontab
   ```

---

## Question
Teach me Week 4 Day 2 — System Enumeration.
