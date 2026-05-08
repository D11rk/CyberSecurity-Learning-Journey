# TLS (Transport Layer Security)

## What I learned today
- TLS is the encryption protocol used by HTTPS.
- It protects data from attackers during transmission.
- TLS uses certificates to prove the server is real.
- TLS creates a secure tunnel between browser and server.

## What TLS Does
- Encrypts data so nobody can read it.
- Prevents tampering.
- Verifies the identity of the server.
- Protects cookies, passwords, and personal data.

## How TLS Works (Simple)
1. Browser says: “I want to connect securely.”
2. Server sends its certificate.
3. Browser checks if certificate is trusted.
4. Browser and server create a shared secret key.
5. All communication becomes encrypted.

This is called the **TLS handshake**.

## Certificates
A certificate contains:
- Domain name  
- Public key  
- Issuer (CA)  
- Expiry date  

Browsers trust certificates signed by trusted Certificate Authorities (CAs).

## Why TLS Matters in Cybersecurity
- Stops MITM attacks.
- Protects login forms.
- Protects session cookies.
- Prevents sniffing on public WiFi.
- Required for modern websites.

## Notes
- HTTPS = HTTP + TLS  
- TLS keeps your data safe  
- Certificates prove identity  



## Questions
- What is a packet?
