# Week 2 — Day 2  
## Basic Linux Commands

## What I learned today
- Learned the core Linux commands used for navigation, file management, and viewing content.
- Understood how to create, move, copy, and delete files and folders.
- Learned how to view file contents using `cat`, `less`, `head`, and `tail`.
- Practised using `man` and `--help` to understand commands.
- Learned how to use command history.

---

## Navigation Commands
### `pwd`
Shows the current directory.

### `ls`
Lists files and folders.
```
ls
ls -l
ls -a
```

### `cd`
Changes directory.
```
cd /home
cd ..
cd ~
cd Documents
```

---

## File & Folder Commands
### `touch`
Create an empty file.
```
touch notes.txt
```

### `mkdir`
Create a folder.
```
mkdir projects
```

### `rm`
Delete a file.
```
rm file.txt
```

### `rm -r`
Delete a folder.
```
rm -r foldername
```

### `cp`
Copy files.
```
cp file.txt backup.txt
```

### `mv`
Move or rename files.
```
mv file.txt /home/d11rk/
mv oldname.txt newname.txt
```

---

## Viewing Files
### `cat`
Show entire file.
```
cat file.txt
```

### `less`
Scroll through a file.
```
less file.txt
```

### `head`
Show first 10 lines.
```
head file.txt
```

### `tail`
Show last 10 lines.
```
tail file.txt
```

---

## Getting Help
### `man`
Manual pages.
```
man ls
man cp
```

### `--help`
Quick help.
```
ls --help
```

---

## Command History
### `history`
Shows previous commands.

### Arrow keys
Use ↑ to repeat commands.

---

## Notes
- These commands are the foundation of Linux usage.
- `man` is the most important command for learning.
- Navigation + file management = core terminal skills.

---

## Question
How do I create and edit files in Linux?
