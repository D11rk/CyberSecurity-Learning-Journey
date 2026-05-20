# Week 2 — Day 3  
## Files & Editing

## What I learned today
- Learned how to create files using `touch` and `echo`.
- Understood the difference between `>` (overwrite) and `>>` (append).
- Learned how to edit files using `nano` and the basics of `vim`.
- Practised viewing files using `cat`, `less`, `head`, and `tail`.
- Learned how to use pipes (`|`) to combine commands.
- Learned how to redirect output and errors.

---

## Creating Files

### `touch`
Create an empty file.
```
touch notes.txt
```

### `echo`
Create a file with content.
```
echo "hello world" > file.txt
```

### Overwrite vs Append
```
echo "line 1" > file.txt
echo "line 2" >> file.txt
```

---

## Editing Files

### Using nano (beginner friendly)
```
nano file.txt
```
Inside nano:
- CTRL + O → save  
- CTRL + X → exit  
- CTRL + K → cut line  
- CTRL + U → paste line  

### Using vim (advanced)
```
vim file.txt
```
Basic workflow:
1. Press `i` to enter insert mode  
2. Type your text  
3. Press `ESC`  
4. Type `:wq` to save and quit  

---

## Viewing Files

### `cat`
Show entire file.
```
cat file.txt
```

### `less`
Scroll through file.
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

### `tail -f`
Live updates (useful for logs).
```
tail -f /var/log/syslog
```

---

## Redirecting Output

### Send output to a file
```
ls > files.txt
```

### Append output
```
ls >> files.txt
```

### Redirect errors
```
command 2> errors.txt
```

### Redirect output + errors
```
command > output.txt 2>&1
```

---

## Pipes (`|`)
Send output of one command into another.

Examples:
```
ls | grep .txt
cat /var/log/syslog | grep error
cat file.txt | wc -l
```
---

## Question
How do I search for files and text in Linux?
