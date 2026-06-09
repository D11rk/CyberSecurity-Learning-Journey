# Week 4 — Day 4  
## SUID & SGID Binaries (Privilege Escalation)

## What I learned today
- Learned what SUID and SGID permissions are and why they exist.
- Understood how SUID/SGID binaries run with elevated privileges.
- Learned why misconfigured SUID binaries are a major privilege‑escalation risk.
- Practised safely enumerating SUID and SGID binaries on a Linux system.
- Learned how to identify unusual or suspicious SUID binaries.

---

## What is SUID?
SUID (Set User ID) is a special permission on executable files.

If a file has the SUID bit set:
- it runs with the **file owner’s permissions**, not the user’s.

Example:
- `/usr/bin/passwd` is SUID‑root so normal users can change their passwords.

---

## What is SGID?
SGID (Set Group ID) is similar but applies to groups.

If a file has the SGID bit set:
- it runs with the **file’s group permissions**, not the user’s.

SGID is also used on shared directories so new files inherit the directory’s group.

---

## Why SUID/SGID Matter for Privilege Escalation
SUID‑root binaries run with **root privileges**.

If a SUID binary:
- loads config files  
- calls external programs  
- uses environment variables  
- has a bug  
- or is not meant to be SUID  

…it may be exploitable.

This is why SUID binaries are heavily audited in security assessments.

---

## Safe Enumeration Commands

### Find all SUID binaries
```
find / -perm -4000 -type f 2>/dev/null
```

### Find all SGID binaries
```
find / -perm -2000 -type f 2>/dev/null
```

### Find both SUID and SGID
```
find / -perm /6000 -type f 2>/dev/null
```

These commands only **list** files — they do not modify anything.

---

## Common Legitimate SUID Binaries
These are normally present:
- `/usr/bin/passwd`
- `/usr/bin/sudo`
- `/usr/bin/su`
- `/usr/bin/chsh`
- `/usr/bin/chfn`
- `/usr/bin/newgrp`

These require elevated permissions to function correctly.

---

## Suspicious SUID Binaries
Take note if you see:
- editors (vim, nano)
- scripting languages (python, perl)
- file managers
- network tools
- anything in `/usr/local/bin`
- custom scripts
- world‑writable SUID files

These may indicate misconfigurations.

---

## How Attackers Think About SUID Binaries
Attackers ask:
- “What else can this program do?”
- “Does it load configs?”
- “Does it call other programs?”
- “Does it rely on environment variables?”
- “Is it outdated or custom?”

Understanding this mindset helps identify risky binaries.

---

## Practice Tasks (Safe)

### Task 1 — List SUID binaries
```
find / -perm -4000 -type f 2>/dev/null
```

### Task 2 — List SGID binaries
```
find / -perm -2000 -type f 2>/dev/null
```

### Task 3 — Identify unusual entries
Look for:
- programs you don’t recognise  
- binaries in strange locations  
- custom scripts  

### Task 4 — Compare with known safe binaries
Use the list above.

---

## Notes
- SUID/SGID binaries are essential but dangerous if misconfigured.
- Enumeration helps identify unusual or risky binaries.
- Today focused on understanding and recognising patterns, not exploiting them.
- This prepares me for cron jobs and scheduled tasks in Day 5.

---

## Question
Teach me Week 4 Day 5 — Cron Jobs & Scheduled Tasks.
