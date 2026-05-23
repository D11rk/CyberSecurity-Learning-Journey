# Week 2 — Day 6  
## Users, Groups & sudo

## What I learned today
- Learned how Linux users work (UID, home directory, shell).
- Understood what groups are and how they control permissions.
- Learned how to create and delete users.
- Learned how to create and delete groups.
- Practised adding users to groups using `usermod`.
- Learned how `sudo` works and why it’s important.
- Explored the key authentication files: `/etc/passwd`, `/etc/shadow`, `/etc/group`.
- Learned how to switch users with `su` and `sudo -u`.

---

## Users in Linux
Linux is a multi-user system.  
Examples of users:
- `root` → superuser  
- normal users (e.g., `d11rk`)  
- service users (`www-data`, `mysql`)  

Each user has:
- UID  
- GID  
- home directory  
- default shell  

Check your groups:
```
groups
```

---

## Groups in Linux
Groups allow multiple users to share permissions.

Check a user’s groups:
```
groups username
```

---

## Managing Users

### Create a user
```
sudo adduser john
```

### Delete a user
```
sudo deluser john
```

### Add user to a group
```
sudo usermod -aG groupname username
```

Example:
```
sudo usermod -aG sudo d11rk
```

---

## Managing Groups

### Create a group
```
sudo groupadd admins
```

### Delete a group
```
sudo groupdel admins
```

---

## sudo — Run commands as root
```
sudo command
```

Check sudo access:
```
sudo -v
```

---

## Important System Files

### /etc/passwd
Stores user account info (NOT passwords).
```
d11rk:x:1000:1000:D11rk:/home/d11rk:/bin/bash
```

### /etc/shadow
Stores password hashes (root only).

### /etc/group
Stores groups and their members.
```
sudo:x:27:d11rk
```

---

## Switching Users

### Switch to another user
```
su username
```

### Switch to root
```
su -
```

### Run a command as another user
```
sudo -u username command
```

---

## Notes
- Users and groups control access and security.
- `sudo` is the safe way to run admin commands.
- `/etc/passwd`, `/etc/shadow`, and `/etc/group` are core authentication files.
- Misconfigured users/groups can lead to privilege escalation.

---

## Question
Practice tasks for everything I learned this week.
