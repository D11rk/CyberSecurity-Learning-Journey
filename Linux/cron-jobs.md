# Week 4 — Day 5  
## Cron Jobs & Scheduled Tasks (Privilege Escalation)

## What I learned today
- Understood what cron jobs are and how Linux schedules automated tasks.
- Learned why cron jobs running as root can be risky if misconfigured.
- Identified common cron job misconfiguration patterns.
- Practised safely enumerating cron jobs and scheduled tasks.
- Learned how to recognise dangerous cron setups without exploiting them.

---

## What Are Cron Jobs?
Cron is the Linux task scheduler.

It automatically runs commands at:
- specific times  
- specific intervals  
- daily/weekly/monthly schedules  

Cron is used for:
- backups  
- updates  
- maintenance scripts  
- monitoring tasks  

---

## Why Cron Jobs Matter for Privilege Escalation
If a cron job runs as **root**, and it uses:
- a script you can edit  
- a file you can modify  
- a directory you can write to  
- unsafe wildcards  
- unsafe paths  

…it becomes a potential privilege‑escalation risk.

Today’s goal is to **recognise** these patterns safely.

---

## Where Cron Jobs Are Located

### System-wide cron file
```
/etc/crontab
```

### Cron directories
```
/etc/cron.hourly/
/etc/cron.daily/
/etc/cron.weekly/
/etc/cron.monthly/
```

### User-specific cron jobs
```
crontab -l
```

These locations show what tasks run automatically.

---

## How to Read a Cron Job
Cron format:
```
minute hour day month weekday user command
```

Example:
```
* * * * * root /usr/local/bin/backup.sh
```

Meaning:
- runs every minute  
- runs as root  
- runs `/usr/local/bin/backup.sh`  

If that script is writable → risky.

---

## Common Cron Misconfiguration Patterns

### 1. Writable scripts
If a cron job runs a script in a writable directory, it’s dangerous.

### 2. Writable directories
Example:
```
/tmp/backup.sh
```
`/tmp` is world-writable.

### 3. Wildcards in commands
Example:
```
tar -czf /root/backup.tar.gz /home/*
```
Wildcards can behave unpredictably.

### 4. Relative paths
Example:
```
backup.sh
```
If PATH is unsafe, the wrong program may run.

### 5. Custom scripts
Custom scripts often contain mistakes or unsafe commands.

---

## Safe Enumeration Commands

### View system cron jobs
```
cat /etc/crontab
```

### List cron directories
```
ls -la /etc/cron.hourly/
ls -la /etc/cron.daily/
ls -la /etc/cron.weekly/
ls -la /etc/cron.monthly/
```

### View user cron jobs
```
crontab -l
```

These commands only **read** information.

---

## What to Look For
Ask yourself:
- Does the cron job run as root?
- Does it run a script?
- Is the script writable?
- Is the directory writable?
- Does it use wildcards?
- Does it use relative paths?
- Is it a custom script?

These patterns help identify risky cron setups.

---

## Practice Tasks (Safe)

### Task 1 — Inspect system cron jobs
```
cat /etc/crontab
```

### Task 2 — Check cron directories
```
ls -la /etc/cron.daily/
```

### Task 3 — View your user’s cron jobs
```
crontab -l
```

### Task 4 — Identify suspicious patterns
Look for:
- writable scripts  
- writable directories  
- wildcards  
- custom scripts  

---

## Notes
- Cron jobs are powerful and often run as root.
- Misconfigurations can create privilege‑escalation risks.
- Today focused on recognising dangerous patterns, not exploiting them.
- This prepares me for capabilities and other escalation vectors in Day 6.

---

## Question
Teach me Week 4 Day 6 — Capabilities, NFS & Other Vectors.
