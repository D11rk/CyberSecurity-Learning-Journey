# Week 2 — Day 5  
## Linux Permissions

## What I learned today
- Learned how Linux permissions work (read, write, execute).
- Understood the three permission groups: user, group, others.
- Learned how to view permissions using `ls -l`.
- Practised changing permissions using `chmod` (symbolic and numeric).
- Learned how to change file ownership using `chown`.
- Learned how to change group ownership using `chgrp`.
- Got introduced to special permissions (SUID, SGID, sticky bit).

---

## Permission Basics

### Permission Types
- **r** → read  
- **w** → write  
- **x** → execute  

### User Types
- **u** → user (owner)  
- **g** → group  
- **o** → others  

---

## Viewing Permissions
Use:
```
ls -l
```

Example:
```
-rwxr-xr-- 1 d11rk users 1200 May 22 script.sh
```

Breakdown:
- `rwx` → user permissions  
- `r-x` → group permissions  
- `r--` → others permissions  

---

## Changing Permissions — chmod

### Symbolic
```
chmod u+x script.sh
chmod g-w file.txt
chmod o+r notes.txt
```

### Numeric
| Number | Meaning |
|--------|---------|
| 4 | read |
| 2 | write |
| 1 | execute |

Examples:
```
chmod 755 script.sh
chmod 644 file.txt
```

---

## Changing Ownership — chown
```
sudo chown d11rk file.txt
sudo chown d11rk:users file.txt
```

---

## Changing Group — chgrp
```
sudo chgrp admins file.txt
```

## Notes
- Permissions control security and access.
- Misconfigured permissions can lead to privilege escalation.
- Numeric permissions are faster and used more often.

---

## Question
How do users and groups work in Linux?
