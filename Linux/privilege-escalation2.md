# Week 4 — Day 7  
## Privilege Escalation Mini‑Project

## What I learned today
- Practised the full Linux privilege‑escalation workflow from start to finish.
- Learned how to combine all enumeration techniques into one structured process.
- Understood how to identify potential escalation paths safely.
- Learned how to document findings like a real pentester.
- Completed a full system analysis without exploiting anything.

---

## Scenario
You have a low‑privileged shell on a Linux machine:

```
user@machine$
```

Your goal:
- enumerate the system  
- identify misconfigurations  
- document potential escalation paths  
- **do not exploit anything**  

This mirrors real‑world pentesting methodology.

---

## Full Enumeration Workflow

### 1. User Information
```
id
whoami
```
Check:
- UID  
- groups  
- privilege level  

---

### 2. System Information
```
uname -a
cat /etc/os-release
```
Check:
- kernel version  
- OS version  
- architecture  

---

### 3. Process Enumeration
```
ps aux
```
Look for:
- root processes  
- custom scripts  
- unusual services  

---

### 4. Services & Ports
```
ss -nltu
```
Check:
- listening services  
- internal ports  
- network exposure  

---

### 5. Sudo Permissions
```
sudo -l
```
Look for:
- NOPASSWD entries  
- custom scripts  
- unusual binaries  

---

### 6. SUID/SGID Binaries
```
find / -perm -4000 -type f 2>/dev/null
```
Look for:
- unusual binaries  
- writable files  
- custom scripts  

---

### 7. Cron Jobs
```
cat /etc/crontab
```
Look for:
- scripts run as root  
- writable directories  
- wildcards  

---

### 8. Capabilities
```
getcap -r / 2>/dev/null
```
Look for:
- unusual capabilities  
- custom binaries with elevated powers  

---

### 9. NFS Exports
```
cat /etc/exports
```
Look for:
- `no_root_squash`  
- writable shares  

---

### 10. SSH Keys
```
ls -la ~/.ssh/
```
Look for:
- weak permissions  
- backup keys  
- shared keys  

---

## What to Document
For each category, write down:

- what you found  
- why it might be risky  
- what misconfiguration pattern it matches  
- whether it could be an escalation path  

This builds your professional privesc analysis skills.

---

## Example Documentation Structure

### 🔹 System Info
- Kernel: 5.x  
- OS: Ubuntu 20.04  
- Notes: Kernel not outdated  

### 🔹 Sudo
- No NOPASSWD entries  
- No unusual commands  

### 🔹 SUID
- Standard binaries only  
- No custom scripts  

### 🔹 Cron
- One root cron job  
- Script not writable  

### 🔹 Capabilities
- No unusual capabilities  

### 🔹 SSH Keys
- Permissions correct  

### 🔹 Potential Paths
- None confirmed  
- Documented observations  

---

## Notes
- Today was about combining everything learned this week.
- The goal was to think like a pentester, not exploit anything.
- This completes the Linux privilege‑escalation foundation.
- Next week begins a new topic.

---

## Question
Start Week 5 — what am I learning next?
