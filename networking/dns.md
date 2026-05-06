# DNS (Domain Name System)

## What I learned today
- DNS translates domain names into IP addresses.
- It exists because humans use names, but computers use numbers.
- DNS uses a hierarchy: root → TLD → authoritative.
- DNS caching makes repeated lookups faster.
- DNS has different record types for different purposes.

## How DNS Works 
1. Device checks local DNS cache.
2. If not found, it asks the DNS resolver (router/ISP/8.8.8.8).
3. Resolver asks the Root server.
4. Root points to the TLD server (.com, .net, etc.).
5. TLD points to the authoritative server.
6. Authoritative server returns the real IP.
7. Resolver sends the IP back to the device.
8. Device caches the result.

## DNS Record Types
- A → Domain to IPv4  
- AAAA → Domain to IPv6  
- **CNAME** → Alias to another domain  
- **MX** → Mail server  
- **NS** → Nameserver for the domain  
- **TXT** → Text data (verification, SPF, DKIM)

---

## Why DNS Matters in Cybersecurity
- Used for recon (finding subdomains).
- Attackers use DNS tunneling to hide traffic.
- Defenders block malicious domains.
- DNS logs help detect suspicious activity.

---

## Notes
- DNS is the first step in almost every internet request.
- Understanding DNS helps with web hacking, recon, and network analysis.

---

## Questions
- What is HTTP vs HTTPS?
