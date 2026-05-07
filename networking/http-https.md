# HTTP vs HTTPS

## What I learned today
- HTTP is the basic protocol used for communication between browser and server.
- HTTPS is HTTP with encryption using SSL/TLS.
- HTTP is not secure; HTTPS protects data from attackers.
- HTTPS uses certificates to prove the server is real.
- HTTP uses port 80, HTTPS uses port 443.

## HTTP (HyperText Transfer Protocol)
- Used for sending requests and receiving responses.
- Not encrypted.
- Anyone on the network can read the data.
- Vulnerable to MITM attacks.
- Uses port 80.

## HTTPS (HTTP Secure)
- HTTP + SSL/TLS encryption.
- Data is protected from attackers.
- Uses certificates to verify identity.
- Safe for passwords, cookies, and personal data.
- Uses port 443.

## How HTTPS Works (Simple)
1. Browser says: “I want to connect securely.”
2. Server sends its certificate.
3. Browser checks if certificate is valid. 
4. Browser and server create an encrypted key.
5. All communication becomes encrypted.

## Notes
- HTTPS protects against sniffing and MITM attacks.
- Almost all modern websites use HTTPS.
- Understanding HTTP/HTTPS is essential for web hacking.

## Questions
- How do cookies and sessions work?  
