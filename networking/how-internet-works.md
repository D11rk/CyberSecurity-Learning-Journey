# How the Internet Works (Simple Explanation)

## What I learned today
- The internet works through a series of steps: DNS → TCP handshake → HTTPS handshake → request/response.
- Every website visit starts with DNS.
- Data travels in packets across routers and networks.
- HTTPS encrypts the communication for security.

## What Happens When I Type google.com
1. *DNS Lookup
   Browser finds the IP address for google.com.

2. TCP Handshake
   Device and server establish a reliable connection (SYN → SYN/ACK → ACK).

3. HTTPS Handshake
   They exchange certificates and create an encrypted tunnel.

4. HTTP Request
   Browser sends: “Give me the homepage.”

5. Server Response
   Server sends HTML, CSS, JS, images, etc.

6. Rendering
   Browser displays the webpage.

## Notes
- DNS finds the server.
- TCP connects to the server.
- HTTPS secures the connection.
- HTTP transfers the data.
- Routers move packets across the internet.

## Questions
- What is HTTP vs HTTPS?
