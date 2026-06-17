# Week 4 — Day 6  
## Capabilities, NFS & Other Vectors (Privilege Escalation)

## What I learned today
- Learned what Linux capabilities are and how they give programs specific elevated powers.
- Understood how NFS misconfigurations can create privilege‑escalation risks.
- Learned how weak SSH key hygiene can expose systems.
- Learned how password reuse and exposed config files can be dangerous.
- Understood PATH and environment variable misconfigurations.
- Practised safely enumerating these vectors without exploiting anything.

---

## Linux Capabilities
Capabilities split root privileges into smaller pieces.

Examples:
- `cap_net_bind_service` → bind to ports < 1024  
- `cap_sys_time` → change system time  
- `cap_sys_admin` → powerful system‑level actions  

Capabilities allow programs to perform privileged actions **without being fully root**.

### Why this matters
If a program has a dangerous capability and is:
- outdated  
- misconfigured  
- writable  
- or behaves unexpectedly  

…it may be risky.

### Safe enumeration
```
getcap -r / 2>/dev/null
```

Look for unusual capabilities in:
- `/usr/bin/`
- `/usr/local/bin/`

---

## NFS (Network File System) Misconfigurations
NFS allows one machine to share directories with another.

The configuration file:
```
/etc/exports
```

### Dangerous setting
```
no_root_squash
```

This means:
- remote root users are treated as **real root** on the server  
- this is a major misconfiguration  

### Safe enumeration
```
cat /etc/exports
```

Look for:
- `no_root_squash`
- writable shares
- world‑accessible directories

---

## SSH Keys
SSH keys allow passwordless login.

Weaknesses include:
- private keys readable by others  
- keys stored in backups  
- reused keys  
- keys left in scripts  

### Safe enumeration
```
ls -la ~/.ssh/
```

Look for:
- world‑readable private keys  
- unusual key files  
- backup keys like `id_rsa.old`

---

## Password Reuse & Config Files
Admins sometimes store passwords in:
- scripts  
- config files  
- backups  
- environment variables  

### Safe enumeration
```
grep -Ri "password" /etc 2>/dev/null
```

Look for:
- hardcoded passwords  
- database credentials  
- service passwords  

---

## PATH Misconfigurations
The `PATH` variable tells Linux where to find programs.

If root runs a script that uses:
```
tar
cp
ls
```
without full paths like `/bin/ls`, then the wrong program could run.

### Safe enumeration
```
echo $PATH
```

Look for:
- writable directories  
- unusual paths  
- relative paths  

---

## Environment Variables
Programs may rely on environment variables like:
- `LD_PRELOAD`
- `LD_LIBRARY_PATH`
- `PATH`
- `PYTHONPATH`

If root runs a script that trusts these variables, it may be risky.

### Safe enumeration
```
env
```

Look for:
- unusual variables  
- unexpected paths  
- custom library paths  

---

## Practice Tasks (Safe)

### Task 1 — List capabilities
```
getcap -r / 2>/dev/null
```

### Task 2 — Check NFS exports
```
cat /etc/exports
```

### Task 3 — Inspect SSH key permissions
```
ls -la ~/.ssh/
```

### Task 4 — Search for passwords in configs
```
grep -Ri "password" /etc 2>/dev/null
```

### Task 5 — Check PATH
```
echo $PATH
```

### Task 6 — View environment variables
```
env
```

---

## Notes
- Capabilities, NFS, SSH keys, PATH, and environment variables are real‑world escalation vectors.
- Today focused on recognising dangerous patterns, not exploiting them.
- This completes the core privilege‑escalation techniques for Linux.
- Tomorrow is the Week 4 mini‑project.

---

## Question
 — Privilege Escalation Mini‑Project.
