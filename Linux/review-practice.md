# Week 2 — Day 7  
## Review + Practice

## What I learned today
- Reviewed all Linux fundamentals from Week 2.
- Practised navigation, file management, editing, searching, permissions, and user management.
- Strengthened understanding of `grep`, `find`, `chmod`, `chown`, `nano`, and `sudo`.
- Completed hands-on tasks to reinforce learning.
- Built confidence using the terminal for real-world tasks.

---

## Week 2 Summary

### Navigation
- `ls`, `cd`, `pwd`

### File Management
- `touch`, `mkdir`, `rm`, `cp`, `mv`

### Viewing Files
- `cat`, `less`, `head`, `tail`

### Editing
- `nano`
- basic `vim`

### Searching
- `grep`
- `find`

### Permissions
- `chmod`
- `chown`
- `chgrp`

### Users & Groups
- `adduser`, `deluser`
- `groupadd`, `groupdel`
- `usermod -aG`
- `sudo`
- `/etc/passwd`, `/etc/shadow`, `/etc/group`

---

## Practice Tasks

### Task 1 — Navigation
- Create a `practice` folder with subfolders:
  - `notes`
  - `projects`
  - `logs`

### Task 2 — File Creation & Editing
- Create `day7.txt`
- Add text using `echo` and `nano`
- View it with `cat`, `head`, `tail`

### Task 3 — Searching
- Create multiple `.txt` files
- Add the word **password** to one
- Use `grep` to find it
- Use `find` to locate all `.txt` files

### Task 4 — Permissions
- Create `run.sh`
- Add:
  ```
  echo "Hello D11rk"
  ```
- Make executable with `chmod 755`
- Run it

### Task 5 — Users & Groups
(Do on a VM)
- Create `testuser`
- Create `testgroup`
- Add user to group
- Check `/etc/passwd` and `/etc/group`
- Switch users with `su`

---

## Notes
- This week built the foundation for all future Linux and cybersecurity work.
- Practising commands is the key to becoming fast and confident.
- Next week moves into networking, which builds directly on these skills.

---

## Question
Teach me Week 3 Day 1 — Advanced Networking.
