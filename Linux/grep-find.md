# Week 2 — Day 4  
## grep + find

## What I learned today
- Learned how to search *inside* files using `grep`.
- Learned how to search *for* files using `find`.
- Practised recursive searches and filtering.
- Learned useful flags like `-i`, `-r`, `-n`, and `-v`.
- Learned how to combine `find` and `grep` for powerful searches.
- Understood real-world uses like searching logs, configs, and large files.

---

## grep — Search inside files

### Basic search
```
grep "hello" file.txt
```

### Case-insensitive
```
grep -i "hello" file.txt
```

### Search in all files in a folder
```
grep "password" *
```

### Recursive search
```
grep -r "error" /var/log
```

### Show line numbers
```
grep -n "root" /etc/passwd
```

### Exclude matches
```
grep -v "error" logfile.txt
```

### Combine with pipes
```
cat file.txt | grep "admin"
```

---

## find — Search for files

### Find by name
```
find / -name file.txt
```

### Find by extension
```
find /home -name "*.png"
```

### Only files
```
find / -type f -name "*.conf"
```

### Only directories
```
find / -type d -name "config"
```

### Find by size
```
find / -size +10M
```

### Find and delete (dangerous)
```
find /tmp -name "*.log" -delete
```

---

## Combining find + grep

### Search for files, then search inside them
```
find /etc -name "*.conf" | xargs grep "root"
```

### Search for Python files containing “import”
```
find . -name "*.py" | xargs grep "import"
```

---

## Real-world uses
- Search logs for errors  
- Search config files for passwords  
- Find large files  
- Find suspicious scripts  

---

## Question
How do Linux file permissions work?
