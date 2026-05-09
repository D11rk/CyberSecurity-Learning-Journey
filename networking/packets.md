# What Is a Packet?

## What I learned today
- A packet is a small piece of data sent across a network.
- Data is broken into packets so it can travel faster and more reliably.
- Each packet has a header (info) and a payload (data).
- Packets may take different paths and are reassembled at the end.

## Packet Structure
### Header (the label)
Contains:
- Source IP
- Destination IP
- Source port
- Destination port
- Protocol (TCP/UDP)
- Packet number

### Payload (the content)
- The actual data being sent
- Could be part of a webpage, message, login request, etc.

## Why Packets Exist
- Faster than sending one big chunk of data
- More reliable (only broken packets need resending)
- Easier to route across the internet
- Allows multiple users to share the network

## How Packets Travel
- Packets can take different routes to the destination.
- Routers forward packets based on the header.
- The receiving device reassembles them in order.

## Example Packet (Simple)
Source IP: 192.168.1.10  
Destination IP: 142.250.187.206  
Protocol: TCP  
Source Port: 51512  
Destination Port: 443  
Payload: Encrypted HTTPS data  


## Questions
- How do I capture and analyse packets in Wireshark?
