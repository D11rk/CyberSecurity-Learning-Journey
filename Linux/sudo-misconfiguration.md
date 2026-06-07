# Week 4 — Day 3  
## Sudo & Misconfigurations (Privilege Escalation)

## What I learned today
- Understood what sudo is and how it controls privileged commands.
- Learned how misconfigurations in sudo rules can create security risks.
- Learned the most common dangerous sudo patterns.
- Practised checking my own sudo permissions safely.
- Built the mindset needed to recognise risky sudo configurations.

---

## What is Sudo?
Sudo allows a normal user to run specific commands with elevated privileges.

Admins define these permissions in the **sudoers** file:
```
/etc/sudoers
```

If the admin makes a mistake in this file, it can create a privilege‑escalation opportunity.

---

## Why Sudo Misconfigurations Matter
If a user can run a program with elevated privileges, and that program can:
- edit files  
- open other tools  
- run system commands  
- load plugins or configs  
- call external binaries  

…then it may be possible to misuse it.

Today’s goal is to **recognise** these patterns, not exploit them.

---

## Common Sudo Misconfiguration Patterns

### 1. Commands allowed without a password
Pattern:
```
NOPASSWD:
```
If a program runs without requiring a password, it may be risky.

---

### 2. Editors allowed under sudo
Programs like:
- nano  
- vim  
- less  
- more  

These can open or modify system files.

---

### 3. Programs that execute system commands
Some tools internally run:
- shells  
- scripts  
- external binaries  

If allowed under sudo, they inherit elevated privileges.

---

### 4. Custom scripts allowed under sudo
Example:
```
/usr/local/bin/backup.sh
```
If the script uses insecure paths or writable files, it may be risky.

---

### 5. Programs that load configs or plugins
If the config files are writable, they can be abused.

---

## Checking Sudo Permissions (Safe)
You can safely inspect your sudo permissions with:
```
sudo -l
```

This shows:
- which commands you can run  
- whether a password is required  
- which user the command runs as  

You are not exploiting anything — only observing.

---

## What to Look For
When reviewing sudo permissions, note if:
- any commands run without a password  
- any commands are editors  
- any commands are scripting languages  
- any commands are custom scripts  
- any commands load configs or plugins  

These patterns help identify potential misconfigurations.

---

## Practice Tasks (Safe)

### Task 1 — Check your sudo permissions
```
sudo -l
```

### Task 2 — Identify unusual commands
Look for:
- editors  
- file managers  
- custom scripts  
- anything in `/usr/local/bin`  

### Task 3 — Document findings
Write down:
- allowed commands  
- whether they require a password  
- whether any look risky  

---

## Notes
- Sudo misconfigurations are one of the most common privilege‑escalation vectors.
- Today’s goal is to recognise patterns, not exploit them.
- Understanding sudo rules is essential for the rest of Week 4.

---

## Question
Teach me Week 4 Day 4 — SUID & SGID Binaries.
